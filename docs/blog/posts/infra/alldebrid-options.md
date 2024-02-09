---
date: 2024-02-09
categories:
  - CHANGELOG
tags:
  - infrastructure
title: AllDebrid options, KnightScraper / Torrentio stabilty, and Prowlarr indexer fixes
description: We've now got AllDebrid-friendly options for RDTClient and Torrentio / Knightcrawler, and season packs are working in Sonarr!
---

# AllDebrid Alternatives Available

It's been a week since we announced our [free public torrentio alternative](https://torrentio.elfhosted.com) (*with [paid private instances](https://store.elfhosted.com/product/knightcrawler/)*), and it's been exciting (*and at times, overwhelming!*) to welcome a flock of enthusiastic new elves to the platform.

The influx of users has brought some edge-cases / bugs to the fore, which I'll detail below..

<!-- more -->

## Solved Sonarr Season Searching

Our [Prowlarr torrentio indexer](https://github.com/geek-cookbook/elfhosted-prowlarr-indexers/tree/main/Custom), which is bundled into every Prowlarr installation, included a penguin-introduced-bug, preventing the searching for entire seasons from [Sonarr][sonarr]. Searches could still be performed, but only episode-at-a-time.

Thanks to some help from the [Ragnarock Discord](https://discord.gg/wDgVdH8vNM), this is now fixed, and season searches work again!

## Arr-SS (RSS) searching solved too

The Aars may complain that our Prowalarr indexer is not RSS-compatible. This is true, which means that Sonarr won't auto-detect new episodes, without a manual search being performed. Fortunately, there's a [path forward here](https://github.com/Pukabyte/scannarr), which we should able to bake into our image and have "just work"!

## AllDebrid Altervatives Available

Unlike Real-Debrid, AllDebrid doesn't permit its API to be used from a "datacenter". This means that torrentio / Knightcrawler, and RDTClient, weren't able to interact with AllDebrid. I've created AllDebrid-specific instances of [Knightcrawler](https://store.elfhosted.com/product/knightcrawler-vpn) and [RDTClient](https://store.elfhosted.com/product/rdtclient-alldebrid), which are routed via a PIA VPN, to deal with this.


## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 251 | +22
:fontawesome-solid-hard-drive: Storageboxes mounted | 18 | -
:alien: Zurg mounts: | 106 | -
:floppy_disk: ElfStorage in TBs | 53 | +1
:material-dolphin: Tenant pods | 3440 | +406 [^1]
:superhero: Elf-vengers | 3 | -
:student: Trainees | 2 | -
:material-bug: Bugz squished | 3 | -
:fontawesome-solid-gamepad: New toyz | 1 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"

[^1]: Includes 2 x 26 new sharded flux pods!