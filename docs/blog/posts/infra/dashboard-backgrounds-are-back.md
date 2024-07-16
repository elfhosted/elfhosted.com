---
date: 2024-07-16
categories:
  - infra
tags:
  - CHANGELOG
title: Dashboard backgrounds are back!
description: We've snazzed up your dashboard, including working (again) backgrounds!
---

# Dashboard backgrounds are back!

!!! warning "Old / daily subscriptions will sunset from 1 Aug. Take action as described below"

    We have a new pricing model / bundle structure which requires resubscriptions (*the store can't migrate daily to monthly subscriptions for us*). Unless you take action described [here](/blog/2024/07/10/pricing-model-updated/), your ElfHosted subscriptions **will** stop working some time after 1 Aug 2024. 

    Details [here](/blog/2024/07/10/pricing-model-updated/)!

Tonight's user-facing change update is primarily UI polish - we've got the first instance of Zurg/Riven stats being reported on your dashboard, and the random background wallpapers are back! (*We assumed these to be lost in the #fluxpocalypse, but it turns out unsplash just turned off their HTTP-based endpoint we were using to download them!*)

Upon tonight's update, you'll end up with 2 random backgrounds on your apps dashboard, which may / may not look good. Think of these as placeholders - you can replace them with anything you like, provided you save your replacements into `config/homer/backgrounds`, and then restart homer with `elfbot restart homer` :thumbsup:

<!-- more -->

## Behind-the-scenes

Behind the scenes, tonight's update also combines Gatus (*health checks*) with Homer (*dashboard*), with Homer joining Gatus on the gnome (*observability*) nodes, rather than the power-house, contended, jack-of-all-trades elf nodes.

The motivation here is to provide core services (*health, dashboard, etc*) on nodes isolated from contended load (*Plex, Flaresolverr, etc*), so that even if the elf nodes are workin' hard, your dashboard and management tooling will be available and responsive.

!!! tip "Dedicated nodes are dedicated"
    [Hobbit](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/hobbit) and [Ranger](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/infinite-streaming-plus) users get their heavy hitters running on dedicated nodes anyway!

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 341 | -23
👾 Zurg mounts: | 153 | -13
⛰ Riven pods: | 49 | +3
🐬 Tenant pods | 2718 | -469 [^1]
🧑🏻‍🌾 [Hobbits](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/hobbit) | 23 | +8
🤠 [Rangers](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/infinite-streaming-plus) | 19 | +4
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 8 | -
🧑‍🎓 Trainees | 24 | +1
🐛 Bugz squished | 1 | -
🕹️ New toyz | 1 | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"

[^1]: This is expected - with the decommissioning of the 10 x HDD nodes, and the consolidation of some of the "minor" pods to reduce control-plane overhead, we can expect to see pod count dropping for a while. This is a good thing :)
