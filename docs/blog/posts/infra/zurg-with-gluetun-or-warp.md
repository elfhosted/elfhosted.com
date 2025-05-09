---
date: 2024-06-19
categories:
  - infra
tags:
  - zurg
title: Gluetun and WARP both with Zurg
description: While WARP appears to be working well with Zurg by default, the updates necessary to prefer gluetun are now ready
---

# Zurg will default to WARP if gluetun is not configured

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

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"
