---
date: 2024-02-12
categories:
  - CHANGELOG
tags:
  - infrastructure
title: ElfBot can symlink your messy remote folders
description: Your remote storage (usually debrid providers) is littered with content, all mostly unsorted, weirdly-named, and hard to play in Plex. ElfBot can now symlink these for you so that the Aars can import them and sort them beautifully for Plex to scan!
---

# Elfbot Symlinks Save Storage Clutter

If you've been using your Real-Debrid account outside of the RDTClient+Arrs symlink solution (*say, with [Debrid Media Manager](https://debridmediamanager.com), or [Stremio](https://elfhosted.com/guides/media/stream-from-real-debrid-with-self-hosted-torrentio/)*), you'll have lots of content sitting in `/storage/realdebrid-zurg/{movies,shows}` which is **not** symlinked to `/storage/elfstorage`, and thus **not** sorted into libraries managed by [Radarr][radarr] / [Sonarr][sonarr].

You **can** work around this by adding additional folders to your Plex libraries, but it's counter-intuitive, and messy, and it can be especially hard to track watched vs unwatched TV episodes, etc.

For media which **did** arrive via the Aars / RDTClient, the symlink design feature of RDTClient is genius:  you end up with a 2kb file instead of a 60GB file, which you can rename and move around your filesystem, sort into folders using the Aars, and delete and replace when an upgrade becomes available, etc.

We can now replicate the symlink design using ElfBot, to import all your existing Debrid content (*not sourced via RDTClient*) into Radarr / Sonarr for better organizing / managing!

For details, check out these pages:

<!-- more -->

* [ElfBot instructions](/app/elfbot/#how-to-import-symlinks) for symlinking content
* Importing external content via symlink for [Radarr](/app/radarr/#import-existing-remote-media)
* Importing external content via symlink for [Sonarr](/app/sonarr/#import-existing-remote-media)

## Scannarr, refactored

The way we added Scannar yesterday was confusing - it was attached to Radarr / Sonarr as a sidecar, and you didn't know whether it was running or not. Also, it seemed to fail with Sonarr if it happened to start **faster** than Sonarr. Finally, if you are using the OG torrentio indexer with a lot of content, you may have found scannarr causing you to hit rate-limits, making the torrentio indexer useless to you.

So I've refactored Scannar into a (free) product in the store - you'll find a HD version and a 4K version below. If you'd like your libraries auto-refreshed on a regular basis, you can opt into Scannar by adding one of the products below to your subscription:

* [Scannarr](https://store.elfhosted.com/product/scannarr)
* [Scannarr 4k](https://store.elfhosted.com/product/scannarr-4k)

## Calibre-Web OPDS server fixed

[Calibre-Web][calibre-web] includes an OPDS server, which allows you to read your ebooks directly from a supported device / app. This wasn't working, however, because our custom HTML error messages were overriding the 401 the OPDS server emitted, intended to cause your browser to prompt you for a username and password.

This is now resolved, and us ebook-geeks can enjoy one more way to consume our libraries!

## Tautulli exposed externally

At an insightful user's request, we're now exposing your [Tautulli][tautulli] instance publically, without SSO, since Tautulli itself relies on either its own auth, or linked Plex accounts. 

Now you can access your Tautulli URL from the official [iOS](https://apps.apple.com/us/app/tautulli-remote/id1570909086) or [Android](https://play.google.com/store/apps/details?id=com.tautulli.tautulli_remote) app, plus (presumably) whatever 3rd-party apps are available!

## Zurg rolled back to 0.9.3-hotfix.8

It's not exactly clear **why**, but the Puks The Pirate's famous [Sailarr’s Guide to Plex + Real-Debrid](https://puksthepirate.notion.site/puksthepirate/eebe27d130fa400c8a0536cab9d46eb3?v=0cf094af30854b628e47ec17010725a5) was recently updated to rollback from Zurg 0.9.3-hotfix.9 to 0.9.3-hotfix.8, citing:

> reverted back to zurg 0.9.3-hotfix.8 where refreshes work.

Since we've seen some users with issues recently about files which only appear after restarting zurg, I've rolled us back to hotfix.8 out of an abundance of caution.

I've also re-introduced the default repair option in our Zurg configs, since (a) it makes sense, and prevents some stalled download issues, and (b) the previous issues it caused with duplicates seem to be fixed now.

## RDTClient gets moooar RAM

[RDTClient][rdtclient] initially had a RAM limit of 1GB, which is way more than most instances use. Today we had a user report out-of-memory errors when processing their (large!) Real-Debrid database. I bumped the RAM limit for RDTClient up to 2GB, and the user's RDTClient settled in at 1.3GB used. So, our new limit for RDTClient is 2GB RAM!

## New 10Gbps ceph nodes flexing

Our new 10Gbps storage nodes for the `/config` volumes are coming into their own, already pushing out twice what the  previous 1Gbps nodes were capable of (*and not griding to a halt in the process!*):

```
root@goblin04 ~ # vnstat -l enp1s0
Monitoring enp1s0...    (press CTRL-C to stop)

   rx:     1.91 Gbit/s 187121 p/s          tx:     1.89 Gbit/s 184414 p/s^
```

## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 255 | -
:fontawesome-solid-hard-drive: Storageboxes mounted | 19 | -
:alien: Zurg mounts: | 108 | -4
:floppy_disk: ElfStorage in TBs | 53 | -
:material-dolphin: Tenant pods | 3492 | -24
:superhero: Elf-vengers | 4 | -
:student: Trainees | 2 | -
:material-bug: Bugz squished | 4 | -
:fontawesome-solid-gamepad: New toyz | 4 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"