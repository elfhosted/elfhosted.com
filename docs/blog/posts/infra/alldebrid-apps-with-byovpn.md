---
date: 2024-02-14
categories:
  - CHANGELOG
tags:
  - infrastructure
title: AllDebrid 100% supported (with BYO VPN)
description: Are you an AllDebrid user? You can now get the same level of support as Real-Debrid (rclone mounts, KnightCrawler, and RDTClient), with one exception - you'll need to BYO VPN. Here's the details..
---

# AllDebrid 100% supported (if you BYO VPN)

We've had AllDebrid support for our debrid-related apps in testing for a few days, and our elf-a-testers have confirmed it's good to go (*thanks elf-a-testers!*).

The trick with AllDebrid, it turns out, is that they don't allow use of their API or WebDAV endpoints from "datacenter IPs", which includes our Hetzner IP ranges. (*Confusingly, they allow **listing** of WebDAV files from anywhere, but not actual **downloading**!*).

**However**, **if** you configured your AllDebrid account to specify that you're using a VPN, then you **can** access their endpoints via that VPN provider. Soo.. the workaround to using AllDebrid with ElfHosted apps is to... BYO VPN credentials (*like we do with our torrent clients*).

Currently this is just working with PrivateInternetAccess (PIA), but we can easily add more VPN flavors in future (*let me know if you need one ASAP*)

Here are the AllDebrid / VPN-enhanced versions of our regular debrid apps...

<!-- more -->

* [RDTClient (VPN)](https://store.elfhosted.com/product/rdtclient-vpn-pia)
* [Rclone Mount (AllDebrid)](https://store.elfhosted.com/product/rclone-alldebrid-pia)
* [KnightCrawler (VPN)](https://store.elfhosted.com/product/knightcrawler-vpn)
* [Advanced Plex Infinite Streaming Bundle (AllDebrid)](https://store.elfhosted.com/product/advanced-infinite-arr-plex-alldebrid-streaming-bundle)

## Komga OPDS server fixed

[Komga][komga] suffered from the same 401-pretty-error issue which affected Calibre-Web (*OPDS wasn't prompting for auth*) - this is now fixed!

## Annatar is coming..

Yesterday another self-hosted Stremio addon (*torrentio replacement*) was [announced](https://www.reddit.com/r/StremioAddons/comments/1apghdn/annatar_the_fastest_selfhosted_justintime/) - we've offered to host a free public instance, hopefully with some snazzy public Grafana graphs to geek out over the speed / usage over time. 

Watch this space!

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"