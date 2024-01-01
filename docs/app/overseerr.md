---
title: Elf Hosted Overseerr 🧝 from $0.05/day
slug: Overseerr
description: Overseerr is a request management and media discovery tool built to work with your existing Plex ecosystem
upstream: https://overseerr.dev
links:
- name: subreddit
  uri: https://www.reddit.com/r/Overseerr
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
1. Navigate in FileBrowser to config > overseerr > branding
3. Overwrite the logo_stacked.svg and logo_full.svg
4. Restart Overseerr using ElfBot

You may just need to play with the size of the image to get it to fit correctly.

{% include 'app_footer.md' %}
