---
date: 2023-09-15
categories:
  - store
tags:
  - plex
title: Bypassing Plex's Hetzner block with VPN
description: When Plex starts blocking Hetzner IPs, we'll need BYO VPN to keep using Plex
---
# What will we do about Plex blocking Hetzner IPs?

Plex recently sent [notices](https://torrentfreak.com/plex-will-block-media-servers-at-prevalent-hosting-company-230915/) to users hosted on Hetzner IP ranges, indicating that from 12 Oct 2023, their hosting provider will be blocked.

Although the letter didn't mention Hetzner by name, it's pretty clear that they're the target, presumably due to their affordable (*woo!*) pricing, and the prevalence of "Plex Shares" services using it.

This presents an issue for ElfHosted, since we're using Hetzner for the same reasons (*the price is nice*).

Luckily (*ironically*) due to Hetzner's infamous zero tolerance of DMCA notices, we've already built out the infrastructure to add VPNs to pods, and allow users to "BYO VPN". This is how our torrent clients work - you've got to bring your own VPN credentials to play.

So, come 12 Oct, when Plex blocks Hetzner's IP ranges, it **may** be necessary to BYO VPN in order to keep using your Plex instance.

Worst-case, if you're a Plex user who wants to continue beyond 12 Oct, you'll want to cancel your Plex subscription, and add one of the [Plex BYO VPN alternatives from the store](https://store.elfhosted.com/product/plex/).

Of course, the other solution would be (*like half of r/selfhosted currently*), to loudly bemoan Plex's behaviour, and rage-switch to [Jellyfin][jellyfin] or [Emby][emby] ;)

<!-- more -->

## Mattermost users get 9.0 upgrade

[Mattermost][mattermost] users, rejoice! Tonight's maintenance window will bump you to the [new version 9.0](https://mattermost.com/blog/mattermost-v9-0-is-now-available/), just released!

### Summary

As always, thanks for building with us!

--8<-- "common-links.md"