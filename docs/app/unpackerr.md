---
title: Elf Hosted Unpackerr 🧝
slug: Unpackerr
description: Unpackerr extracts downloads for Torrents, Radarr, Sonarr, Lidarr and Readarr, and deletes extracted files after import . Use it to automatically unpack archives after download.
upstream: https://github.com/davidnewhall/unpackerr
---

# {{ page.meta.slug }}

Unpackerr extracts downloads for Torrents, [Radarr][radarr], [Sonarr][sonarr], [Lidarr][lidar] and [Readarr][readarr], and deletes extracted files after import . Use it to automatically unpack archives after download.

## How do I use it?

### Troubleshooting

You can examine the Unpackerr logs using [File Browser][filebrowser], at `/config/unpackerr/logs/`. Log files are auto-rotated, so there's no need to worry about truncation, etc.

### Advanced customization

Unpackerr should "just work", provided you use both the built-in API keys for the Arr apps, and download to `/storage/elfstorage/downloads/completed`. For more advanced Unpackerr options, you may (*using [File Browser][filebrowser]*) edit `/conf/unpackerr/unpackerr.conf` and make further customizations. Remember to restart Unpackerr afterwards, using [ElfBot][elfbot], by running `elfbot restart unpackerr`

{% include 'app_footer.md' %}