---
date: 2024-04-23
categories:
  - CHANGELOG
tags:
  - infrastructure
title: KnightCrawler v2 brings filename improvements
description: Since switching to the latest KnightCrawler a few days ago, we've had issues with the Prowlarr indexer (mostly TV shows). There's an upstream PR waiting merging, but we're already on the latest version, so your internal indexer should be happy again!
image: docs/images/knightcrawler-stremio-results-yeah.png
---

# KnightCrawler updated to v2, filename results fixed

The first [ElfHosted Stremio Addon](/stremio-addons/) was a hacky, untested build of [iPromKnight's monster rewrite](https://github.com/knightcrawler-stremio/knightcrawler/releases/tag/v1.0.1) of the backend components of the original torrentio open-source code.

It served us well from [Feb 2024](/blog/2024/02/04/post-stremio-stress/), and was my introduction to the wider StremioAddons community, but the rapid pace of the [KnightCrawler devs](https://github.com/knightcrawler-stremio/knightcrawler/) outpaced our build, and so while fresh builds were prancing around with [fancy parsers and speedy Redis caches](https://github.com/knightcrawler-stremio/knightcrawler/releases/tag/v2.0.0), we ended up with a monster MongoDB instance :pig: (*shared by the consumers, and public/private addon instances*), which would occasionally eat more than its allocated 4 vCPUs and get into a bad state!

To migrate our hosted instance to the v2 code, we ran a parallel build, imported the 2M torrents we'd scraped/ingested, and re-ran these through KnightCrawler's v2 parsing/ingestion process. Look at how happliy our v2 instance is [purring along](https://fnky.nz/grafana-knightcrawler) :tiger: now!

We cut over to the v2 code a few days ago, and since then we've had some users of the [Prowlarr indexer](https://github.com/geek-cookbook/elfhosted-prowlarr-indexers) pointing out that the results coming back from the KnightCrawler indexer were... 

<!-- more -->

meh.

![](/images/knightcrawler-indexer-results-meh.png)

Also, the results of the addon in Stremio client itself were a bit too.. minimal - it wasn't possible to see the video/audio codec, for example:

![](/images/knightcrawler-stremio-results-meh.png)

This was a carry-over from the original addon code, and the fancy parsing that v2 does inadvertently truncated the results, such that they weren't as useful anymore. There's an [upstream PR](https://github.com/knightcrawler-stremio/knightcrawler/pull/210) which fixes this, and the public instance is already updated.

Now *(my preference, anyway*) the search results are more detailed and useful:

![](/images/knightcrawler-stremio-results-yeah.png)

And the [Prowlarr indexer](https://github.com/geek-cookbook/elfhosted-prowlarr-indexers) is returning useful results again:

![](/images/knightcrawler-indexer-results-yeah.png)

## Bugfixes

### RealDebrid blocks Hetzner IP(v4) ranges

Just in time for some weekend streaming, Real Debrid performed some maintenance, and [prevented download/streaming to non-residential addresses](https://www.reddit.com/r/debridmediamanager/comments/1c7ujhj/observation_realdebrid_has_imposed_new_limits_on/). At the time, this included our Hetzner ranges, as well as popular VPN providers (i.e., PrivateInternetAccess).

To reduce the impact on users, we quickly (*and without much testing!*) turned on IPv6 addressing in our cluster, and configured Zurg to force an IPv6 connection to Real-Debrid. For now, this has restored service - there are some reports of the original issue being resolved, but testing from our Hetzner ranges shows that IPv4 is still blocked.

So, now we have an IPv6 cluster, and all the fun that comes with it...

### IPv6 breaks networking

Shortly after the IPv6 enablement, we started to see sporadic issues with our apps. It turned out that when enabling IPv6, we triggered a [bug in Cilium](https://github.com/cilium/cilium/issues/17870) (*our CNI*) which started allocating duplicate IP ranges to our pods, and generally causing havoc.

After trying various "soft" strategies to fix this, the solution ended up being manually updating the PodCIDR ranges on half of our nodes, which has restored us to the stablity we've been enjoying today!

## Coming Soon

### TRaSH Guides

!!! tip 
    Yes, this is still coming, it's just been delayed by IPv6 and related drama!

\@LayeZee has been helping users implement TRaSH Guides custom formats to optimize their media selection for streaming (*without transcoding*). We added [Recyclarr][recyclarr], but it's still a tedious process to build a config file. \@LayeZee has been working on a ELI5 guide on the process of manually setting up formats, and \@pomnz has suggested we pre-configure the Aars with all the custom formats etc, to make new user setup easier.

Watch this space, and shout out if you have experience with the TRaSH setups and how best to implement / maintain them.

(*This weekend's project!*)

## Today's scoreboard

(*The negative trends look bad, but they're likely a response to the [April 2024 repricing](/blog/2024/03/20/planned-for-1-april-2024/), rather than a disinterest / negative reflection on our platform*)

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 346 | -18
👾 Zurg mounts: | 152 | -3
💾 [ElfStorage](https://elfhosted.com/what-is/elfstorage/) in TBs | 88 | +1
🐬 Tenant pods | 3808 | -41
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 4 | -
🧑‍🎓 Trainees | 2 | -
🐛 Bugz squished | 1 | -
🕹️ New toyz | 1 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"

