---
date: 2024-02-04
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Stremio Scaling Stress (and how we adapted)
description: Bringing in a bunch of stremio / torrentio users unearthed some more scaling / fragility issues, here's how we fared!
---
# Stremio Scaling Stresses

In our [previous episode](/blog/2024/02/01/supporting-stremio/), your brave (*perhaps foolhardy?*) elves had scaled the [infrastructure](/blog/2024/01/28/scaling-the-gigabytes/) and the [humans](/blog/2024/01/29/scaling-the-humans/), preparing to announce our tiered torrentio-like service (*free-public, [paid-subscription](https://store.elfhosted.com/product/torrentio), and free-internal*), https://torrentio.elfhosted.com, to the rampaging streaming hordes at [r/StremioAddons](https://www.reddit.com/r/StremioAddons).

The next morning iPromKnight [PR'd a huge](https://github.com/Gabisonfire/torrentio-scraper-sh/pull/26) (*and hugely more efficient*) replacement of the original scrapers, so I scrambled to YOLO-implement these scrapers into our instance before launching.

The [announcement post](https://www.reddit.com/r/StremioAddons/comments/1agomu9/free_public_instance_torrentioelhostedcom_with/) went flawlessly, except in my rush I misspelled "ElfHosted" in the title! :man_facepalming:

In the 3 1/2 days since the announcement, we've added 39 more (*free ElfBuckz*) subscribers, and 35 of those are torrentio subscribers.

The extra attention have added stress in a few areas, which I'll detail below..

<!-- more -->

## Storage I/O

Debrid users have **huge** Plex libraries, so we've seen the effect of many new users signing up for Plex, connecting to Zurg, and letting Plex go to town with metadata scraping / library building, putting I/O load on our SSD-backed user-config-storage nodes.

I tried to relieve some of this pressure by increasing our Ceph MDS count - big mistake, because the resulting throughput on the storage nodes exceeded their 1Gbps capacity, and I/O stalled / halted for an hour or two while I untangled the mess!

Shortly thereafter, I put in the order to replace our 3 x 1Gpbs nodes with 3 x 10Gbps nodes, such that we won't get caught out in a similar cascading storage situation! (*Under normal load, the 1Gbps nodes seem to only work at 20% capacity, or 200Mbps, but the fact that there's a hard ceiling at 1Gbps makes me nervous!*)

## Flux overhead

Our GitOps processes are based on [Funky Penguin's Geek Cookbook Flux Deployment design](https://geek-cookbook.funkypenguin.co.nz/kubernetes/deployment/flux/design/) - every tenant gets a [Kustomization](https://fluxcd.io/flux/components/kustomize/kustomizations/), which points to a [HelmRelease](https://fluxcd.io/flux/components/helm/helmreleases/), which contains their specific app selection and parameters.

During our daily maintenance window, any waiting container updates or app changes are rolled out, and this process had started to take longer than the 1h maintenance window. What was worse, is that if a new user created an account 1 minute into the maintenance window, they could end up waiting for an hour for their new apps to reconcile, while flux worked its way through the backlog of updates.

Today I enabled Flux's "[horizontal sharding](https://fluxcd.io/flux/installation/configuration/sharding/)", whereby we split the responsibility for the user deployments across multiple instance of the flux controllers. I created 26 shards (A-Z), and assigned responsibility for each user's resource to the shard matching the first letter of their username. So theoretically, we should reconcile changes 26x faster now. 

Here's how tonight's rollout looked, in terms of CPU resources (*I only turned on sharding just before starting*):

![](/images/flux-sharding-effects-on-daily-rollout.png)

Note that the entire rollout took 15 minutes!

## Bugs fixed

We've also uncovered a few decent-sized bugs over the last few days:

### Plex DirectPlay

Plex's remote DirectPlay capabilities were broken due to.. wait for it.. [a misplaced comma/bracket combination](https://github.com/geek-cookbook/containers/commit/4feadf03f1ed1225b433f6b86c92a581d993e55f). The result was that users were throttled (by Plex) when attempting to remote-play their media. This was fixed in tonight's rollout, so DirectPlay remotely should work properly again. (*The message about being unreachable externally is normal, it's because Plex is behind a reverse proxy and VPN*)

### 72H Bug

The dreaded 72h bug (*if you renewed your subscription a few times to switch apps, the store would "expired" you because you had so much credit that it hadn't processed your orders for several days*) is now resolved. I refactored the way subscriptions are expired, making it Wordpress's responsibility to decide when a subscription has expired, rather than simply relying on timestamps.

The result should be no more surprise empty dashboards, but also more predictable expiry of unused apps, after your 24h renewal cycle has applied.

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"

[^1]: Includes 2 x 26 new sharded flux pods!