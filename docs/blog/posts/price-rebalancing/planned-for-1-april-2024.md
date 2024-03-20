---
date: 2024-03-20
categories:
  - price-rebalancing
tags:
  - infrastructure
title: Price rebalancing planned for 1 April 2024
description: We're planning a price rebalancing on 1 April 2024, here's how it works and how it'll impact you
---

# Price rebalancing planned for 1 April 2024

As [previously announced](/open/feb-2024/#regular-pricing-re-balancing-starts-1-april-2024), we're be doing the first of what will become routine price-rebalancing, starting on 1 April 2024. This is the first time we've adjusted prices since we were ["born" in June of 2023](/open/june-2023/), and so this process may be a little jarring / unpolished at first!

!!! question "TL;DR - How will this affect me?"
    There will be **no change** to the price of existing, active subscriptions. New prices will apply to new subscriptions.

    **However**.. where there's a significant difference between existing and new pricing, we **may** reduce resource allocations on existing subscriptions proportionately. (*for example, the existing Plex pricing only covers about 30% of actual expenses*) - I'm seeking community feedback on how to proceed here.

I've laid out our [transparent pricing process and costs in detail](/open/pricing/), and the stated goal is:

> At the highest level, our goal is to **recover hardware costs equivalent to resources consumed, and to realize 20% profit on costs** (*see how we're going on this goal by examining our [monthly reports](/open)!*)

Read below for details on app-specific changes..

<!-- more -->

## Upcoming pricing changes

After reviewing the actual usage data as described [here](/open/pricing/), the following price changes will be effected as of April 1 2024:

App | Current Price | New Price
---------|----------|----------
["Exposed" apps](https://store.elfhosted.com/product-category/advanced) | \$0.05 | **FREE**
[Custom domains](https://store.elfhosted.com/product-category/custom-domains) | \$0.05 | **FREE**
[ElfStorage][elfstorage] (*per TB*)    | \$0.20 | \$0.10
Remote debrid mounts ([Zurg][zurg], AllDebrid, PutIO, etc)    | \$0.05 | \$0.20
[Plex][plex]    | \$0.15 | \$0.50
[Jellyfin][jellyfin]    | \$0.15 | \$0.50
[Emby][emby]    | \$0.15 | \$0.50
[Radarr][radarr]    | \$0.05 | \$0.20
[Sonarr][sonarr]    | \$0.05 | \$0.20
[qBittorrent][qbittorrent]    | \$0.15 | \$0.30
[Deluge][deluge]    | \$0.15 | \$0.30
[ruTorrent][rutorrent]    | \$0.15 | \$0.30
[SABnzbd][sabnzbd]    | \$0.15 | \$0.30
[NZBGet][nzbget]    | \$0.15 | \$0.30
Other $0.05 apps    | \$0.05 | \$0.10

!!! question "Why the massive jump in streamers / Aars?"
    When the current pricing was set in June 2023, we didn't have "[infinite streaming](/guides/media/)" from debrid providers with symlinks, and so it was a "simpler time"..
    
    With the current symlink design, it's possible to import huge libraries (*upwards of 50TB!*) within a few hours, which has a significant resource implication, especially for storage I/O related to metadata and databases!

There's an obvious trend here - when users have the choice, local storage and "traditional" seedboxing are "fading away" :t_rex:, and the debrid-based "infinite streaming" options are becoming more popular.

The other obvious trend is that everything except ElfStorage has become at least 100% more expensive! :scream: The primary reason for this has to do with cluster overheads - there's a minimum amount of overhead required to maintain a stable and secure cluster, so even apps with a very small footprint (*such as [PrivateBin][privatebin]*) incur some measure of cluster / management overhead.

## Plex_debrid refreshed (in beta)

Our xterm-in-VNC-in-a-browser [plex_debrid][plex-debrid] implementation works, but it's a PITA, and creates a disproportionate amount of support requests. I've refactored the app into a terminal-in-a-browser (*can't escape the fact that it's an interactive CLI UI!*), which is much quicker to manage, and responds better to copy/paste.

I'm also working on an improved bootstrapping process, by providing a pre-configured `settings.json`, and walking the user through making the minimum required changes (*usually a Plex token and a RealDebrid API key*). Since it's **still** a bit of a nuisance to get your head around, I've also got grand designs (*which may not materialize!*) on creating a basic video HOWTO of the whole "infinite streaming" setup. (If you've got experience / interest in the area of screencasts / video, LMK!)

Here's what the refreshed plex_debrid looks like:

![](/images/plex_debrid_in_browser.png)

Currently the updated plex_debrid is available to beta-testers, and will roll out to the stable channel after the pricing changes kick in on 1 April (*don't want to attract a bunch more users just to "bait-and-switch" them with a price rebalance!*)

## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 388 | +4
:alien: Zurg mounts: | 152 | +14
:floppy_disk: ElfStorage in TBs | 82 | +5
:material-dolphin: Tenant pods | 4721 | +614
:superhero: Elf-vengers | 4 | -
:student: Trainees | 2 | -
:material-bug: Bugz squished | - | -
:fontawesome-solid-gamepad: New toyz | - | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"