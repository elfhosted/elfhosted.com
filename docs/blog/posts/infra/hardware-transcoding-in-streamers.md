---
date: 2023-07-25
categories:
  - build-in-public
tags:
  - plex
  - emby
  - jellyfin
title: Hardware transcoding is now available
description: Our streamers now support hardware transcoding!
---

# Hardware Transcoding now available

Thanks to helpful elf-a-testers, we now have hardware transcoding support in [Jellyfin][jellyfin], [Emby][emby], and [Plex][plex] (*PlexPass required*).

## Why is this a big deal?

Previously, the streamers would use CPU resources to transcode any media they deemed incompatible with your client. The only way to prevent one streamer hogging all the CPU was to apply a CPU limit (*4 vCPUs*) to each streamer, roughly tested to support up to 3 1080P CPU transcodes. This still places a heavy load on our nodes, given each node only has 16 CPUs. Oh, and 4K transcoding was just a total no-go, even with 4 vCPUs!

After enabling Intel QuickSync Video (QVS) transcoding in Jellyfin, I was able to transcode 4K HEVC media, consuming only 250m (1/4 of a vCPU)[^1] Needless to say, this makes our platform a **lot** more scalable!

## How well does it work?

I.. don't know. Plex has one lonely toggle which turns transcoding on/off, and Jellyfin has about 2 pages of advanced options which affect transcoding performance! It'll take a little trial-and-error to find the sweet spot per streamer, and it's impossible to test all variations / clients. So I've rolled transcoding support out to all (beta) users, and reduced the CPU allocation to the streamers to 500m (1/2 vCPU), so that CPU-based transcoding **will** fail. This may be a little extreme, but given we can now transcode 4K on 1/4 vCPU, it's more transcoding grunt than we had previously.

It's likely that we'll refine the transcoding support / parameters over the next few days, so please feel free to play around, test, and send feedback in [Discord][discord].

Of course, as always, for optimal experience from your streamer, avoid any transcoding whatsover. (*Direct-playing 4K media consumes 0.01 vCPU!s*)

Read on for smaller announcements...

<!-- more -->

## Other changes

### Improvementz

* :white_check_mark: Port forwarding for qBittorrent PIA BYOVPN users is now working properly
* :white_check_mark: Added docs describing what [ElfStorage][elfstorage] and [StorageBoxes][storagebox] are, and when/how they should be used

### Upcoming

* [ ] Add a link on the store user account page to the app dashboard (*not done yet, but I've found out [how to do it](https://github.com/woocommerce/woocommerce/wiki/Customising-account-page-tabs)*)
* [ ] Send email to user with link to their dashboard (*enabled but apparently not working, grr*)
* [ ] Make checkout fields work better with browser auto-fill (*is this a Woocommerce/Wordpress issue?*)

### Summary

Thanks for building with us - stay tuned!

--8<-- "common-links.md"

[^1]: I did have mixed results with various 4K content. In some cases, transcoding still wouldn't make the media play smoothly.

