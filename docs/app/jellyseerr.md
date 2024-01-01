---
title: Elf Hosted Jellyseerr 🧝 from $0.05/day
slug: Jellyseerr
description: Jellyseer is a Jellyfin/Emby-compatible fork of Overseerr, a request management and media discovery tool built to work with a existing Plex ecosystem.
upstream: https://noted.lol/jellyseerr/
links:
- name: GitHub
  uri: https://github.com/Fallenbagel/jellyseerr
---

# {{ page.meta.slug }}

Jellyseer is a Jellyfin/Emby-compatible fork of [Overseerr][overseerr], a request management and media discovery tool built to work with a existing Plex ecosystem.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

Sign in in with your [Plex][plex] account, or your ElfHosted [JellyFin][jellyfin] / [Emby][emby] account (*use `jellyfin:8096` or `emby:8096` as your hostname*) and [connecting to your apps][connect-apps] of choice.

## Custom Branding

You can now change the branding on both the login page and within the app.
To do so:

1. Navigate in [FileBrowser][filebrowser] to `config/jellyseerr/branding`
3. Overwrite `logo_stacked.svg` and `logo_full.svg`
4. Refresh your browser tab to see the changes

Some adjustments / trial-and-error re the size of the images may be required to get them to fit correctly.

{% include 'app_footer.md' %}