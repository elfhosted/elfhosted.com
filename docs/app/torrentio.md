---
title: Get ElfHosted Torrentio 🧝 for $0.15/day
slug: Torrentio
description: Torrentio is an extremely popular torrent indexer used for streaming torrents via Stremio. Due to massive usage, the developer has significantly rate-limited the service, and has been clear that he doesn't want to productize it. ElfHosted runs an internal scraper for our users (rate-limited externally), and this product makes the indexer available externally on a per-tenant basis
upstream: https://github.com/Gabisonfire/torrentio-scraper-sh
works_with:
- Prowlarr
- Iceberg
price: 0.15
---

# {{ page.meta.slug }}

Torrentio is an extremely popular torrent indexer used for streaming torrents via Stremio. Due to massive usage, [the developer has significantly rate-limited the service](https://github.com/TheBeastLT/torrentio-scraper/issues/199#issuecomment-1913347357), and has been clear that he doesn't want to productize it.

ElfHosted runs an internal scraper for our users (*rate-limited externally*), and this product makes the indexer available externally on a per-tenant basis

[Get Elf Hosted {{ page.meta.slug }} from $0.15/day :magic_wand:](https://store.elfhosted.com/product/{{ page.meta.slug | lower }}/){ .md-button .md-button--primary }

![Screenshot of {{ page.meta.slug }}](/images/screenshots/{{ page.meta.slug | lower }}.png){ loading=lazy }

{% include 'app_access.md' %}

## How do I use it?

!!! warning "Hacky code ahead"
    Be aware our instance is a fork of [Gabisonfire/torrentio-scraper-sh](https://github.com/Gabisonfire/torrentio-scraper-sh/tree/master), which in turn is a fork of the original ([TheBeastLT/torrentio-scraper](https://github.com/Gabisonfire/torrentio-scraper-sh/tree/master)). Some features from the public torrentio don't yet work, and the database doesn't have the years of history that torrentio did. This is a work in progress :)

### Install the Addon!

Click "**Install**" to allow your OS to open the link in Stremio, or right-click the **Install** button, and copy the long `stremio://` URL, and paste it into your Stremio search bar.

### Am I rate-limited?

Yes, but the intention is that the rate-limit be generous, and enough to share with up to 10 friends / devices.

We're still dialing this in, but you can see the current limit [here](https://github.com/geek-cookbook/elf-charts/blob/main/charts/other/myprecious/templates/middleware/middleware-torrentio-rate-limit.yaml)

### Can I try it out?

Sure, the free public version is at https://torrentio.elfhosted.com - it's the same database, just a lower rate-limit.

### Can I use it with Prowlarr?

All ElfHosted apps get unrestricted access to the internal endpoint, at `http://elfhosted.torrentio`[^1]. So yes. See [Prowlarr][prowlarr] for instructions re adding the indexer.

### Can I use it with Iceberg?

Yes, Iceberg already supports custom URLs for torrentio endpoints. Use `http://elfhosted.torrentio`[^1] - see [Iceberg][iceberg] for instructions.

{% include 'app_footer.md' %}

[^1]: No, that's not a typo, it's a [Kubernetes service](https://github.com/funkypenguin/elf-infra/blob/ci/torrentio/service-elfhosted.yaml) called `elfhosted` in the namespace `torrentio`, on port `80`!