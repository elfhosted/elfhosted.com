---
title: sElfHosted RDTClient 🪄 from $0.05/day
slug: rdtclient
description: A web interface to manage your torrents on Real-Debrid, AllDebrid or Premiumize
upstream: https://github.com/rogerfar/rdt-client
---

# {{ page.meta.slug }}

RDT Client a web interface to manage your torrents on [Real-Debrid](https://real-debrid.com/?id=1348683), [AllDebrid](https://alldebrid.com/?uid=2v91l) or [Premiumize](https://www.premiumize.me/).

It supports the following features:

* [x] Add new torrents through magnets or files
* [x] Download all files from Real-Debrid, AllDebrid or Premiumize to your local machine automatically
* [x] Unpack all files when finished downloading
* [x] Implements a fake qBittorrent API so you can hook up other applications like Sonarr, Radarr or Couchpotato.

{% include 'app.md' %}
{% include 'app_access.md' %}

## Set your download directory

The app defaults to saving to `/data/downloads` - this will fail, and needs to be changed to your desired `/storage/<whatever>` mount.

{% include 'app_footer.md' %}