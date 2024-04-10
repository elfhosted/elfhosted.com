---
date: 2024-04-10
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Stremio Simultaneous Streams are Stupendous
description: with the introduction of Stremio Server / Web, it's now possible (under certain conditions) to stream from Real-Debrid via Stremio, from multiple remote IPs, simultaneously!
---

# Stremio Simultaneous Streams are Stupendous

Now that the [April 2024 repricing](/blog/2024/03/20/planned-for-1-april-2024/) is behind us, and the dust has settled, we can continue working on the ongoing tension of features and stability!

Today's headline update is [Stremio Server][stremio-server] - an instance of the official Stremio server/transcoder, which you can leverage to:

1. Safely stream direct torrents (*not **necessarily** Debrid, see below*) without worrying about a VPN
2. Simultaneously stream Debrid downloads from supported clients (*currently just https://web.strem.io or our hosted [Stremio Web][stremio-web] instance*)

For more details, see the [step-by-step guide to simultaneous Stremio streaming](/guides/media/stream-from-real-debrid-with-stremio-from-with-multiple-ip-addresses-simultaneously/)!

Read on for more developments, features, and bugfixes!

<!-- more -->

## Public cluster dashboard

We've had a public Grafana dashboard showcasing [high-level ElfHosted cluster metrics](https://fnky.nz/grafana-elfhosted) for a month or two, but at \@pomnz's suggestion, it's now included on your ElfHosted dashboard, in the "Tools" tab.

## We have a subreddit! :fontawesome-brands-reddit-alien:

Thanks to the work of \@LayeZee, [r/ElfHosted](https://reddit.com/r/elfhosted ) is a thing! If you're a Reddit user, join our little community - I'll post blog/disclosure updates to the subreddit, and community requests, posts, and general chatter are welcome!

[Join r/ElfHosted! :fontawesome-brands-reddit-alien:](https://reddit.com/r/ElfHosted){ .md-button .md-button--primary }

## Downloaders are now on 10Gbps nodes

In an attempt to reserve more bandwidth on our 1Gbps nodes for streamers, I've moved the torrent clients and WebDAV to our 10Gbps nodes. This means they have more "room to run" (*they're still subject to a 150Mbps egress limit*), but usage over 20TB/month is going to cost me €1/month, so I may need to revert this if things get crazy! (*or, offer a higher-priced "plus" torrenting product to cover the usage!*)

You'll hopefully see the impact of the migration in the aforementioned cluster dashboard - we want to avoid seeing any of the 1Gbps nodes hitting their physical NIC throughput limits (*of 1Gbps*).

## Plex Meta Manager gets 10x storage

Some [Plex Meta Manager (PMM)][plex-meta-manager] users were running into issues with our default 1Gb storage assigned to PMM. Since overlay images on a tool which runs once a day don't exactly need to be super-performant, I've migrated this storage to our HDD-based pool, and increased it to 10Gb, for 10x the fancy movie-poster storage love!

## TheLounge logs get the 10x treatment

Speaking of increasing things 10x by moving them to cheap (slow) storage, I've done the same with TheLounge's `/config` volume, which grows as you participate in IRC channels with logging enabled. This should have happened transparently, and since it's just static data, I don't anticipate a performance impact.

## Bugfixes

### Trial subscription fixes

In a carryover from how daily subscriptions **used** to work, some trial subscriptions were being terminated early, and others were living on beyond their expiry date, depending on conditions. This **should** now be solved, but if you notice any subscription-related issues, please create an #elf-help ticket, and I'll get right onto it!

### KnightCrawler / TorrentIO migration underway

There's a new KnightCrawler (*originally a fork of TorrentIO*) parser, much faster and more accurate, and hopefully up to the task of improving search results and filtering out any porn (*any instances we've noticed have been scraped from DMM and mis-matched by the older parser*).

I'm building the public ElfHosted instance of the new Knightcrawler "from scratch", to be sure that all the scraped torrents are clean - there's a dashboard at https://fnky.nz/grafana-knightcrawler where you can track the ingestion progress of the new instance.

The scraping isn't quite done yet, and I prematurely rolled out the new addon code, resulting in a situation where your hosted Knightcrawlers weren't returning (enough) results. In an attempt to roll back, I didn't roll the code far back **enough**, and created a situation where the hosted addon (*per tenant*) was crashing and erroring, and using all its available CPU (*limited to 2 vCPU*).

Here's a [visual representation](https://static.funkypenguin.co.nz/2023/ElfHosted_Cluster_-_Dashboards_-_Grafana_2024-04-11_01-36-36.png) of how badly this went:

(*Yes, normal tenant load is about 12, we hit a peak of 175, or ~15x normal*)

I've rolled us back **properly** now, and when the ingestion is finally finished (in the next few days), I'll roll us forward again.

## Coming Soon

### TRaSH Guides

\@LayeZee has been helping users implement TRaSH Guides custom formats to optimize their media selection for streaming (*without transcoding*). We added [Recyclarr][recyclarr], but it's still a tedious process to build a config file. \@LayeZee has been working on a ELI5 guide on the process of manually setting up formats, and \@pomnz has suggested we pre-configure the Aars with all the custom formats etc, to make new user setup easier.

Watch this space, and shout out if you have experience with the TRaSH setups and how best to implement / maintain them.

## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 378 | -10
:alien: Zurg mounts: | 158 | +6
:floppy_disk: ElfStorage in TBs | 90 | +8
:material-dolphin: Tenant pods | 4010 | - [^1]
:superhero: Elf-vengers | 4 | -
:student: Trainees | 2 | -
:material-bug: Bugz squished | 2 | -
:fontawesome-solid-gamepad: New toyz | 3 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"

[^1]: Delta on tenant pods is meaningless in this report, since we dropped 500+ pods when we made rclone UI/FM opt-in