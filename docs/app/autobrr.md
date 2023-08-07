---
title: sElfHosted Autobrr 🪄 from $0.05/day
slug: Autobrr
description: Autobrr monitors IRC announce channels to get releases as soon as they are available, with good filtering
works_with:
- Radarr
- Sonarr
upstream: https://autobrr.com
---

# {{ page.meta.slug }}

Autobrr monitors IRC announce channels to get releases as soon as they are available, with good filtering.

{% include 'app.md' %}

Features include:

- Single binary + config for easy setup
- Support for 30 trackers
- Easy to use UI
- Available torrent actions:
  - qBittorrent
  - Deluge
  - Radarr
  - Sonarr
  - Lidarr
  - Save to watch folder
  - Run custom commands

{% include 'app_access.md' %}

## How do I use it?

Upon launch, you'll be prompted to create a username/password. Once this is completed, you'll be able to access the app, and configure your indexers, groups, etc.

See [here][connect-apps] for details re connecting with your other apps.

## Torrent Clients

### [Deluge][deluge]

* Type: `Deluge 2`
* Host: `deluge`
* Port: `58846`
* Username - `autobrr` 
* Password - `c7RJKKt#KBcM5Z?a` (*this is the default value set in our deluge*)

### [qBitorrent][qbittorrent]

* Type: `qBittorrent`
* Host: `http://qbittorrent:8080` 
* Username/Password: `<leave blank>`

### [ruTorrent][rutorrent]

* Type: `rTorrent`
* Host: `http://rutorrent:8080/plugins/rpc/rpc.php`

{% include 'app_footer.md' %}