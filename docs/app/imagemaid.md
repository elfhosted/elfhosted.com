---
title: Elf Hosted ImageMaid
slug: ImageMaid
description: ImageMaid cleans up your Plex images, removing bloat, custom art, etc.
upstream: https://github.com/Kometa-Team/ImageMaid
sponsorship: 
- name: GitHub Sponsors
  uri: https://github.com/sponsors/meisnate12
---

# {{ page.meta.slug }}

ImageMaid cleans up your Plex images, removing bloat, custom art, etc.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How to use ImageMaid

### Plex Token

ImageMaid needs a Plex token in order to interact with Plex.

Grab a [Plex token][plex-token], and use [ElfTerm][elfterm] to run:

```bash
elfbot env imagemaid PLEX_TOKEN=<token here>
```

Plex will restart (*ImageMaid runs on Plex's pod*), after which the UI should load. After 10 seconds, ImageMaid will go into "scheduled run" mode, and run once a week.

### Running 

To run ImageMaid immediately, hit `CTRL-C`, and then `ENTER` to restart, and hit any key within 10 seconds.

### Discord Notifications

To receive notifications in Discord, you'll want to set a Discord webhook, using:

```bash
elfbot env imagemaid DISCORD=<discord webhook url>
```

{% include 'app_footer.md' %}