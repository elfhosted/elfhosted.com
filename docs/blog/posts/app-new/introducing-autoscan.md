---
date: 2023-12-19
categories:
  - new-app
tags:
  - autoscan
title: Your ElfHosted streamer now includes autoscan!
description: Tired of waiting for your massive media library to rescan? All streaming apps now get FREE bundled autoscan, for instant Library updates!
---
# Your ElfHosted streamer now includes autoscan!

Our users may have large media libraries stored either on [ElfStorage][elfstorage], or some other, BYO storage, which may be subject to API ratelimits, increased latency, etc. As such, the default behavior of rescanning the entire media library at a set interval is both resource-intensive and time-consuming.

Thanks to user suggestions, we've now bundled [Autoscan][autoscan] with our streamers ([Plex][plex] / [Jellyfin][jellyfin] / [Emby][emby]). 

By simply adding a webhook connection on the Arrs (*[Radarr][radarr], [Sonarr][sonarr], [Lidarr][lidarr], [Readarr][readarr]*), you can configure the Arr to fire a webhook at Autoscan when new media is downloaded. 

Autoscan will then use an API token to instruct Plex / Jellyfin / Emby to rescan **just** the parent folder that the media appeared in, so that your library is instantly updated, rather than relying on regular filesystem scans.

See the [Autoscan][autoscan] page for instructions on how to set it up!

<!-- more -->

## What's new? ##

### Bugz squished

#### Mattermost attachments working again

The HDD->SSD migration caused a permissions issue for Mattermost file uploads, which has now been resolved. (*Of course, if you're a serious Mattermost user, it'd make more sense to send all of your file uploads to an S3 bucket, so that you're not constrained by our volume sizes*)

#### 404 bug still lurking

The 404 / expiry bug which I **thought** I'd fully solved popped out of another hole today. I've dealt with this issue as well, but if you do find yourself seeing 404s when you think you shouldn't, click that [#elf-help](https://discord.com/channels/396055506072109067/1119478614287712337) link!

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers | 84
:fontawesome-solid-hard-drive: Storageboxes mounted | 23
:material-sync: Rclone mounts | 8
:material-dolphin: Tenant pods | 802
:material-bug: Bugz squished | 2
:fontawesome-solid-gamepad: New toyz | 0

### Summary

As always, thanks for building with us - feel free to share suggestions, and your own ideas for new apps to add!

--8<-- "common-links.md"