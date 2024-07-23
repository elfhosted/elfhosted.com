---
date: 2024-07-23
categories:
  - infra
tags:
  - CHANGELOG
title: Plex_debrid gets Zilean support
description: Our plex_debrid instances get Zilean support, customizable watchlist loop intervals, and bugfixes
---

# Plex_debrid gets Zilean support, fixes

!!! warning "Old / daily subscriptions will sunset from 1 Aug. Take action as described below"

    We have a new pricing model / bundle structure which requires resubscriptions (*the store can't migrate daily to monthly subscriptions for us*). Unless you take action described [here](/blog/2024/07/10/pricing-model-updated/), your ElfHosted subscriptions **will** stop working some time after 1 Aug 2024. 

    Details [here](/blog/2024/07/10/pricing-model-updated/)!

Plex_debrid's [GitHub repository](https://github.com/itsToggle/plex_debrid) has been stale since Dec 2023, and achived since May 2024. Our [attempts to contact the developer](https://github.com/elfhosted/enhancements/issues/7) to offer stewardship of the project have been unfruitful thus far.

We've had our [own fork](https://github.com/elfhosted/plex_debrid) of the plex_debrid repo for a while, to manage a few fixes (*like Trakt auth*), but \@ron has taken it to a whole new level by adding Zilean support, and a parametized watchlist search interval (*original is hard-coded to 30m*).

I [announced](https://www.reddit.com/r/RealDebrid/comments/1e9vjtg/plex_debrid_maintenancefeature_fork_with_trakt/) our repo on Reddit today, with the intention of attracting more users and hopefully more PRs, so that we can continue to improve upon and support plex_debrid for ElfHosted users.

To activate Zilean support in plex_debrid, add Zilean as a scraper source at `Options/Settings/Scraper Settings/Sources` - our internal Zilean instance is addressed at `http://zilean.zilean:8181`.

To adjust your search-my-watchlist interval, change `Options/Settings/UI Settings/Watchlist loop interval (sec)` accordingly.

## Riven Comet support, duplicates fixed

Riven 0.8.0 shipped yesterday, but without Comet support due to a bug. This is now resolved, so your Riven should start searching the ElfHosted Comet database from tonight's rollout.

Also, duplicate folders will no longer cause Riven to crash-and-burn, but just to log an error and continue on its way :muscle:

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 327 | -2
👾 Zurg mounts: | 127 | -26
⛰ Riven pods: | 50 | +2
🐬 Tenant pods | 2651 | -18
🧑🏻‍🌾 [Hobbits](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/hobbit) | 29 | +2
🤠 [Rangers](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/infinite-streaming-plus) | 19 | -
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 8 | -
🐛 Bugz squished | 1 | -
🕹️ New toyz | 1 | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"
