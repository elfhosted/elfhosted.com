---
title: ElfHosted TorBox
slug: TorBox
description: TorBox is a next-generation "Debrid" provider, offering 
upstream: https://torbox.app
links:
works_with:
- RDTClient
- Prowlarr
- Blackhole
---

# {{ page.meta.slug }}

TorBox is a popular newcomer to the "debrid" downloader landscape. TorBox's core differentiator is that they do not limit users to a set amount of IP addresses, but rather they allocate download "slots". Once the slots on your plan are full, you can continue to add downloads to a queue, which will be serviced as slots become available.

You can use TorBox with ElfHosted to:

* Stream media via Stremio, using our [Stremio addons][stremio-addons]
* Run a classic "infinite" [Plex](/guides/media/stream-from-torbox-with-plex-radarr-sonarr-prowlarr/) / [Emby](/guides/media/stream-from-torbox-with-emby-radarr-sonarr-prowlarr) / [Jellyfin](/guides/media/stream-from-torbox-with-jellyfin-radarr-sonarr-prowlarr) stack with [Radarr][radarr], [Sonarr][sonarr], and [Prowlarr][prowlarr], using either [RDTClient][rdtclient] or West's [BlackHole][blackhole] scripts to create symlinks
* Run a next-gen "infinite" [Plex](/guides/media/docs/guides/media/stream-from-torbox-with-plex-riven/) / [Emby]((/guides/media/docs/guides/media/stream-from-torbox-with-emby-riven/)) / [Jellyfin]((/guides/media/docs/guides/media/stream-from-torbox-with-jellyfin-riven/)) with [Riven][riven]