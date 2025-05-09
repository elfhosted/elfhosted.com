---
date: 2024-02-11
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Scannarr improves searching for Radarr / Sonarr
description: Your Radarr / Sonarr instances now include Scanarr, to trigger automatic searches (since RSS doesn't work with torrentio/knightcrawler)
---

# Scannarr added to Radarr / Sonarr

You might have noticed your [Radarr][radarr] / [Sonarr][sonarr] complaining about the lack of RSS-capable indexers. This is because, unlike some popular trackers, the [Prowlarr knightcrawler / stremio indexer](https://github.com/geek-cookbook/elfhosted-prowlarr-indexers) doesn't (*and can't*) include an RSS feed.

Sonarr especially relies on an RSS feed to alert it to when new episodes are out, and ready to search. Without an RSS source, you have to manually trigger searches for your TV series, in order to grab new episodes when they're downloaded.

Thanks to [Scannarr](https://github.com/Pukabyte/scannarr), we now have a solution!

<!-- more -->

## Simple Scannarr Solution

Scannarr is now deployed as a simple sidecar to all of our Radarr / Sonarr (HD and 4K) pods, and will trigger an automatic search of all your monitored content, every 2 hours. You don't have to do or change anything, this just means that you'll get more successful searches for your historical backlog and monitored series, over time.

## PikPak and Debrid-Link mounts

At user requests, I've added the following two new types of storage mounts:

* [PikPak](https://store.elfhosted.com/product/pikpak-webdav-mount)
* [Debrid-Link](https://store.elfhosted.com/product/debrid-link-webdav-mount)

## Plex Meta Manager's ENV vars

[Plex Meta Manager][plex-meta-manager] (PMM) is a CLI tool which obsessively tidies up, augments, and expands your Plex library. Out-of-the-box, PMM runs daily, but it's sometimes desirable to change the run frequency, or to force it to run immediately.

Thanks to an enthusiastic user, we now have ENV var support for Plex Meta Manager, via [ElfBot][elfbot]. More details can be found on the [Plex Meta Manager's documentation page][plex-meta-manager].

## Bugfix - unnecessary restarts on rclone mounts

A user highlighted a completely unnecessary restart of all their pods today - it turns out there was a bug in the way the provisioning process would handle a renewal of an rclone mount (*basically, any storage mount other than storageboxes*).

To simplify onboarding, we ask users to enter their **actual** credentials for an rclone mount, but in the backend, we have to feed rclone an "obscured" password in order to perform a mount (*trying to get users to enter an obscured password on signup was just too hard*). The results of an `rclone obscure` of the same password will change each time though, like this:

```bash
~ ❯ rclone obscure batman                                                                                                                                                         22:19:46
j9J_IY-56NfMf-X4awms-c8giABhsg
~ ❯ rclone obscure batman                                                                                                                                                         22:19:51
5qS5GclEn6vN8A7--DcJulll4YceZg
~ ❯
```

So what was happening was that every time an rclone mount renewed, we'd get a fresh rclone-obscured version of the credentials generated, and a [big blob of checksums](https://github.com/geek-cookbook/elf-charts/blob/main/charts/other/myprecious/templates/configmaps/configmap-storage-changed.yaml) would get updated. This checksum "blob" update would trigger a restart of all pods using the storage mount. You see where this is going...? :)

So probably this auto-rebooting-on-renewal bug been happening for a while, but remained unnoticed because (a) a restart is usually pretty fast, and (b) every user's subscription renews at different times of the day.

I'm happy to say that with a bit more logic / sanity-checking, this bug is :gravestone:, and won't be back to bother our stability again!

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"

[^1]: Includes 2 x 26 new sharded flux pods!