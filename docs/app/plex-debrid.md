---
title: Elf Hosted plex_debrid 🧝 from $0.5/day
slug: Plex-Debrid
description: ruTorrent is a popular Bittorrent client for power users, which includes the unique ability (among our torrent apps) to create torrents from its web UI.
upstream: https://github.com/Novik/ruTorrent
links:
- name: GitHub
  uri: https://github.com/itsToggle/plex_debrid
works_with:
- Plex
- Jellyfin
- Emby
- Zurg
- Overseerr
- Jellyseerr
price: 0.5
---

# {{ page.meta.slug }}

plex_debrid facilicates [Plex][Plex] / [Emby][emby] / [Jellyfin][jellyfin] / Infuse torrent streaming through Debrid Services, using Plex Discover Watchlists, Trakt lists and [Overseerr] / [Jellyseerr].

Using content services like plex discover, trakt and overseerr, your personal media server users can add movies/shows to their watchlist and they become available to stream in seconds.

[Get Elf Hosted {{ page.meta.slug }} from ${{ page.meta.price }}/day :magic_wand:](https://store.elfhosted.com/product/{{ page.meta.slug | lower }}/){ .md-button .md-button--primary }

Here's a demo from the [upstream repo](https://github.com/itsToggle/plex_debrid):

![Screenshot of {{ page.meta.slug }}](/images/plex-debrid-demo.gif){ loading=lazy }

!!! warning "Advanced use"
    plex_debrid is an advanced and complex tool, you should expect to spend some time troubleshooting!

    Further, plex_debrid requires an [rclone WebDAV mount](https://store.elfhosted.com/product/rclone-webdav-mount/) to your Debrid service, and if using Real-Debrid, you'll want [Zurg][zurg] plus the [Zurg-specific WebDAV mount](https://store.elfhosted.com/product/rclone-real-debrid/)!

{% include 'app_access.md' %}

## How do I use it ?

### Initial setup

plex_debrid is unusual in that it requires a CLI-based setup. For this reason, we run it within a VNC-based browser session. 

The first time you open plex_debrid, you'll be prompted with the "setup wizard". Go through the wizard and enter the necessary details as prompted.

ElfHosted-specific config steps are illustrated below:

### Connect Plex

When you connect to plex, use the URL `http://plex:32400`

![Screenshot of {{ page.meta.slug }} connecting to plex](/images/plex-debrid-add-local-plex.png){ loading=lazy }

### Connecting to Overseerr / Jellyseerr

To optionally connect to Jellyseerr / Overseerr, enter their details per [Connecting Apps](/how-to/connect-apps/), as illustrated below:

![Screenshot of {{ page.meta.slug }} connecting to Jellyseerr](/images/plex-debrid-add-overseerr-jellyseerr.png){ loading=lazy }

{% include 'app_footer.md' %}