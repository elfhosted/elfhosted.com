---
title: Get Elf Hosted Stremio-Jackett 🧝 from $0.05/day
slug: Stremio-Jackett
description: Stremio-Jackett is a clever Stremio add-on, which will search your Jackett instance for content, and then pass the results to Real-Debrid, allowing for near-instant streaming directly from RealDebrid to Stremio
upstream: https://github.com/aymene69/stremio-jackett/
links:
- name: Discord
  uri: https://discord.gg/7yZ5PzaPYb
works_with:
- Jackett
---

# {{ page.meta.slug }}

Stremio is an ingenious [Stremio](https://strem.io) addon, developed by @aymene69 and @hyoretsu, which acts as the "glue" between Stremio and [Real-Debrid][real-debrid], using your own [Jackett][jackett] indexer to seek out suitable torrents, and your Real-Debrid API key to identify cached torrents.

This integration can be useful if you want to avoid relying on 3rd-party addons, or search your private trackers for content to stream to Stremio via Debrid or even directly!

The result is a beautifully polished Stremio experience across your devices, to instantly stream any available torrent, without relying on the (*often overloaded*) torrentio addon!

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

!!! warning "Under active development"
    Be aware that stremio-jackett is under **rapid** development, so some features may change / break over time. It's also a little awkward to use in some cases (*you can't edit your addon, for example, you have to uninstall and reinstall*)

First, setup [Jackett][jackett], by adding your indexers, and copying your API key.

Next, navigate to **Stremio Jackett** from your ElfHosted dashboard, and enter your [Real-Debrid][real-debrid] API key, as well as your Jackett API key:

![](/images/stremio-jackett-setup-1.png)

Click "**Install**", and allow your OS to open the link in Stremio!

That's it!

{% include 'app_footer.md' %}