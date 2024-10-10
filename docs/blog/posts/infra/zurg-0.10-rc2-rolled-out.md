---
date: 2024-06-11
categories:
  - infra
tags:
  - zurg
title: Zurg 0.10.0rc2 rolled out, repair enabled
description: After positive testing, we're rolling out Zurg 0.10rc2, which includes better repairing (no more hanging Plex scans), and unpacking of RAR archives!
---

# Zurg 0.10.0rc2 rolled out, love live repairman!

It's been 4 days since [Zurg 0.10.0rc2 was released](https://www.reddit.com/r/debridmediamanager/comments/1d957ib/new_rc_out_0100_release_candidate_2/) (*to sponsors*), and we've had a few brave Elves testing it out. So far, there are no show-stoppers, so we've now rolled v0.10.0rc2 out to all users.

Significant improvments over v0.9.x are:

* :one: Repairing works again, without causing plex to stall its scans
* :two: Zurg can now co-operate with Real-Debrid to extract RAR-compressed "downloaded" media!
* :three: Zurg now supports non-video files (*i.e., audio*)

Read on for how to enable the new features...

<!-- more -->

Repair should already be enabled in your config, but to take advantage of RAR extraction and extra playable content, you'll want to add something like this to your Zurg config in `config/zurg/config.yml`

```
rar_action: extract
addl_playable_extensions:
- mp3
- flac
```

(See the [upstream minimal config example](https://gist.github.com/yowmamasita/ed1be7eff7847a19be78f98d9ea80911))

!!! question "Can I reset to default/optimal config?"
    If you want to reset your Zurg to the latest defaults, run `elfbot reset zurg --yesiamsure` via FileBrowser, wait a few minutes, and then edit `config/zurg/config.yml` to re-insert your RD API key.

## Riven is rising..

There's been much excitement in Discord today about [Riven][riven], the new name for Iceberg, and the successor to [plex_debrid][plex-debrid]. Be warned, it's still under active development, but if you're the sort who likes to tinker, and live on the bleeding edge, then Riven is for you!

The thinking is that Riven will be functionally able to replace Radarr, Sonarr, Prowlarr, Autoscan, and RDTClient, as an "all-in-one" tool to interface Plex/Jellyfin/Emby with your Debrid media.

![](/images/riven-teaser.png)

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 333[^1] | -8
👾 Zurg mounts: | 143 | +27
💾 [ElfStorage](https://elfhosted.com/what-is/elfstorage/) in TBs | 105 | +12
🐬 Tenant pods | 3471 | +481
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 9 | -
🧑‍🎓 Trainees | 22 | -
🐛 Bugz squished | 2 | -
🕹️ New toyz | 2 | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks!

[^1]: I don't really understand why subscribers have **decreased** over the past 3 weeks (*since the last metrics were recorded*), but Zurg mounts, pods, and even Ceph storage have **increased**. One possibility is that Wordpress is excluding trial users from our subscriber count - another is that over time, plex_debrid users are "upgrading" to the "[Advanced Infinite Streaming](/guides/media/stream-from-real-debrid-with-plex-radarr-sonarr-prowlarr/)" bundle, which implies more pods...

--8<-- "common-links.md"
