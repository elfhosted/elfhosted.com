---
title: Recyclarr
slug: Recyclarr
description: Recyclarr automatically synchronizes recommended settings from the TRaSH guides to your Sonarr/Radarr instances
upstream: https://github.com/recyclarr/recyclarr
links:
works_with:
- Radarr
- Sonarr
sponsorship:
- uri: https://github.com/sponsors/rcdailey
  name: GitHub Sponsors
price: 0.10
---

# {{ page.meta.slug }}

Recyclarr automatically synchronizes recommended settings from the [TRaSH guides](https://trash-guides.info/) to your Sonarr/Radarr instances.

[Get Elf Hosted {{ page.meta.slug }} from ${{ page.meta.price }}/day :magic_wand:](https://store.elfhosted.com/product/{{ page.meta.slug | lower }}/){ .md-button .md-button--primary }

## How do I use it?

There's no UI for Recyclarr, but you can edit the config file in `config/recyclarr` (*your Dashboard link will also take you here*).

The config file is created upon first install, and is not changed thereafter, unless you reset Recyclarr with `elfbot reset recyclarr --yesiamsure` in Filebrowser.

By default, recyclarr runs `@daily`, but it also runs once upon restart, in a separate pod named `sync`. Take advantage of this to test your config, and use ElfBot or Kubernetes Dashboard to restart it, watching the "sync" container for debug logs, as illustrated below:

![](/images/recyclarr-logs-1.png)

![](/images/recyclarr-logs-2.png)

!!! tip "This screenshot shows an error"

{% include 'app_footer.md' %}