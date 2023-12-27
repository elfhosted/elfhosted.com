---
title: Elf Hosted ruTorrent 🧝 from $0.10/day
slug: ruTorrent
description: ruTorrent is a popular Bittorrent client for power users, which includes the unique ability (among our torrent apps) to create torrents from its web UI.
upstream: https://github.com/Novik/ruTorrent
links:
works_with:
- LazyLibrarian
- Mylar
- Radarr
- Readarr
- Sonarr
price: 0.10
---

# {{ page.meta.slug }}

ruTorrent is a popular Bittorrent client for power users, which includes the unique ability (*among our torrent apps*) to create torrents from its web UI.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it ?

### Set inbound port

If you're using Private Internet Access, or ProtonVPN, then your inbound port will be automatically configured for you.

If you're using a different VPN provider, you may need to manually configure a port assigned to you by your VPN provider. In this case, use [FileBrowser][filebrowser] to create `/config/rtorrent/forwarded-port-override`, populated with the port number you'd like rtorrent to listen on.

Restart rutorrent using [ElfBot][elfbot], and the port will be fixed at the one you specified.

{% include 'faq_use_mam.md' %}

{% include 'app_footer.md' %}