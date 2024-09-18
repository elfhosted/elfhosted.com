---
title: Elf Hosted Blackhole Scripts 🧝
slug: Blackhole
description: West's Blackhole Script is part of a collection of scripts maintained by westsurname, intended to support Plex users with Debrid services
upstream: https://github.com/westsurname/scripts
---

# {{ page.meta.slug }}

"West's Blackhole Script" is part of a collection of scripts maintained by @westsurname, intended to support Plex users with Debrid services.

Within ElfHosted, the blackhole scripts provide a lightweight alternative to the symlinking functionality that RDTClient provides to [Radarr][radarr] / [Sonarr][sonarr].

{% include 'app.md' %}
{% include 'app_access.md' %}

## How to use it

### Configure Blackhole

!!! note "Only set ENV var once"
    You'll note both an "Blackhole" and a "Blackhole 4K" link on your dashboard. This is to accommodate our dual-Aarr design, but it's only necessary to configure your RD API key in `blackhole` (*so just run the elfbot commands as illustrated below*).

#### Real-Debrid

Blackhole needs your RealDebrid API token. Use [ElfBot][elfbot] to provide your token as an ENV var, by running: 

```
elfbot env blackhole REALDEBRID_API_KEY=<paste token here>
```

#### Torbox

Alternatively, Blackhole can be used with Torbox. Once again, ENV vars are required, as follows:

```
elfbot env blackhole TORBOX_API_KEY=<paste token here>
elfbot env blackhole TORBOX_ENABLED=true
```

!!! warning "Torbox requires mount"
    To make your Torbox data visible to your apps, you'll need to purchase a [Torbox mount](https://store.elfhosted.com/product/torbox-mount)

### Configure Aaars

Under each Aarr, add a new "Torrent Blackhole" download client, as follows:

* Torrent folder: `/storage/symlinks/blackhole/<name of aarr>/`
* Watch folder: `/storage/symlinks/blackhole/<name of aarr>/completed`
* Save magnet files: **checked**
* Save Magnet Files Extension: `.magnet`
* Read only: **unchecked**
* Remove Completed: **checked**

For example:

![](/images/blackhole-arr-1.png)

!!! tip "Set to the appropriate Aarr"
    When copying details above, remember to customize the path for the specific Aarr you're using!

{% include 'app_footer.md' %}
