---
date: 2024-05-10
categories:
  - new-app
tags:
  - airdcpp
title: Introducing AirDC++ (Web Client), share files like it's the 90s!
description: We welcome AirDC++ (Web Client) to our catalogue! With AirDC++, you can share your libraries with "hubs" of like-minded users, exchanging files and messages, secured with a BYO VPN
image: docs/images/screenshots/airdc++.png
---

# Introducing AirDC++

After some careful user testing (*thanks \@lath!*), [AirDC++][airdcpp] is generally available!

AirDC++ (Web Client) is a modern client for the "[Advanced Direct Connect Protocol](https://en.wikipedia.org/wiki/Direct_Connect_(protocol))", a protocol with a 25-year backstory, which allows creating file sharing communities with thousands of users. Among other things, AirDC++ is popular with comic-book-sharing communities.

![](/images/screenshots/airdc++.png)

More details on the [AirDC++ App page][airdcpp]!

<!-- more -->

## New Features

### \@Layezee's TRaSH Guides

Thanks to \@LayeZee, we now have dedicated guides to configuring Radarr / Sonarr with the TRaSH guides custom formats, for 1080P content.

For details, see:

* [Optimizing your movie quality with TRaSH Guides custom formats](/guides/media/optimize-movie-quality-with-trash-custom-formats/)
* [Optimizing your series quality with TRaSH Guides custom formats](/guides/media/optimize-series-quality-with-trash-custom-formats/)

### ElfBot talks TRaSH

Don't fancy copying/pasting all that JSON, but still want to take advantage of the TRaSH magic to grab optimal content with your Aaars?

[ElfBot][elfbot] has [Recyclarr][recyclarr] built-in now, so you can get 98% of the way there by just running `elfbot recyclarr sync` :thumbsup:

### Jellyfin bumped to 3Gi RAM limit

We've started to see the occasional Jellyfin pod get OOMKilled due to reaching its 2Gi RAM limit (*during analysis*). The RAM limit for Jellyfin has been bumped up to 3Gi 🎉

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"
