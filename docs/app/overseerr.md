---
title: Elf Hosted Overseerr 🧝
slug: Overseerr
description: Overseerr is a request management and media discovery tool built to work with your existing Plex ecosystem
upstream: https://overseerr.dev
links:
- name: subreddit
  uri: https://www.reddit.com/r/Overseerr
sponsorships:
- name: Patreon
  uri: https://www.patreon.com/overseerr
- name: GitHub Sponsors
  uri: https://github.com/sponsors/sct
---

# {{ page.meta.slug }}

Overseerr is a request management and media discovery tool built to work with your existing Plex ecosystem.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

Sign in in with your [Plex][plex] account, or your ElfHosted [Emby][emby] account (*use `emby:8096` as your hostname*) and [connecting to your apps][connect-apps] of choice.

## Custom Branding

You can now change the branding on both the login page and within the app.
To do so:

1. Navigate in [FileBrowser][filebrowser] to `config/overseerr/branding`
3. Overwrite `logo_stacked.svg` and `logo_full.svg`
4. Refresh your browser tab to see the changes

Some adjustments / trial-and-error re the size of the images may be required to get them to fit correctly.

{% include 'app_footer.md' %}
