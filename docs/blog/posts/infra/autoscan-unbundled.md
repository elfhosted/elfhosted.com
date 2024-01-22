---
date: 2024-01-23
categories:
  - CHANGELOG
tags:
  - autoscan
title: Autoscan unbundled
description: We're gradually taming the zurg, autoscan is now its own (free) product

---
# Autoscan Unbundled

Last month, we [added Autoscan for free](/blog/2023/12/19/introducing-autoscan/), bundled with [Plex][plex], [Jellyfin][jellyfin] or [Emby][emby].

With the Jan 2024 influx of "[infinite streaming](https://elfhosted.com/guides/media/)" users, Autoscan has taken a front seat, since it's key to updating your streamer libraries when new content is added to your remote library.

A hiccup has emerged re our deployment strategy though - it turns out if you have both Plex **and** Jellyfin, then you'll get **two** copies of autoscan, and they'll fight with each other for access to their SQLite database :man_facepalming:

The workaround here has been simply to refactor Autoscan into its own product, and make it [available in the store](https://store.elfhosted.com/product/autoscan) (*for free*).

TL;DR : If you lost Autoscan and you want it back, add it to your subscription via the link above, and then "renew now" your subscription to force the store to update it immediately.

<!-- more -->

## Zurg eats a lot, hiccups

We've had some issues with [Zurg][zurg] 0.9.3, which our friend @yowmamasita has been tirelessly addressing. During tonight's maintenance window, I rolled us back to `v0.9.2-hotfix.4`, since I was still seeing users reporting issues with `0.9.3-hotfix.1`, and felt we should test it a little more thoroughly first.

Another unexpected side-effect of the user influx, is it seems that it's possible to completely max out our nodes' 1Gbps NICs with incoming Real-Debrid traffic, such that connectivity to our network storage suffers. (*and then bad things(tm) happen, like Plex loosing its `Preferences.xml` and needing to be reclaimed*)

I've applied a 40Mbit rate-limit to each Zurg instance while I gather more stats and baselines - it should be possible, in time, to fine-tune the amount of Zurgs to a node, and the amount of bandwidth to a Zurg, to provide reasonable and reliable streaming without impacting storage.

[Let me know][elf-help] if you're still having issues with Zurg, or if this 40Mbit rate-limit negatively impacts you. It's new territory, and there's bound to be a little trial-and-error!

## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 148 | +7
:fontawesome-solid-hard-drive: Storageboxes mounted | 12 | -2
:floppy_disk: ElfStorage in TBs | 48 | -
:material-sync: Rclone mounts | 53 | +10 [^1]
:material-dolphin: Tenant pods | 1518 | +68
:material-bug: Bugz squished | 2 | -
:fontawesome-solid-gamepad: New toyz | - | -

### Summary

As always, thanks for building with us - feel free to share suggestions, and your own ideas for new apps to add!

--8<-- "common-links.md"

[^1]: The big increase here is due to all the Zurg mounts!