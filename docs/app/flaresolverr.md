---
title: Elf Hosted Flaresolverr 🧝
description: FlareSolverr is a proxy server to bypass Cloudflare protection commonly applied to indexers / trackers, so that they can be auto-queried by Prowlarr
slug: Flaresolverr
upstream: https://github.com/FlareSolverr/FlareSolverr
works_with:
- Prowlarr
---

# {{ page.meta.slug }}

FlareSolverr is a proxy server to bypass Cloudflare protection commonly applied to indexers / trackers, so that they can be auto-queried by [Prowlarr][prowlarr].

## How do I use it?

Configure Flaresolverr as a proxy in [Prowlarr][prowlarr] under `Settings --> Indexers` as follows:

* name: `flaresolverr`
* tags: `flaresolverr`
* host: `http://flaresolverr:8191`

Then add the `flaresolverr` tag to any indexers requiring it.

## Viewing Flaresolverr logs

Examine `/config/flaresolverr` using [FileBrowser][filebrowser].

{% include 'app_footer.md' %}
