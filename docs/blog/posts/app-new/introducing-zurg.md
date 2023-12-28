---
date: 2023-12-28
categories:
  - new-app
tags:
  - zurg
title: Stream directly from real-debrid thanks to Zurg!
description: Don't care to keep your media, just want to stream it from Real Debrid using Plex/Jelly/Emby? Zurg makes this happen!

---
# Stream from Real Debrid with Plex using Zurg

Thanks to a recent user request, we now have a way to stream media directly from your Real-Debrid account as if it were on an attached filesystem, without having to download / transfer it first.

<!-- more -->

It works like this - you give [Zurg][zurg] your [Real-Debrid API token](https://real-debrid.com/apitoken), and a bunch of regular expressions (regexes) explaining roughly what filenames match to what kind of content.

Zurg then scrapes your Real-Debrid account, applies the regexes, and presents a WebDAV endpoint to "browse" your files.

Next, we perform an rclone WebDAV mount, and attach the zurg-exposed WebDAV URL to your apps. Now, in `/storage/real-debrid-zurg`, you'll find directories matching the regexes you defined (*"movies", "tv", "music", etc*). If you add `/storage/real-debrid-zurg` to your [Plex][plex] / [Jellyfin][jellyfin] / [Emby][emby] libraries, suddenly you can stream from Real Debrid as if the media were locally attached, without any delay for download / transfer, etc! 

See the [Zurg][zurg] page for more details, and instructions on how to set it up!

## What's new?

### 50% off of ElfStorage until 2024 ($3/TB)

Give the ongoing growth of ElfStorage usage, I've further built out our ElfStorage infrastructure to 10 storage nodes, so that we can take advantage of "[erasure coding](https://docs.ceph.com/en/latest/rados/operations/erasure-code/)" (8+2), and reduce the disk space overhead from 50% to 12.5%. 

As a result of all these upgrades, we now have (a) cheaper storage over the long term, and (b) excess unused storage in the short term (*and \(c) a larger bill from Hetzner!*)

So, I've setup a [50% off sale of ElfStorage](https://store.elfhosted.com/product/elfstorage/) for the remainder of 2024, dropping it to $3/TB/month, as discussed [here](https://www.reddit.com/r/seedboxes/comments/18rkwm6/50_off_storage_3tb_at_elfhosted_until_2024/) - if you've been thinking about adding some extra ElfStorage, then now is the time to pounce!

### Bugz squished

#### WebDAV export working again

A recent improvement (*auto-obscuring credentials for rclone mounts*) broke the WebDAV access product (*which allows you to copy to/from your storage using WebDAV*), because the SKU for the webdav unfortunately contained the string "rclone" :man_facepalming:.

This is fixed now, but if you've previously used WebDAV access, you'll want to update your config, since the target URL syntax has changed. See [WebDAV Access][webdav] for details and further documentation.

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers | 90
:fontawesome-solid-hard-drive: Storageboxes mounted | 19
:material-sync: Rclone mounts | 7
:material-dolphin: Tenant pods | 820
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 1

### Summary

As always, thanks for building with us - feel free to share suggestions, and your own ideas for new apps to add!

--8<-- "common-links.md"