---
slug: Deluge
description: Deluge is a lightweight, Free Software, cross-platform BitTorrent client
works_with:
- Autobrr
- Lidarr
- Prowlarr
- Radarr
- Readarr
- Sonarr
upstream: https://deluge-torrent.org
---

# {{ page.meta.slug }}

Deluge is a lightweight, Free Software, cross-platform BitTorrent client.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### What's the password for Deluge?

The default credentials are:

* user: `deluge`

See [here][connect-apps] for details re connecting with your other apps.

### I can't connect my Arr apps to Deluge

Deluge requires the "Label" plugin for compatibilty with Arr, which is already enabled on our default Deluge config.

{% include 'app_footer.md' %}