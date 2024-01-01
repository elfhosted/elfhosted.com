---
date: 2024-01-01
categories:
  - CHANGELOG
tags:
  - rdtclient
  - sabnzbd
title: SABnzbd gets persistent /tmp queue, RDTClient gets moooar speed!
description: SABnzbd queues survive restarts now, and RDTClient gets 10Gbit (sort of) throughput
---
# Welcome to 2024! 🎉

In today's blog post, the first of 2024, we discuss:

* How SABnzbd's queue in the 1TB /tmp folder now persists
* How RDTClient gets some VIP network connectivity
* How the volume provisioning bug was **actually** solved

<!-- more -->

## SABnzbd's persistent 1TB /tmp queue

One of the reasons we updated our design to run the downloading tools on their own separate nodes, is that it allows us to provision huge checks of temporary HDD space (*we have 14TB per node*) for ephemeral processes like temporary torrent assembly, NZB unpacking / repair, etc, before content is moved to permanent network storage.

This process saves us tremendously on I/O load, and consequently makes downloads faster.

While this process is opt-in for [qBittorrent][qbittorrent] and [Deluge][deluge], [NZBGet][nzbget] and [SABnzbd][sabnzbd] are already configured to use `/tmp` for temporary storage, so you don't have to do anything to take advantage of this.

However, it turns out that SABnzbd stores its **queue** data in the temporary path, meaning that if the temporary data goes away (for example, when the pod restarts for rebalancing / upgrades), so do all the queued up NZBs! (*NZBGet doesn't do this, it stores the queue data separately from temp files*)

Today I've added, (*and some helpful Elf-a-testers have validated*), [some magic](https://github.com/geek-cookbook/elf-charts/blob/main/charts/other/myprecious/values.yaml#L1590) which will backup and restore the SABnzbd queue data (*but not big, chunky .par files!*) on restart, meaning that SABnzbd users can take advantage of their 1TB `/tmp` volume without loosing in-progress downloads, in the event of a routine restart. [^1]

## RDTClient gets 10Gbps

Here's last month's internet usage in GB, per-host, as reported by Hetzner (*orc03 was a late addition*). Internal traffic (*like network storage I/O*) is excluded:

![](/images/blog/dwarves-vs-orcs-1-jan-2024.png)

??? question "Notice anything interesting?"
    Yes! The dwarves record almost **zero** internet traffic, and there are now **10** of them!

The dwarves are our storage nodes. I recently splashed upgrading us to 10 of them, so that we can use 8+2 erasure coding for more efficient storage using in [ElfStorage][elfstorage].

So we have 10 x nodes, each capable of unlimited internet traffic at 1Gbps, doing zero internet traffic. Of course, the dwarves are not idle, they're providing OSDs for [ElfStorage][elfstorage], but given the physical limitations of HDDs, this only consumes 10-20% of their network capacity. We have 10 of them for redundancy / efficiency, not because the load demands it.

Other than participating in Ceph, the dwarves are not doing much, so I've been looking for opportunities to shift some apps to the dwarves, and utilize their available internet capacity. Specifically, we're looking for apps which would benefit from high throughput, relatively low CPU and RAM, and require no local resources like a GPU or chunky local disks for ephemeral temp storage.

I felt that [RDTClient][rdtclient] would be a good candidate. RDTClient's job is to pull content from Real-Debrid (*and similar services*) down to your local / BYO storage, usually by pretending to be qBittorrent and integrating with [Radarr][radarr] / [Sonarr][sonarr]. I'm working on a more detailed guide, but basically RDTClient lets you grab torrents, without torrenting. This means no VPN requirement, no seeding, uncompressing, ratio, etc, just an HTTPS download directly to your storage.

Soo.. I've switched our RDTClient instances over to the dwarves as an experiment. What I **hope** will happen is that we'll be able to use the the idle part of the 10 x 1Gbps internet connections for downloads from real-debrid, leaving more capacity for the heavyweight downloaders (*torrents and NZBs*) on the dedicated downloading nodes, while having no effect on Ceph[^2].

## What happened to the provisioning bug?

Remember that rook-ceph provisioning bug I was chasing for days? The root cause, it turned out, was that I hadn't adequately opened the firewall on our nodes for the ports necessary for rook-ceph, which allocates ports non-deterministically! 

I've made the [obvious fix](https://github.com/geek-cookbook/elf-infra/blob/main/roles/node/tasks/main.yml#L57), and our provisioning woes are now behind us!

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers [^1]| 128
:fontawesome-solid-hard-drive: Storageboxes mounted | 20
:material-sync: Rclone mounts | 12
:material-dolphin: Tenant pods | 1040
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 2

### Summary

As always, thanks for building with us!

--8<-- "common-links.md"

[^1]: An unexpected failure like a power outage would still result in the loss of ephemeral data, since the data couldn't be backed up on shutdown.
[^2]: If this negatively affects ElfStorage, I'll undo it, and will be keeping a careful eye on performance over the next few days