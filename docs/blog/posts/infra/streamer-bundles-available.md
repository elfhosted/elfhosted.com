---
date: 2023-08-22
categories:
  - CHANGELOG
tags:
  - plex
  - jellyfin
  - emby
title: Discounted streamer bundles now available
description: To improve new-user-friendliness, we've got some new bare-bones bundles for Plex, Jellyfin, and Emby
---

# New basic streaming bundles

As alluded to a few days ago, now that we can sell storage in 1TB "chunks", I've created some [discounted bundles](https://store.elfhosted.com/product-category/bundles/) in the store for minimal streaming stacks.

For users who just want to get started with the basic toolset for media management, we now have bundles with Jellyfin/Plex/Emby, Radarr, Sonarr, and SABnzbd, with the option for 1TB extra storage bundled in.

The pricing is a bit of an experiment - feel free to send feedback re how you think these stack up :)

!!! question "Why monthly, and why bundled discounts?"

    I wanted to make it easy(ier) for new users to compare our tools with other providers, and the bundles are discounted to make them slightly "stickier". A user unfamiliar with ElfHosted (*ElfBuckz, etc*) could simply purchase a bundle in one move, and then spend their $10 ElfBuckz on ancillary apps like [Overseer][overseerr], [Prowlarr][prowlarr], etc.

<!-- more -->

### Bugz squished

#### SeaFile (more) Fixed

After yesterday's Seafile fix, we discovered that while the native apps worked fine, actually using a browser would fail to upload into Seafile, because of mixed content warnings (*Seafile was defaulting to HTTP links, which were just being redirected to HTTPS by Traefik*). This is now manually fixed for existing users, and automatically fixed for future users!

!!! tip "Seafile talks to rclone"
    TIL that [Seafile][seafile] can be setup as an [rclone remote,](https://rclone.org/seafile/) so that you can use it for simple offsite storage, without having to use one of the [official clients](https://www.seafile.com/en/download/)!

#### qBittorrent's lockfile

Another puzzling bug bit the dust today - it turns out that if qBittorrent doesn't exit properly, it leaves a `lockfile` behind, which persists with the rest of your config, and causes qBittorrent to fail to start the next time. We now auto-delete this lockfile every time the pod starts.

#### gluetun's DNS schenanigans

A final weird bug - we found that https://linuxtracker.org was unreachable via gluetun-protected torrent clients. This seems to be related to [gluetun](https://github.com/qdm12/gluetun)'s DNS proxy / filtering features, which are intended to protect a user from leaking DNS queries. This has been fixed (*by turning it off!*)

### Summary

As always, thanks for building with us - feel free to share suggestions, ideas, and whatever you ate for breakfast today! :cooking:

--8<-- "common-links.md"