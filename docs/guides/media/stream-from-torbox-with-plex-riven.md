---
title: Optimal streaming from TorBox with Plex and Riven
description: This guide describes how to use newcomer "Riven" to replace plex_debrid or the Aars as an all-in-one solution for managing your TorBox media collection
---
# Optimal "Infinite streaming" from TorBox with Plex and Riven

This page describes a minimal solution to create the optimal "infinite" Plex library, utilizing [Real-Debrid][real-debrid] for all media, streaming through your ElfHosted [Plex][plex] instance.

The advantages of this solution are:

* No torrent clients, VPNs, ratios or seeding
* No storage constraints, unpacking issues, migrations etc

The disadvantages, of course, are:

* Limited retention - you've only "got" the content as long as your TorBox subscription is current

## Requirements

!!! tip "Riven gets revenue sharing! :heart:"
    Riven is an "Elf-illiated" app - the devs are active in our [Discord][discord] community, the app itself is tuned to work perfectly with ElfHosted "out-of-the-box", and 30% of your subscriptions are contributed to the Riven devs to further development!

* [x] [TorBox account][torbox] and [API token](https://torbox.app/settings)
* [x] ElfHosted's TorBox [Infinite Plex / Riven Streaming Starter Kit](https://store.elfhosted.com/product/starter-plex-torbox-riven/)
* [ ] [Overseer](https://store.elfhosted.com/product/overseerr) (*can be substituted with Plex Watchlist/Trakt/MBDLists*)

## How does it work?

Here's a diagram, followed by some explanations:

```mermaid
flowchart TD
    K[Plex] --> |Stream|Z[User]
    Z[User] --> |Add to watchlist|K[Plex]
    Z[User] --> |Make requests|O[Overseerr]    
    O[Overseerr] -->|Webhook|G[Riven]
    L["Lists (MDBList, Trackt)"] -->|Poll|G[Riven]    
    K[Plex] --> |Watchlist|G[Riven]
    G[Riven] --> |Scan on download|K[Plex]
    G[Riven] --> |Scan for content|F["Torrentio, KnightCrawler, Mediafusion, etc"]
    G[Riven] <--> |Add to library|H[torbox]
    H --> I[Zurg]
    I --> |/storage/symlink/...|J[rclone mount]
    K[Plex] <--> |Library|J
```

1. The user adds content to their [Plex][plex] Watchlist, Overseerr, or subscribes to Trakt/MDBLists
2. [Riven][riven] notices the change to the watchlist, searches various indexers for suitable cached torrents on [TorBox][torbox], triggers a download. When Riven notices the download, it creates a symlink, and tells Plex to rescan the appropriate Library
3. The rclone mount make it appear that the TorBox account is locally mounted to Plex
4. Plex detects the new content, adds it to the library, and it's ready to stream!

## How to set up Riven

Review the [Riven docs][riven] for the next steps!

!!! warning "Beware Real-Debrid IP bans"
    Be aware that Real-Debrid states:
    
    > You can use your account from any public IP address but you can't use your account from more than one public IP address at the same time.

    So if you use RealDebrid **outside** of ElfHosted, it's likely that your account may be warned / banned.

## How do I get help?

1. For general use of the [individual tools](/apps/), refer to the each app's upstream site
2. For specific support re your ElfHosted configuration / account, see the [ElfHosted support options](/get-help/

--8<-- "common-links.md"

{% include 'testimonials.md' %}