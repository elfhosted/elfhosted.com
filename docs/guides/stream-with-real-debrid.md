---
title: Stream your media with Real-Debrid and Plex/Jellyfin/Emby
description: This guide describes how to setup your own "Streaming Platform", streaming your media from Real-Debrid, without having to store it locally or use a torrent client.
---

# How to Setup your own Plex Cloud

Once upon a time, Plex provided "Plex Cloud", a partnership with Amazon which would let you run your Plex server "in the cloud", and attach various cloud storage providers for storing your vast media libraries.

The Plex Cloud service was [shut down](https://www.digitaltrends.com/home-theater/plex-cloud-shutting-down/) due to technical / cost issues, but given the popularity of online streaming platforms, a "cloud based" Plex instance is still an attractive solution for many users who don't want to bother with self-hosting their Plex server or their media.

ElfHosted provides all the hosting and options to setup your own hosted Plex instance (*your Plex Cloud*), and stream your media from cloud storage, creating your own "Plex Google Drive", "Plex Onedrive", etc.

## Requirements

* [x] [Radarr][radarr] / [Sonarr][sonarr]
* [x] [Jellyseerr][jellyseerr] / [Overseerr][overseerr]
* [x] [RDTClient][rdtclient]
* [x] [Zurg][zurg]
* [ ] Zurg Rclone Mount
* [x] A [Real-Debrid account](http://real-debrid.com/?id=10184538) and [API token](https://real-debrid.com/apitoken)

## The classic Arr setup

```mermaid
flowchart TD
    B[Manual Request] --> C[Jellyseer]
    A[Add to watchlist] --> C[Overseer/Jellyseer]
    C <--> |Add to Arrs|D[Radarr/Sonarr]
    D <--> |Search for media|E[Prowlarr]
    D <--> |Add to downloader|G[RDTClient]
    E --> |Search trackers|F[Trackers]
    G <--> |Add torrent|H[real-debrid]
    H --> I[Zurg]
    J[rclone mount] --> |WebDAV endpoint|I
    K[Plex/Jellyfin/Emby] --> |Add library|J
    Z[fa:fa-user User] --> K
    Z[fa:fa-user User] --> B
    Z[fa:fa-user User] --> A
```

## Lightweight debrid setup

```mermaid
flowchart TD
    B[Manual Request] --> C[plex_debrid]
    A[Add to watchlist] --> C[plex_debrid]
    C <--> |Add to Arrs|D[Radarr/Sonarr]
    D <--> |Search for media|E[Prowlarr]
    D <--> |Add to downloader|G[RDTClient]
    E --> |Search trackers|F[Trackers]
    G <--> |Add torrent|H[real-debrid]
    H --> I[Zurg]
    J[rclone mount] --> |WebDAV endpoint|I
    K[Plex/Jellyfin/Emby] --> |Add library|J
    Z[fa:fa-user User] --> K
    Z[fa:fa-user User] --> B
    Z[fa:fa-user User] --> A
```

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