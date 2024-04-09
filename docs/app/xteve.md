---
title: Elf Hosted xTeVe 🧝 from $0.10/day
slug: xTeVe
description: xTeVe M3U Proxy for Plex DVR and Emby Live TV
upstream: https://github.com/xteve-project/xTeVe
price: 0.10
---

# {{ page.meta.slug }}

xTeVe M3U Proxy for Plex DVR and Emby Live TV

{% include 'app.md' %}

!!! note
    Note that DVR functionality in either Plex or Emby requires a paid subscription (*either PlexPass or Emby Premier*)

Features include:

Files

- Merge external M3U files
- Merge external XMLTV files
- Automatic M3U and XMLTV update
- M3U and XMLTV export

Channel management

- Filtering streams
- Channel mapping
- Channel order
- Channel logos
- Channel categories

Streaming

- Buffer with HLS / M3U8 support
- Re-streaming
- Number of tuners adjustable
- Compatible with Plex / Emby EPG


{% include 'app_access.md' %}

## How do I use it

### Connecting to Plex

Because we run Plex behind a VPN, it's not possible for Plex to "see" xteve by name. However, we can use its Kubernetes service IP address, which doesn't change for the life of the service (*it'll change if you uninstall and reinstall though!*)

To get the IP of your xteve service, use [Kubernetes Dashboard][kubernetes-dashboard], search for `xteve`, and look for the ClusterIP of the **service**, as illustrated below:

![](/images/xteve-identify-service-ip.png)

Then use the cluster IP to connect Plex to XTeve, in the syntax `http://<IP>:33400`

{% include 'app_footer.md' %}