---
date: 2024-05-21
categories:
  - infra
tags:
  - elfbot
title: Jellyfin / Emby transcoding fixes, force-killing outlawed, subscription bugs fixed
description: We've made a few fixes to the new subscription processing process (a pending-cancel service is still an active service), found and fixed an Emby/Jellyfin transcoding issue, and locked out force-restarts of pods for now
---

# Emby / Jellyfin transcode fixes

The recent transcode path fixes to [Jellyfin][Jellyfin] / [Emby][Emby] have brought a small bug out of the woodwork.. in some cases, the streamers may insist on transcoding your media based on your perceived bandwidth limits, and then fail to transcode because (a) it's 4K content, or (b) the transcoding path is not set to `/transcode`, and we've prevented use of the network storage for such!

A simple workaround is to edit your Jellyfin / Emby users, and to remove their permissions to perform video transcodes, something like this:

![](/images/emby-prevent-user-from-transcoding.png)

Read on for more fixes...

<!-- more -->

## Subscription bugfixes

So far we've found one bug with the subscription process improvements announced yesterday - if you had subscription pending cancellation (*maybe you canceled a monthly subscription after a few days because you don't want to renew it*), the system would deactivate your subscription **immediately**.

We'll now "hang on to" cancelled subscriptions until they age out - this could still cause a little bit of a nuisance if you cancel and resubscribe to the same app on a daily subscription, for example to fix your VPN configuration. In this case, the old "pending" and new "active" subscriptions would clash, and the config may get muddled.

If you're on a prepaid subscription though, you do have the option to either "cancel" (immediate), or "cancel when prepaid period ends" (pending).

If you're unlucky enough to stumble into this edge case, drop us an [#elf-help][elf-help] ticket, and we'll sort it manually for you.

## Force kills suspended

In March/April, when we were dealing with Ceph instability, we implemented "force" app restarts, which would restart your apps without waiting for the storage to disconnect (*typically [Plex][Plex] and the Aars were culprits*). Now that storage is purring like a happy, well-fed cat, there's hardly ever a legitimate need to force-kill a pod.

Since we made much of the storage single-attachable (*ReadWriteOnce*) as well, (*to avoid the I/O congestion which caused the instability in the first place*), force-killing pods generally makes their replacements unhappier, as they can sit and wait forever for the previous pod's storage volumes to "detach".

So I've turned off force-killing for now - if you find yourself needing to force-delete a pod, please create an [#elf-help][elf-help] ticket, and we'll try to address the underlying problem instead :)

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 341 | +5
👾 Zurg mounts: | 116 | +2
💾 [ElfStorage](https://elfhosted.com/what-is/elfstorage/) in TBs | 93 | -
🐬 Tenant pods | 2990 | +77
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 8 | -
🧑‍🎓 Trainees | 22 | -
🐛 Bugz squished | 2 | -
🕹️ New toyz | 0 | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"
