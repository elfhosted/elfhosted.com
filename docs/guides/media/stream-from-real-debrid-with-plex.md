---
title: Stream from Real-Debrid with Plex
description: This guide describes how to setup your own "stremio", streaming your media from Real-Debrid using Plex, without having to store it locally or even touch a torrent client or a VPN!
---
# "Infinite streaming" from Real Debrid with Plex

This page describes a minimal solution to create your "infinite" Plex library, utilizing [Real-Debrid][real-debrid] for all media, streaming through your ElfHosted [Plex][plex] instance.

The advantages of this solution are:

* No torrent clients, VPNs, ratios or seeding
* No storage constraints, unpacking issues, migrations etc

The disadvantages, of course, are:

* Limited retention - you've only "got" the content as long as your Real-Debrid subscription is current

## Requirements

* [x] [Real-Debrid account][real-debrid] and [API token](https://real-debrid.com/apitoken)

And from the [ElfHosted store][store]:

* [x] [plex_debrid][plex-debrid]
* [x] [Zurg][zurg]
* [x] [Zurg Rclone Mount](https://store.elfhosted.com/product/rclone-real-debrid/)
* [x] [Plex][plex]

Add the apps above to your cart, or subscribe to all of the above, as a bundle to make it easier, here:

[Get all the apps, bundled, for $0.30/day! :gift:](https://store.elfhosted.com/product/minimal-real-debrid-plex-streaming-bundle){ .md-button .md-button--primary }

## How does it work?

Here's a diagram, followed by some explanations:

```mermaid
flowchart TD
    K[Plex] --> |Stream|Z[User]
    Z[User] --> |Add to watchlist|K[Plex]
    K[Plex] --> |Watchlist|G[plex_debrid]
    G[plex_debrid] --> |Scan on download|K[Plex]
    G[plex_debrid] <--> |Find and add torrent|H[real-debrid]
    H --> I[Zurg]
    I --> |/storage/real-debrid/...|J[rclone mount]
    K[Plex] <--> |Library|J
```

1. The user adds content to their [Plex][plex] Watchlist
2. [Plex_debrid][plex-debrid] notices the change to the watchlist, searches for suitable cached torrents on [Real-Debrid][real-debrid], triggers a download, and then tells Plex to rescan the appropriate Library
3. [Zurg][zurg] + the rclone mount make it appear that the Real-Debrid account is locally mounted to Plex
4. Plex detects the new content, adds it to the library, and it's ready to stream!

Here's a demo from the plex_debrid repo:

![Demo of operation of plex_debrid](/images/plex-debrid-demo.gif){ loading=lazy }

## How to set it up

Here's a little more detail..

1. Get a [Real-Debrid account][real-debrid] subscription for your ElfHosted account (*can't be used elsewhere at the same time, else you risk being banned*), and copy your [API token](https://real-debrid.com/apitoken)
2. Paste the token into the [Zurg product][store/zurg] on the store, and add to your cart
3. Add at the [Zurg rclone mount][store/zurgmount] and [Plex][store/plex] to your cart, and buy with [ElfBuckz][elfbuckz]!

On purchase, you'll get the necessary components deployed, but some configuration will be required, see below:

### Setup Real-Debrid

Currently, Zurg will crash if your Real-Debrid account is empty. This is scheduled for fix in the next release, but in the meantime, ensure that you have at least one file to be detected as "movies", and another as "shows".

Confirm Zurg is setup correctly by browsing it from your ElfHosted dashboard.

### Setup Plex

Claim your Plex instance using [ElfBot][elfbot], and add 2 new media libraries ("movies" and "shows") pointing to `/storage/real-debrid-zurg/[movies/shows]`

### Setup plex_debrid

Launch [plex-debrid][plex-debrid] from your dashboard, and perform the initial setup, then tell it to run.

## Success!

That's it, you're done. Adding content to your Plex watchlist should trigger plex_debrid to find it for you, and once it appears in your real-debrid account, Zurg will make it available to Plex to stream! Hope into our [friendly Discord server][discord] if you have questions or suggestions!

!!! warning "Beware Real-Debrid IP bans"
    Be aware that Real-Debrid states:
    
    > You can use your account from any public IP address but you can't use your account from more than one public IP address at the same time.

    So if you use RealDebrid **outside** of ElfHosted, it's likely that your account may be warned / banned.

--8<-- "common-links.md"