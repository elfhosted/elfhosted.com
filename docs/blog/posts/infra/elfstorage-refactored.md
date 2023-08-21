---
date: 2023-08-21
categories:
  - CHANGELOG
tags:
  - elfstorage
title: ElfStorage refactored, repriced, 100Gb now free, Seafile fixed
description: We've extended the free ElfStorage to 100Gb, and repackaged upgrades into 1TB chunks, $0.20/day. Oh, and Seafile actually works now!
---

# ElfStorage refactored, 100GB free, 40% cheaper

ElfStorage is our internal storage platform, providing basic network-attached storage for new users, and users who choose not to BYOS.

Following some recent feedback, we've made the following changes:

1. Initially sized at a puny 10Gb, all users now get 100Gb :elephant: storage in `/storage/elfstorage` for **FREE** with their account.

2. ElfStorage is now a daily :calendar: subscription (*previously monthly*), so that it can be added to existing subscriptions and funded with ElfBuckz, rather than being a totally separate, monthly subscription. This also makes it easier to try out with your initial $10 ElfBuckz.

3. ElfStorage's monthly price is now 40% :fire: cheaper, at **$6/TB**, instead of $10/TB (*\$0.20/day*)

!!! info
    ElfStorage is built with Ceph, on a collection of 1Gbps single-purpose nodes, and large HDDs (*spinning rust*). We store 2 replicas of each object, across two separate physical hosts, for basic redundancy.

Read more for ElfStorage questions, Seafile fixes, and app bundles..

<!-- more -->

## Questions re ElfStorage

### Why does it exist?

Question:
> Why do we have our own storage, if we encourage users to BYO with [StorageBoxes][storagebox]?"
  
Answer:
> Some apps don't allow you to choose where they store their data (*[OpenBooks][openbooks], or [SeaFile][seafile] for example*), so we need to have some consistently-addressed storage to make these apps usable. Having easily accessible, expandable storage also makes the onboarding process much simpler for newer users, who can later build out their stacks using BYOS in time.

### Existing subscribers

Question:
> What if I've already subscribed to extra ElfStorage at the old rate of $0.01/GB/month?

Answer:
> ElfStorage1TB is a new package, and your subscription won't automatically transfer. Remove your old ElfStorage product from [your subscription](https://store.elfhosted.com/my-account/subscriptions/) to avoid being charged next month, and [hit me up](https://discord.com/channels/396055506072109067/1119478614287712337) for an ElfBuckz refund if I owe you anything.
> Going forward, add the new daily, [per-TB ElfStorage](https://store.elfhosted.com/product/elfstorage/) to your subscription if you need more than 100Gb.

### Can it seed?

Question:
> Can I torrent / seed from ElfStorage?

Answer:
> Currently this works, but TBH this may be due to initial low usage, rather than great performance. The ceph cluster is intended for long-term storage, and eventually we'll hit a saturation point for I/O. 
> 
> For best performance, use the NZB tools (*[NZBGet][nzbget] or [SABnzbd][sabnzbd]*) or [RDTClient][rdtclient], rather than torrent clients, since they have access to a 200Gi NVMe-backed `/tmp` directory for downloading and unpacking (*and then completed files can be moved to storage mounts*)

### Should I still BYO?

Question:
> At $6/TB, ElfStorage is nearly priced the same as a Hetzner [Storagebox](storagebox). Should I just skip the storagebox and subscribe to ElfStorage?

Answer:
> No, a storagebox is still an excellent option in terms of both price, data ownership, and flexibility.
>
> ElfStorage is a good alternative to a storagebox if (a) you can't buy a Storagebox for some reason, or (b) you don't consider your data to be "precious" enough to keep separate from ElfHosted, or \(c) you don't need to transfer in/out of ElfStorage much.
>
> Additionally, more users using storageboxes decreases the overall load on the ElfHosted infrastructure, which allows us to scale better.

## SeaFile Fixed

Today also saw the final fixes for [Seafile][seafile] 10 applied, so users who were having issues with Seafile should now be sorted. A few things to note:

1. Files synced with Seafile **cannot** be read by other apps, due to the way Seafile represents all files as "blobs". This "blobbage" does make for extremely fast and efficient file syncing, but it's not a suitable solution for sycing media from ElfHosted to elsewhere.
2. Seafile's default admin username will be the email address you signed up with, and your password will be the highly-secret `changeme`. Be sure to change it!
3. If you use client-side encrypted libraries, nobody but you can read your files. This makes Seafile the only option I'm comfortable using myself, or offering users for photo backups (*the mobile app can do background uploads to encrypted libraries*).

## Upcoming bundles

Another reason to refactor ElfStorage was to support the option of product bundles, another recent suggestion. The idea would be to reduce friction for new users by offering a simple bundle, for example [Radarr][radarr]+[Sonarr][sonarr]+[Prowlarr][prowlarr]+[SABnbd][sabnzbd]+[Plex][plex]+[ElfStorage1TB][elfstorage] for ~$15/month. This would afford new users the option to get started with a single purchase, and then spend their $10 ElfBuckz on ancillary apps.

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total users | 62
:fontawesome-solid-hard-drive: Storageboxes mounted | 14
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 2

### Bugz squished

* :bug: ruTorrent with gluetun-based VPN providers was failing due to a port conflict. (*Both rutorrent and gluetun want to use port `8000`*). Gluetun has now been set to use a different port.
* :bug: Seafile gets **really** grumpy without a memcached service for caching. Although it's strictly not required, I've added memcached so that we're best positioned for easy future upgrades.

### Summary

As always, thanks for building with us - feel free to share suggestions, ideas, and whatever you ate for breakfast today! :cooking:

--8<-- "common-links.md"