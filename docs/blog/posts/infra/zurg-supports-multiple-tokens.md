---
date: 2024-06-29
categories:
  - infra
tags:
  - zurg
title: Zurg multi-token support, price refactor coming 1 Aug
description: Our Elf-hero, @yowmamasita, has built multi-token support into Zurg, so you can create a "fallback" account if you get rate-limited
---

# Zurg multitoken support solves slowdowns

\@yowmamasita has added a neat feature to Zurg, which takes advantage of the new "[zurgtorrent](https://github.com/debridmediamanager/zurg-testing/wiki/zurgtorrent-v0.10)" feature, allowing you to add multiple RD tokens to your Zurg account. This means that your library stays in your primary account, but your backup tokens will be used to stream if your main account temporarily ends up in "RD Jail". Read more details [here](https://www.patreon.com/posts/how-to-bypass-107090551).

<!-- more -->

## Jellyfin rolled back to Elves

While the recent move to make the Giants (*10Gbps nodes*) preferable for the Plex pods has gone well, some Jellyfin users have reported significantly poorer streaming performance on the giants. Given the possibility that the problem is related to the change of CPU architecture (*Intel i9-9900k vs Ryzen 5 3600*), I've rolled Emby / Jellyfin back to being "elf-only" for now.

## End of grandfathered pricing from 1 Aug

On 1 Aug, we will have been "in prod" for a year (*and [not profitable yet](/open/)!*), and while we [repriced new subscriptions in April 2024](https://elfhosted.com/blog/2024/03/20/planned-for-1-april-2024/), "legacy" subscriptions were grandfathered in at their original price, which was mostly the result of very vague original guesswork.

We'll be doing another price adjustment from 1 Aug (*resource requirements change over time, and we want to contribute more to support the developers of our core open-source tools*), and those grandfathered subscriptions will be repriced on renewal to match the current rate, which will be our ongoing policy (*dynamic subscription pricing with reasonable and transparent advance notice*).

I'll finalize the new pricing in the June's ElfReport report in a few days, giving monthly subscriptions a full subscription cycle at the old rates before the new ones kick in.

## AI product logos

Do you like messing with AI image generation? We're planning to replace some of the boring :sleep: product images on the store with fancy, AI-generated art, typically involving elves! 

If you'd like to contribute some ideas, or just join in the fun, jump in to the [AI-enhance-the-store thread](https://discord.com/channels/396055506072109067/1256221423123304468)!

## Coming up..

Look forward to updates in the near future re Comet (*a new Stremio addon*), a trial of our US cluster (*I registered `elfhosted.us` today*), and an improvement in the store layout / structure! :)

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"
