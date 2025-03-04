---
title: 🧝 Hosted Debridav
slug: Debridav
description: Deluge is a lightweight, Free Software, cross-platform BitTorrent client
works_with:
- Radarr
- Sonarr
upstream: https://deluge-torrent.org
sponsorship: 
- name: Patreon
  uri: https://www.patreon.com/deluge_cas
---

# {{ page.meta.slug }}

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### RealDebrid

To use Debridav with RealDebrid, you'll need to set the `DEBRIDAV_DEBRIDCLIENTS` env var accordingly, like this:

```
elfbot env debridav DEBRIDAV_DEBRIDCLIENTS=real_debrid
```

You'll also need to set your RD API key, like this:

```
elfbot env debridav REAL-DEBRID_APIKEY=<your key>
```

{% include 'app_footer.md' %}