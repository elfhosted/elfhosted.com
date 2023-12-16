---
date: 2023-12-16
categories:
  - CHANGELOG
tags:
  - infra
title: Mooar downloaders, better balancing, RIP tmpfs, hello ephemeral volumes!
description: We've added 50% more capacity / bandwidth for download clients, and improved the way /tmp volumes are presented
---
# 50% more download capacity, better (and bigger) /tmp volumes

In a [previous blog post](/blog/2023/11/23/added-third-download-host/), we discussed how we've expanded our node types to provide compute (*CPU, RAM*), storage, and network bandwidth for high-traffic-volume apps (*torrent / NZB clients, data sync tools, etc*) seperately from the resources for general-purpose and streaming apps.

In November, we provisioned 2 "download-class" nodes, but a month later, I've added a third node. This gives us an extra 1Gbps aggregate bandwidth capacity, provides better failover for workloads when doing maintenance, and allows for better automated balancing of workloads across the download-class nodes, since we can calculate a "mean" CPU/RAM/pod usage, and move workloads around accordingly.

<!-- more -->

## Deletion policy documented

I'm putting the finishing touches on the automation which deletes abandoned / unused volumes. 

I've documented [our deletion policy](/how-to/delete-your-data/), but here's a summary:

Action | Data affected | Retention
---------|----------|---------
 :no_entry_sign: Unsubscribe an app | :material-trash-can-outline: Application data | 7 days
 :sleeping: Have no active subscriptions | :material-trash-can-outline: ElfStorage data | 31 days
 :material-nuke: Delete your account | :material-trash-can-outline: Account data<br/>:material-trash-can-outline: Application data<br/>:material-trash-can-outline: ElfStorage data | Immediately

See the [our deletion policy](/how-to/delete-your-data/) for more details!

## New Toyz

### 1TB /tmp volume on downloaders

One advantage of moving the downloaders to dedicated nodes is that I could pick nodes with **much** bigger local disks. As a result, we're able to offer each download client a 1TB ephemeral `/tmp` folder, to facilitate unpacking / processing, before completed files are moved to permanent storage. There are some gotchas (*ephemeral means the data goes away when the pod restarts*), but if you're processing big queues of small(ish) files, an ephemeral `/tmp` can significantly improve efficiency.

The implementation varies slightly between clients, and is documented on each individual app's below:

* [qBittorrent][qbittorrent]
* [Deluge][deluge]
* [SABnzbd][sabnzbd]
* [NZBget][nzbget]
* [ruTorrent][ruTorrent]

Incidentally, you may have noticed before that your `/tmp` folder used to appear much bigger than expected. Technically, this was because the pods were using [emptyDirs](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir), which provide you with (*again, ephemeral*) storage on the node OS. This was useful, but limited in that (a) it would **appear** to your app as if you had access to **all** the storage on the node OS, and (b) if you exceeded the pre-determined emptyDir storage, your pod would be summarily evicted and the data lost.

We're now using [ephemeral volumes](https://kubernetes.io/docs/concepts/storage/ephemeral-volumes/), backed by thin-provisioned[^2] [topolvm](https://github.com/topolvm/topolvm) volumes, which achieves the same goal - making local storage temporarily available for applications for fast, local I/O-heavy tasks. However, using ephemeral volumes means the pod is presented with a volume exactly the right size, and when it fills up, the pod doesn't restart - it just can't write any more data, avoiding nasty surprises for the user.

### Meet Glime, our AI support bot

We're now using an early-stage AI bot ([Glime](https://glimelab.ai/)) which is trained on our docs, and able to answer generic support questions either in Discord or on the website. It can't solve individual account problems for you (*that'll still require waiting for a friendly human*), but it's trained on our our docs and Discord history, and quite helpful with generic questions like "*how do I access my ElfStorage remotely?*", or "*how do I connect Plex to Overseerr?*"

To interact with Glime, just post your question directly to it in Discord, like this

> @Glime, why should I choose ElfHosted instead of a regular seedbox?

You can also interact without Discord, by using the "**Ask AI**" button at the bottom right of the site / store.

## Bugz Squashed 

### Unintentional subscription expiries fixed

Some users recently found their perfectly valid subscriptions prematurely expired. This was due to a bug re the way "24-hour" vs "recurring" subscriptions are processed, a distinction which I'm no longer sure we need. I've fixed up the bug, but I'll be polling #elf-friends to see whether the "24h app" feature is appealing, or confusing.

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers [^1]| 82
:fontawesome-solid-hard-drive: Storageboxes mounted | 23
:material-sync: Rclone mounts | 9
:material-dolphin: Tenant pods | 764
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 2

### Summary

As always, thanks for building with us!

[^1]: Includes users testing the platform with $10 free ElfBuckz
[^2]: So that we can over-provision storage, since 100% of each user's `/tmp` is unlikely to be in use all the time!

--8<-- "common-links.md"