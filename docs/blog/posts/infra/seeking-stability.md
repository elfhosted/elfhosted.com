---
date: 2024-03-15
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Setting Sail for Stability
description: 5 days after the ceph i/o issues / downtime, we're in good shape WRT stability and speed
---
# Setting Sail for Stability

It's been 5 days since we had to turn all tenant workloads down for 10h while we performed "open-heart" surgery on our storage nodes. The root cause of our storage issues, it turned out, was some poor defaults applied to new ceph metadata pools when the SSD-based `/config` volumes were first added. At that time, our size / load wasn't significant enough to bring the issue to light.

Since the fix was applied (extending the `pg_num` on the blockpool from `1` to `32`), we've not seen another I/O issue, nor pods stuck waiting on restarting.

So.. now that the fire is out, and we're enjoying a period of nice, calm, stability, here's what's coming...

<!-- more -->
## Focus on observability

I'm spending the next few days working on tidying up our internal observability - we're generating so many metrics (*most of them unnecessary*) that we're missing signal in the noise. It's early days yet, but our friend @brett (*the developer of [Annatar](https://annatar.elfhosted.com)*) has pointed me to [Mimir](https://grafana.com/oss/mimir/) as a replacement for Prometheus, on the basis that we might be able to expose beautiful per-tenant Grafana dashboards!

## Bugs / Suggestions are now in GitHub

We were originally tracking bugs and suggestions in Discord forum channels, but it became too hard to manage / triage these over time, and the channels ended up as a sort of "dumping ground" for ideas/bugs.

With the assistance of some industrious elves, we've moved the bugs and suggestions to a [GitHub project board](https://github.com/orgs/geek-cookbook/projects/1). The idea is that the board will help promote visibility of current / upcoming changes, and allow the more popular requests (*or more severe bugs*!) to "bubble to the surface".

Here are links you can use to create new bugs / suggestions:

* Create [new bug](https://github.com/geek-cookbook/elf-charts/issues/new?assignees=funkypenguin&labels=bug&projects=&template=bug-report.yaml&title=%5Bbug+report%5D+)
* Create [new suggestion
](https://github.com/geek-cookbook/elf-charts/issues/new?assignees=funkypenguin&labels=suggestion&projects=&template=suggestion.yaml&title=%5Bsuggestion%5D+)
!!! tip 
    You can also get these links in Discord by typing `!bug` or `!suggestion`

## Alpha channel is now.. beta

Until now, we've had two release channels - bleeding-edge-alpha, and daily-release-stable. Recent bugs have made it clear that we need a middle-ground, where significant changes can have a few days to surface their bugs (*like the upcoming RDTClient upgrade*).

Behind-the-scenes, I've moved my breaking-development changes into an unversioned, "alpha" chart, and promoted the existing alpha chart to beta. The idea is that beta gets upstream updates to containers immediately as they become available (*like Plex or Radarr updates*), whereas stable users continue to get these during the daily maintenance windows. 

New apps and breaking changes will be tested in alpha first, before being merged (*with much fanfare!*) into dev, and ultimately rolling into stable.

If you're a power-user/guinea-pig, and you'd like to be on the beta channel to receive and pre-test updates, let me know!

## Price-balancing is coming

I've been working on the [previously-announced](/open/feb-2024/#regular-pricing-re-balancing-starts-1-april-2024) price-balancing planned for 1 April. The goal is to better align our app prices with our costs, such that we achieve profitability (*or at the very least, break-even on cash expenses*).

!!! tip "Existing subscriptions won't be repriced"
    Existing subscriptions will not be repriced[^1]. The price you're currently paying for your apps, will remain the price, for as long as you're subscribed.

Because it's important to me that our pricing be transparent, I've deployed [kubecost](https://www.kubecost.com/) into the cluster - in a few days, we'll have accurate data on which to base per-app pricing, and I'll make another announcement. 

Kubecost does all sorts of clever things, but the basic take-away for us is that it can give us a base rate per-app calculated on actual CPU / RAM usage, and apportion the cost of "spare capacity" across the apps (*because it's impossible to run the cluster at 100% utilization!*). For details on how costs are calculated, if you like to geek out on this stuff, see the [OpenCost specification](https://www.opencost.io/docs/specification).

So, no firm details yet, just be advised that (a) change is coming, and (b) existing subscriptions will be unaffected.

## Bug fix : WebDAV rolled back to rclone 1.65.2

Overnight the cluster auto-updated our rclone instances to 1.66.0, and broke WebDAV access for subscribed tenants. I've rolled this back to 1.65.2 (*previously working version*), and prevented further automatic upgrades until we can fix this!

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"

[^1]: Because (1) I think it's a better experience for existing users, and (2) it turns out that adjusting rates on individual apps in combined subscriptions is a gigantic PITA in Wordpress/Woocommerce, and therefore not worth doing!
[^2]: On the surface, this looks like a loss, but we actually dropped down to around 3500 pods a week ago when I cleared out 10% wastage from pods which hadn't properly been cleaned up!