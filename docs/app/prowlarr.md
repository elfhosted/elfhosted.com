---
title: Elf Hosted Prowlarr 🧝 from $0.10/day
slug: Prowlarr
description: Prowlarr is an indexer manager/proxy built on the popular arr .net/reactjs base stack to integrate with your various PVR apps. Prowlarr supports management of both Torrent Trackers and Usenet Indexers
upstream: https://wiki.servarr.com/prowlarr
links:
- name: subreddit
  uri: https://www.reddit.com/r/prowlarr
works_with:
- Deluge
- LazyLibrarian
- NZBGet
- qBittorrent
- Radarr
- Readarr
- ruTorrent
- SABnzbd
- Sonarr
sponsorship: 
- name: Open Collective
  uri: https://opencollective.com/prowlarr
- name: GitHub Sponsors
  uri: https://github.com/sponsors/prowlarr
- name: Bitcoin
  uri: https://prowlarr.com/donate
---

# {{ page.meta.slug }}

Prowlarr is an indexer manager/proxy built on the popular arr .net/reactjs base stack to integrate with your various PVR apps. Prowlarr supports management of both Torrent Trackers and Usenet Indexers. 

It integrates seamlessly with [Lidarr][lidarr], [Mylar][mylar], [Radarr][radarr], [Readarr][readarr], and [Sonarr][sonarr], offering complete management of your indexers with no per app indexer setup required.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### Adding torrentio

There are two custom indexers pre-provisioned with Prowlarr.. one is for the public Torrentio, which is significantly rate-limited, and the other is for the ElfHosted internal instance, which is free and unrestricted to all ElfHosted apps.

Search for "torrentio" to find and setup the indexers:

![](/images/prowlarr-setup-torrentio.png)

### Enabling apps

All the supported apps are pre-configured in Prowlarr, but set to a disabled state. To enable Radarr and Sonarr, for example, you'd edit each disabled app, check the "**Enabled**" checkbox, and test and save. 

Then "Sync app indexers" to have Prowlarr sync your indexers to the supported, enabled apps :thumbsup:

{% include 'app_footer.md' %}