---
date: 2024-02-01
categories:
  - CHANGELOG
tags:
  - torrentio
  - stremio
  - realdebrid
title: Supporting Stremio
description: We've dealt with scaling issues (both electronic and biological) and are now ready for a stremio influx! (I think...)
---
# Supporting Stremio

So we've [scaled our infrastructure for growth](/blog/2024/01/28/scaling-the-gigabytes/), and have started to [grow the Elf-Vengers team](/blog/2024/01/29/scaling-the-humans/) to help new elves get started.

We've spent the last few maintenance windows applying bugfixes, including:

* [RDTClient][rdtclient] wasn't symlink-downloading properly due to the tightened restrictions we place on our pods - we don't let them run as root (*yay!*), but RDTClient is doing **something** which requires root (*boo!*), and it's not logging it, so (*for now*), we're choosing the [lesser of the two weevils](https://www.youtube.com/watch?v=Y-aPp7Kiiyg), and preferring a working pod over a secured, non-working one!

* [ElfBot][elfbot] wouldn't properly claim or restart Plex under some conditions, resulting in users **thinking** they'd claimed a server, when in fact they hadn't.

* rclone + zurg was consuming lots of ephemeral space (*very quickly)*, causing Kubernetes to restart the rclone CSI pod, and briefly disrupt connectivity to your RD mounts. This one we finished tonight, it basically required the reinstallation of all our our worker nodes with a larger [drive partitioning scheme](https://github.com/funkypenguin/elf-infra/blob/ci/roles/hetzner-reinstall/tasks/templates/installimage-elf.conf.j2#L17-L18). 

* I've been replacing our 64GB nodes with 128GB ones - they seem less susceptible to slow I/O issues, perhaps because ceph has more RAM to work with.

Now that we've done some housekeeping, we're ready for some new houseguests...

<!-- more -->
## Torrentio refugees

[Torrentio](torrentio.strem.fun) is a free indexer which scrapes public torrent trackers, and then uses your debrid credentials to check whether your provider has those torrents cached. It returns a list of cached torrents.

This is useful, for example, to have [Radarr](radarr) / [Sonarr](sonarr) find debrid-cached torrents to send to [RDTClient][rdtclient], to download or to "fake download" using symlinks, for easy streaming.

The most popular use of torrentio is to facilitate turn-key streaming using [Stremio](https://stremio.com), a free and polished streaming client with a **huge** addon ecosystem. The advantage of Stremio is that it runs in a lot of places Plex doesn't, like crummy little $20 Android TV setups.

Recently the torrentio+stremio combination has [become so popular](
https://www.reddit.com/r/StremioAddons/comments/1abli5e/stremio_and_torrentio_are_a_fascinating_lesson_in/) that the (free) service has started to fail, and [r/debrid](https://reddit.com/r/realdebrid) is plagued by non-technical users complaining about how "realdebrid is down" :facepalm: (*and in fact, the rate-limits employed impact users who run automation to populate big media libraries*)

Enthusiasts have [found and forked](https://www.reddit.com/r/StremioAddons/comments/198pibw/forked_torrentio_for_self_hosting/) the original torrentio code, and [various efforts](https://github.com/ben-2357/Torrentio-sh-Setup-Guide) are underway to reverse-engineer scrapers etc, to "self-host" torrentio..

.. see where I'm going with this?

So, I present to you, our own torrentio instance, at https://torrentio.elfhosted.com!

The idea is this:

1. Anybody cane use the instance, rate-limited to 1 request every 10 sec (*enough for casual streaming*)
2. ElfHosted users can subscribe to their own instance, rate-limited to 1 request every second
3. Elfhosted apps get free access to the indexer internally, with no rate-limits

Here's an easy guide : [Stream from Real-Debrid using Self Hosted Torrentio Addon](/guides/media/stream-from-real-debrid-with-self-hosted-torrentio)

I plan to announce the free instance on [r/realdebrid](https://reddit.com/r/realdebrid) and [r/StremioAddons](https://www.reddit.com/r/StremioAddons) in the next 12h or so, please share do it wherever you hand out (*Discords, Reddit, etc.*)

## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 192 | +22
:fontawesome-solid-hard-drive: Storageboxes mounted | 18 | -
:floppy_disk: ElfStorage in TBs | 51 | +2
:material-sync: Rclone mounts | 112 | +13
:material-dolphin: Tenant pods | 2532 | +321
:superhero: Elf-vengers | 3 | -
:student: Trainees | 2 | -
:material-bug: Bugz squished | 4 |
:fontawesome-solid-gamepad: New toyz | 1 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"
