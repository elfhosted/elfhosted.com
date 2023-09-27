---
date: 2023-09-27
categories:
  - new-app
tags:
  - tdarr
title: Tada, it's Tdarr!
description: Are you annoyed by your streamer transcoding your media just because of audio track incompatibilty? Do you value efficient storage of your media library using modern codecs?
---
# Tada, it's Tdarr! 🎉

I was trying to catch up on my 1080P movie backlog on my laptop recently, only to discover that [Jellyfin][jellyfin] would transcode the movie since the 5.1 audio track apparently won't work on modern Firefox on my modern Macbook (*grr, why? :man_facepalming:*)

Rather than just watching on my nVidia Shield (*which plays **everything** I throw at it*), I instead spent about 6 hours (*I never even got to watch the movie!*) adding [Tdarr][tdarr] to our platform, with a mind to having a 2-channel audio track added to my existing media.

So, we now have [Tdarr][tdarr] available! :partying_face: It works as advertised, although it turns out to be quite tricky to configure, and even trickier to make work with the Quick Sync Video hardware transcoding support in our 9th-gen Intel nodes.

![Screenshot of Tdarr](/images/screenshots/tdarr.png)

A few peculiarities to our implementation:

1. While Tdarr can support multiple, distributed worker nodes, we just use one worker node, paired with the Tdarr server, for easy resource isolation, and because our transcoding "scratch" volume is actually a 200Gb ephemeral NVMe-backed disk, which only exists for as long as the pod does.
2. We don't actually want to significantly increase our CPU usage across the platform - rather, we want to leverage Tdarr for spare capacity on hardware-based transcoding. Each Tdarr pod has minimal CPU, and enough RAM to run the server, plus one hardware transcode, but will crash and restart if trying to do more than one transcode in parallel (*because mooar transcodes requires mooar RAM*)

I've pre-configured a working Tdarr setup, so you won't be starting from scratch when configuring it, and I've added more specifics to the [app][tdarr] page.

Get your 24h trial / subscription at the [store](https://store.elfhosted.com/product/tdarr/)!

<!-- more -->

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:material-dolphin: Healthy tenant pods | 801
:fontawesome-regular-circle-user: Total subscribers | 42
:fontawesome-solid-hard-drive: Storageboxes mounted | 22
:material-sync: Rclone mounts | 11
:material-bug: Bugz squished | 0
:fontawesome-solid-gamepad: New toyz | 1

### Summary

As always, thanks for building with us - feel free to share suggestions and ideas in [Discord][discord]!

--8<-- "common-links.md"