---
title: Setup your own Plex Cloud
description: This guide describes how to setup your own "Plex Cloud", streaming your media from cloud storage like Google Drive, OneDrive, Hetzner Storageboxes, etc.
---

# How to Setup your own Plex Cloud

Once upon a time, Plex provided "Plex Cloud", a partnership with Amazon which would let you run your Plex server "in the cloud", and attach various cloud storage providers for storing your vast media libraries.

The Plex Cloud service was [shut down](https://www.digitaltrends.com/home-theater/plex-cloud-shutting-down/) due to technical / cost issues, but given the popularity of online streaming platforms, a "cloud based" Plex instance is still an attractive solution for many users who don't want to bother with self-hosting their Plex server or their media.

ElfHosted provides all the hosting and options to setup your own hosted Plex instance (*your Plex Cloud*), and stream your media from cloud storage, creating your own "Plex Google Drive", "Plex Onedrive", etc.

## Requirements

* [x] A VPN provider (*since Plex blocked all of Hetzner in Oct 2023 due to abuse*). [Private Internet Access](https://www.privateinternetaccess.com/pages/buy-a-vpn/1218buyavpn?invite=U2FsdGVkX18CE8WQvq-yt5OJ9UFpALCzci2Oz_px1uA%2CGuAfcPbAeh-UmP4KJ2uroADgSdY) (*referral link*) often has deals for as low as $2/month.
* [x] Existing cloud storage (*Google Drive, or anything rclone-compatible*), or a cheap [Hetzner Storagebox][storagebox].
* [x] Optionally, a PlexPass account, which will let you take advantage of hardware transcoding if you're unable to DirectPlay your media.

## Setup Plex Cloud

### Create account, get $10 free credit

[Sign up for an account](https://store.elfhosted.com/my-account/), and confirm your $10 [ElfBuckz][elfbuckz] (*store credit*) balance.

### Add Plex with VPN

[Subscribe][store/plex] to Plex using your chosen VPN provider, and claim your new [Plex][plex] instance using [ElfBot][elfbot].

Your Plex Cloud URL will be `https://<your username>-plex.elfhosted.com`.

### Attach cloud storage to Plex

You get 100GB free "[ElfStorage][elfstorage]", but this won't be enough for any sort of media collection (*other than perhaps [books][calibre-web]!*) Pick one (*or more*) of the options below:

1. Add more [ElfStorage][elfstorage] at $0.20/TB/day (*so $6/TB*)
2. [Buy a storagebox][storagebox] from Hetzner (*sized at 1TB, 5TB, 10TB, and 20TB*)
3. [Mount][store/storage] your existing (*rclone-compatible*) cloud storage

### Populate your Plex Cloud

If you're using ElfStorage or a Storagebox, import any media you'd like per the [migration instructions](/how-to/migrate/).

If you're attaching existing cloud storage, setup your Plex libraries to point to the correct location in `/storage/`.

### Enjoy your own Plex Cloud!

That's it! Enjoy using your new Plex Cloud to stream your media to yourself and your friends and family, without the hassle of local hosting or storage management!

## Why not just self-host Plex?

[Self-hosting](https://reddit.com/r/selfhosted) is a fun and rewarding way to have complete control over your applications and content. If you're into self-hosting, check out [Funky Penguin's Geek Cookbook](https://geek-cookbook.funkypenguin.co.nz), specifically the [Plex](https://geek-cookbook.funkypenguin.co.nz/recipes/plex/) stack.

Reasons **not** to self-host Plex may include:

* [x] You want to avoid the hardware / power costs involved
* [x] You want more reliability / uptime for your Plex server, while your self-hosting / homelab is for tinkering
* [x] You want media streaming to **just work** (*we manage app updates, hardware, connectivity, security, etc.*)

## What now?

That's it, you're done. Hope into our [friendly Discord server][discord] if you have questions or suggestions!

--8<-- "common-links.md"