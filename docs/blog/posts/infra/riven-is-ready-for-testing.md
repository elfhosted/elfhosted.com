---
date: 2024-06-12
categories:
  - infra
tags:
  - riven
title: Riven is Ready for Revenue Sharing (and testing)
description: While we don't yet have the final UI ready in Riven, we've now got a UI of sorts, such than you can see pretty logs in realtime. Also, 30% of your Riven subscription goes to fund development, so show @spoked some love!
---

# Riven is Ready for Revenue Sharing (and testing)

Iceberg has "melted" from the store, to be replaced with [Riven](https://store.elfhosted.com/product/riven), and the [Riven/Plex Infinite Streaming bundle](https://store.elfhosted.com/product/infinite-plex-riven-streaming-bundle).

While we wait for UI dev to complete, I've replaced the UI with a realtime, live view of your Riven logs, via your browser (*launched from your dashboard*). From this UI, you can `CTRL-C` to restart (*it's not actually the logs, it's the backend process itself!*), and watch Riven do its magic in realtime.

!!! important "Riven Revenue Sharing"
    Riven is the first ElfHosted product which falls under a new, experimental "revenue sharing" model. Because [@spoked](https://github.com/sponsors/dreulavelle) is working so closely with the ElfHosted team to make Riven work :100: with our platform, 30% of your subscription will go to the Riven devs to support further development! :heart:

    You can also join me in sponsoring [@spoked](https://github.com/sponsors/dreulavelle) directly, via [GitHub Sponsors](https://github.com/sponsors/dreulavelle)

Remember, this is all very cutting-edge and geeky, so some assembly will be required. Jump into our dedicated [#Riven forum topic](https://discord.com/channels/396055506072109067/1249492216758407168) with your bug reports, feature requests, and feedback!

<!-- more -->

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 326[^1] | -7
👾 Zurg mounts: | 141 | -2
💾 [ElfStorage](https://elfhosted.com/what-is/elfstorage/) in TBs | 106 | +1
🐬 Tenant pods | 3692 | +221
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 9 | -
🧑‍🎓 Trainees | 22 | -
🐛 Bugz squished | - | -
🕹️ New toyz | 1 | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks!

[^1]: I don't really understand why subscribers have **decreased** over the past 3 weeks (*since the last metrics were recorded*), but Zurg mounts, pods, and even Ceph storage have **increased**. One possibility is that Wordpress is excluding trial users from our subscriber count - another is that over time, plex_debrid users are "upgrading" to the "[Advanced Infinite Streaming](/guides/media/stream-from-real-debrid-with-plex-radarr-sonarr-prowlarr/)" bundle, which implies more pods...

--8<-- "common-links.md"
