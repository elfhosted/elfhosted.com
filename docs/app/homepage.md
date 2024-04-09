---
title: 🧝 Hosted Homepage (from $0.10/day)
slug: Homepage
description: A modern, fully static, fast, secure fully proxied, highly customizable application dashboard with integrations for over 100 services and translations into multiple languages. Easily configured via YAML files or through docker label discovery.
upstream: https://gethomepage.dev/
sponsorship: 
- name: GitHub Sponsors
  uri: https://github.com/benphelps
---

# {{ page.meta.slug }}

Homepage is a modern, fully static, fast, secure fully proxied, highly customizable application dashboard with integrations for over 100 services and translations into multiple languages. Easily configured via YAML files or through docker label discovery.

{% include 'app.md' %}

{% include 'app_access.md' %}

## How do I use it?

### Searching

Too many apps? Just start typing, to launch Homepage's integrated app search!

### Integrations

Wherever possible, we've pre-configured homepage to work with your ElfHosted apps. In some cases, however, you'll need settings like API keys an user credentials which only you can configure (*a [Plex][plex] token, for example*). In these case, the instructions below will explain how to integrate Homepage with your apps using these details.

### Plex

Per the [homepage Plex docs](https://gethomepage.dev/main/widgets/services/plex/), the available integration with [Plex][Plex] is quite limited, and you may prefer to use the [Tautulli] integration instead. To setup basic Plex integration, follow [these instructions](https://www.plexopedia.com/plex-media-server/general/plex-token/) to retrieve your Plex token, and save it into `config/homepage/user-change-these/PLEX_KEY`

### Jellyfin

To add a Jellyfin integration to your homepage dashboard, [homepage Jellyfin docs](https://gethomepage.dev/main/widgets/services/jellyfin/), navigate to `Advanced > Api Keys` in your Jellyfin dashboard, create a new API key for homepage, and save it into `config/homepage/user-change-these/JELLYFIN_KEY`

### Emby

To add a Jellyfin integration to your homepage dashboard, [homepage Emby docs](https://gethomepage.dev/main/widgets/services/emby/), navigate to `Advanced > Api Keys` in your Emby dashboard, create a new API key for homepage, and save it into `config/homepage/user-change-these/EMBY_KEY`

### Navidrome

Per the [homepage Plex docs](https://gethomepage.dev/main/widgets/services/navidrome/), you'll need to follow [these instructions](http://www.subsonic.org/pages/api.jsp) to generate a username, token, and a salt, and store them as:

* `config/homepage/user-change-these/NAVIDROME_USER`
* `config/homepage/user-change-these/NAVIDROME_TOKEN`
* `config/homepage/user-change-these/NAVIDROME_SALT`

Here's a quick overview of the instructions:

1. Pick a value for your salt, of at least 6 characters.
2. Generate your token by creating an MD5 hash of `<your password><your salt>`

For example, if your username is `bruce`, your password is `batman`, and you pick `spanky` as your salt, then you can use https://www.md5hashgenerator.com/ to generate an MD5 sum of `batmanspanky`. You'll set your values like this:

* `NAVIDROME_USER: bruce`
* `NAVIDROME_TOKEN: e165c7450e4e51846af33ae0f2c24fd9`
* `NAVIDROME_SALT: spanky`

### Komga

To add a [Komga][komga] integration to your homepage dashboard, you simply need to set the following to match your komga username / password:

* `config/homepage/user-change-these/KOMGA_USERNAME`
* `config/homepage/user-change-these/KOMGA_PASSWORD`

### Kavita

To add a [Kavita][kavita] integration to your homepage dashboard, you simply need to set the following to match your Kavita username / password:

* `config/homepage/user-change-these/KAVITA_USERNAME`
* `config/homepage/user-change-these/KAVITA_PASSWORD`

### Audiobookshelf

To add a [Audiobookshelf][audiobookshelf] integration to your homepage dashboard, log into Audiobookshelf as an admin, navigate to `config -> users`, and click on your account to display your API key. Save the key into `config/homepage/user-change-these/AUDIOBOOKSHELF_KEY`.

### Overseerr

To add an [Overseerr][overseerr] integration to your homepage dashboard, log into Overseerr, and navigate to `Settings -> General` to view your API key - save the it into `config/homepage/user-change-these/OVERSEERR_KEY`.

### Jellyseerr

To add an [Jellyseerr][jellyseerr] integration to your homepage dashboard, log into Jellyseerr, navigate to `Settings -> General`, to view your API key - save the it into `config/homepage/user-change-these/JELLYSEERR_KEY`.

### Ombi

To add an [Ombi][ombi] integration to your homepage dashboard, log into Qmbi, navigate to `Settings > Configuration > General`, to view your API key - save the it into `config/homepage/user-change-these/OMBI_KEY`.

### [Tautulli][tautulli]

To add a Tautulli integration to your homepage dashboard, per the [homepage Tautulli docs](https://gethomepage.dev/main/widgets/services/plex-tautulli/), navigate to `Settings > Web Interface > API` in Tautulli, grab your API key, and save it into `config/homepage/user-change-these/TAUTULLI_KEY`

### Autobrr

To add an [Autobrr][autobrr] integration to your homepage dashboard, log into Autobrr, navigate to `Settings > API Keys`, and create a new API key for Homepage - save the it into `config/homepage/user-change-these/AUTOBRR_KEY`.

### Miniflux

To add a [miniflux][miniflux] integration to your homepage dashboard, log into Miniflux, navigate to `Settings > API Keys`, and create a new API key for Homepage - save the it into `config/homepage/user-change-these/MINIFLUX_KEY`.

### Uptime Kuma

To add an [Uptime Kuma][uptimekuma] integration to your homepage dashboard, setup a status page in Uptime Kuma, and save its "slug" to `config/homepage/user-change-these/UPTIMEKUMA_SLUG`.

### Gotify

To add an [Gotifya][gotify] integration to your homepage dashboard, create a new Gotify client token, and save it in `config/homepage/user-change-these/GOTIFY_KEY`.

{% include 'app_footer.md' %}
