---
date: 2023-07-20
categories:
  - app
tags:
  - premiumize
  - radarr
  - sonarr
  - lidarr
  - mylar
  - rdtclient
title: Introducing RDT Client
description: RDT Client is a web interface to manage your torrents on Real-Debrid, AllDebrid or Premiumize
---
# Introducing RDT Client

Today we added RDT Client, a web interface to manage your torrents on [Real-Debrid](https://real-debrid.com/?id=1348683), [AllDebrid](https://alldebrid.com/?uid=2v91l) or [Premiumize](https://www.premiumize.me/).

![Screenshot of RDT client](/images/screenshots/rdtclient.png)

It supports the following features:

* [x] Add new torrents through magnets or files
* [x] Download all files from Real-Debrid, AllDebrid or Premiumize to your local machine automatically
* [x] Unpack all files when finished downloading
* [x] Implements a fake [qBittorrent][qbittorrent] API so you can hook up other applications like [Sonarr][sonarr], [Radarr][readarr], [Lidarr][lidarr], etc

The fake qBittorrent API is the killer feature - it means you can hook your Premiumize (etc) subscription to the Arrs, and auto-source and download directly as if you were using qBittorrent locally.

See more on the [app][rdtclient] page, or perform a 24h trial / subscription at the [store](https://store.elfhosted.com/product/rdtclient/)!

--8<-- "common-links.md"

