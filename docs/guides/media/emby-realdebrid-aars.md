---
title: Stream from Real-Debrid with Emby and Radarr, Sonarr, Prowlarr
description: This guide describes how to setup a torrent-like "arr stack", to achieve "stremio-like", streaming your media from Real-Debrid using Emby, without having to store it locally or even touch a torrent client or a VPN!
---
# "Infinite streaming" from Real Debrid with Emby, Prowlarr, Radarr, and Sonarr

The following page guides the user through the process of establishing an ElfHosted "Infinite Streaming" stack using [Emby][emby], with media stored on [RealDebrid][real-debrid], and with content acquisition managed by [Radarr][radarr] and [Sonarr][sonarr], to search, source, and sort your media, stealthily using symlinks to skip storage stresses!

An enhanced, "ScribeHow" version of this page can be found [here](https://fnky.nz/elfguide-emby-realdebrid-aars).

The stack described below is available in all of our [regular stack bundles](https://store.elfhosted.com/product-category/streaming-bundles/), and free trials are available on the [hobbit](https://store.elfhosted.com/product/hobbit-emby-realdebrid-aars/) bundles.

[Get your 7 day free trial!](https://store.elfhosted.com/product/hobbit-emby-realdebrid-aars/){ .md-button .md-button--primary }

## Requirements

* [x] [Real-Debrid account][real-debrid] and [API token](https://real-debrid.com/apitoken)
* [x] Subscribe to the ElfHosted ["Hobbit" Infinite Arr Emby Streaming bundle](https://store.elfhosted.com/product/hobbit-emby-arrs-real-debrid-infinite-streaming-bundle)

## How does it work?

Here's a diagram (*it's not as complicated as it looks!*), followed by some explanations:

```mermaid
flowchart TD
    Z[fa:fa-user User] --> |Stream|K
    Z[fa:fa-user User] --> A
    Z[User]--> |Manual addition|D
    Z[User]--> |Requests|C
    A[Lists] --> C[Jellyseer]
    C <--> |Add to Arrs|D[Radarr/Sonarr]
    D --> R[Autoscan]
    D <--> |Search for media|E[Prowlarr]
    D <--> |Add to downloader|G[RDTClient]
    E --> |Search trackers|F[torrent.io]
    G <--> |1. Add torrent|H[real-debrid]

    R[Autoscan] --> K[Emby] 

    K[Emby] --> |"Read file (symlink)"|L["/storage/symlinks"]

    K[Emby] --> |"Resolve symlink (actual file)"|J["/storage/realdebrid-zurg"]
    %% G --> |Confirm download|J

    G[RDTClient] --> |3. Create symlink|P["/storage/symlinks"]

    H --> Q[Zurg+rclone]
    Q --> J

    Q --> O
    G[RDTClient] --> |2. Confirm download|O["/storage/realdebrid-zurg"]
```

1. The user adds content to their [Radarr][radarr] / [Sonarr][sonarr], or [Jellyseerr][jellyseerr]
2. Radarr / Sonarr notice the the new addition, and search Prowlarr (*torrentio indexer*) for appropriate files (*matching size, quality, language parameters*)
3. When an appropriate release is found, Radarr / Sonarr schedules a download via [RDTClient][rdtclient], which is presenting a qBittorrent-like API
4. RDTClient adds the torrent to Real-Debrid, and then monitors the zurg rclone mount to confirm the download has succeeded. Upon success, RDTClient **symlinks** the download to Radarr/Sonarr's `completed` directory, and they process is as if it were a local download (*renaming and moving to the media path*)
5. Aars trigger autoscan, which in turn triggers Emby to re-scan the media path containing the new content, and the Plex library is updated!

!!! question "Why not just use [plex_debrid][plex-debrid]?"

    1. For one thing, it only works with Plex :facepalm:
    2. You can use the Aars ability to select custom qualities per movie / show
    3. Integration into Jellyseerr / Arrs is well-understood and mature, and lets friends-and-family request content (*without complicated Plex Watchlist integrations*)

## How to set it up

1. Purchase a subscription to the ["Hobbit" Infinite Arr Emby Streaming bundle](https://store.elfhosted.com/product/hobbit-emby-arrs-real-debrid-infinite-streaming-bundle)
2. Get a [Real-Debrid account][real-debrid] subscription for your ElfHosted account (*can't be used elsewhere at the same time, else you risk being banned*), and copy your [API token](https://real-debrid.com/apitoken)
3. Log into your ElfHosted dashboard (`https://<your username>.elfhosted.com`), and navigate to **Tools** -> **Filebrowser**. Within FileBrowser, navigate to `/config/zurg`, and open your `config.yml` file. Paste your token after the `token: ` line.

{% include 'scribe_realdebrid_zurg_setup.md' %}

{% include 'scribe_emby_libraries_symlinks.md' %}

{% include 'scribe_emby_aars_setup.md' %}

### Setup Blackhole (default)

Setup [Blackhole][blackhole] with your RD credentials (*enabled by default in the Aars*)

### Setup RDTClient (optional)

Configure [RDTClient], by pasting your debrid provider's details into the config section (*the rest is pre-configured*). Disable blackhole (*enabled by default*), and enabled RDTClient as a downloader instead.

## Success!

That's it! You've got the basic plumbing in place for "unlimited storage" from Real-Debrid, managed by the Arrs and streamed by Emby!

!!! warning "Beware Real-Debrid IP bans"
    Be aware that Real-Debrid states:
    
    > You can use your account from any public IP address but you can't use your account from more than one public IP address at the same time.

    So if you use RealDebrid **outside** of ElfHosted, it's likely that your account may be warned / banned.
    
## How do I get help?

1. For general use of the [individual tools](/apps/), refer to the each app's upstream site
2. For specific support re your ElfHosted configuration / account, see the [ElfHosted support options](/get-help/

--8<-- "common-links.md"

{% include 'testimonials.md' %}