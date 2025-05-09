---
date: 2024-04-25
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Plex Performance Problems Pulverized
description: Suspending scheduled schenanigans speeds up streaming!
image: docs/images/plex_scheduled_tasks_impact-2.png
---

# Plex Performance Problems Pulverized

Since we published the [ElfHosted Cluster Grafana Dashboard](https://fnky.nz/grafana-elfhosted), it's become apparent that **something** is happening on a daily basis which generates significant traffic on the 10Gbps "giant" nodes, and fully saturates the network interfaces on several 1Gbps "elf" nodes.

Here's a 2-day graph:

![](/images/plex_scheduled_tasks_impact_1.png)

Here's a closer look at that spike...

<!-- more -->

![](/images/plex_scheduled_tasks_impact_2.png)

What's interesting is that we're seeing 1Gbps traffic **ingressing** several elves, but absolutely no corresponding increase in traffic **egressing** the elves.

So where's the traffic going?

Some poking around with `jnettop` revealed that the majority of the traffic on the busiest elf was arriving from port `445` from a Hetzner IPv6 address which wasn't one of ours.. it belongs to a user's storagebox instance!

So during this period (***exactly** the same time every day*), we see 600-700% (6-7Gbps) extra traffic from RealDebrid (*via the giants*), **plus** several extra Gbps traffic from storageboxes, towards the elves, with none of it leaving again.

## The Culprit

It turns out the culprit was Plex's scheduled tasks, which analyze your media to identify intros and credits (*for skipping*), and generate chapter thumbnails. In one case, Plex was pulling an entire HEVC 4K copy of LOTR from a storagebox, just to transcode it to extract jpgs for chapter thumbnails! This explains why the data wasn't **going** anywhere!

Needless to say, we don't want to waste precious bandwidth / resources on thumbnailing / analysing "infinite" Plex libraries, so tonight's update includes a fix to turn these scheduled tasks off. This should reduce both the bandwidth and CPU load on the platform, and allow more users to stream without congestion.

While identifying the media analysis issue, we've also tightened up the [transcode-killer script](https://github.com/funkypenguin/elf-infra/blob/main/roles/node/files/kill-unwanted-transcodes.sh), to more widely prevent unnecessary and resource-intensive (HEVC) transcodes.

!!! tip "Avoid transcodes with TRaSH custom formats"
    With the help of several elves, we're continuing to improve implementation of the TRaSH guides custom formats, so that users are able to download the optimal qualities / formats to stream to their devices in original quality, without incurring transcoding overheads.

## Bugfixes

### Plex_debrid now starts automatically

Since we refactored plex_debrid away from that nasty VNC-in-a-browser UI, it's been (unintentionally) necessary to hit `<ENTER>` in the plex_debrid UI to actually start the app, even if you've (sensibly) configured it to run on startup.

Yesterday's update broke this, but tonight's update fixes it properly, and now plex_debrid will start up "without you" - you'll still need to hit `<ENTER>` the first time, to engage the web UI, but plex_debrid itself will already be running in the background.

!!! tip
    Configure plex_debrid **not** to show the menu by default on startup, so that it'll just start searching/downloading immediately upon start.

### Cached old KnightCrawler results cleaned

Even after the recent update to fix the way filenames are returned from a KnightCrawler search, some users were still seeing back / incomplete search results. It turns out that these were added to our central KnightCrawler cache by no-yet-updated private instances.

This has been addressed during the latest maintenance, and the invalid results cleared from the cache, so our Prowlarr indexers should behave as expected again.

## Coming Soon

### TRaSH Guides

!!! tip 
    Yes, this is still coming, it's just been delayed by IPv6 and related drama!

\@LayeZee has been helping users implement TRaSH Guides custom formats to optimize their media selection for streaming (*without transcoding*). We added [Recyclarr][recyclarr], but it's still a tedious process to build a config file. \@LayeZee has been working on a ELI5 guide on the process of manually setting up formats, and \@pomnz has suggested we pre-configure the Aars with all the custom formats etc, to make new user setup easier.

Watch this space, and shout out if you have experience with the TRaSH setups and how best to implement / maintain them.

(*This weekend's project!*)

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"

[^1]: A process which cleaned up stale volumes was stalled. It's working again, which is why this number dropped so suddenly (*i.e, it's now accurate*)
