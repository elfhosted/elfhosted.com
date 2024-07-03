---
date: 2024-06-25
draft: true
categories:
  - infra
tags:
  - symlinks
title: Elf-sclusive "plus" packages (1/4 of a dedicated host) now available
description: If you're a happy elf, but you dream of moaar speed/bandwidth, our new "plus" packages might suit you - share a full dedicated host with 3 other elves, w/ hardware transcoding, minimal limits, high trust
---


## Who's the (storage) boss?

As of the most recent maintenance (`v1.40.0), you'll notice a new pod in your namespaces, named "storageboss". This pod connects to all your storage, and then shares this storage with the **other** pods via samba. You can delete and restart it like any other pod, but doing so will temporarily interrupt storage attached to all your pods, so .. don't :grin:

This is a change from the previous design which attached storage directly to pods using Ceph RBD / CephFS, and was implemented to address the massive I/O bottleneck that our workloads place on CephFS (*which is why we migrated Plex and the Aars off, in Feb*), and to allow single-mount block volumes to be shared among multiple pods (*so now, you can see your Plex data in Filebrowser again!*)

Critically, consolidating storage on a single pod is a key step towards making our design more portable, so that we can establish ElfHosted clusters in other datacenters besides for Hetzner, in Germany (*our US Elfies are particularly excited about this!*).

The change to storage mounts has been tested as far as I can, not being a heavy user of all the apps. If you find an app erroring about missing data / directories, there may be configuration changes required that I've missed, so please drop the details into an [#elf-support][elf-support] ticket!




# Elf-sclusive "plus" packages now available

Further to the [recent blog post](/blog/2024/06/17/warping-around-realdebrid-issues/) about how we now need a VPN to use Zurg with RD, the necessary changes to our design are now done to support this scenario:

1. If you don't have gluetun, your Zurg pod will use WARP
2. If you [add gluetun](/app/gluetun/), your Zurg pod will use gluetun and not WARP
3. If you remove gluetun again, your Zurg pod will revert back to WARP

To make this happen without impacting users bundles, we attach WARP **and** gluetun to your containers, but only one of them is active at a time. To confirm your connection, use the pod logs as illustrated in the gluetun video, or the  troubleshooting video below.

<!-- more -->

### 300Mbps Plex Boost available

Some users who share their Plex with a larger group of family / friends, have asked whether they can pay to increase their Plex streaming rate beyond the default 150Mbps. With the help of some eager elf-a-testers, we now offer a [300Mbps boost for Plex](https://store.elfhosted.com/product/plex-booster-upgrade), which will simply double your  Plex egress rate limit (*enough for 2 x 4K HDR streams, or about 10 x 1080P streams*)

Jellyfin / Emby users, we'll get boosts available for you too, soon! Hit me up if you'd like them sooner rather than later!

## Troubleshooting guide

The ElfVengers have been hard at work trying to improve our support flow - we've recently moved from private-tickets-for-all-support, to public-support-for-all-but-sensitive-tickets, and this has coincided with (*or caused?*) in increase in community discussion / help, which has been great!

Part of the process is a new friendly bot ("Spanky"), which can move support requests into individual topics under [#elf-support](https://discord.com/channels/396055506072109067/1245513340176961606). Spanky's still got some quirks, but our newest ElfVenger \@mxrcy is rapidly making improvements!

When you create a support topic (*or one is created for you, based on a question in #elf-friends*), Spanky will prompt you to review our troubleshooting guide - answers to common "how do I?" questions will be found there. Here's a quick video re troubleshooting, for the visual learners:

<iframe width="560" height="315" src="https://www.youtube.com/embed/gdZaPHvpJCo?si=FPScroHIHfUMuOMe" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 353 | -1
👾 Zurg mounts: | 144 | +3
⛰ Riven pods: | 24 | -
💾 [ElfStorage](https://elfhosted.com/what-is/elfstorage/) in TBs | 111 | +1
🐬 Tenant pods[^1] | 3202 | -18
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 8 | -
🧑‍🎓 Trainees | 23 | +1
🐛 Bugz squished | - | -
🕹️ New toyz | 1 | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"
