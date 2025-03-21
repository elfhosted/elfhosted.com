---
title: 🧝 Hosted AudioBookRequest 🎧
slug: AudioBookRequest
upstream: https://github.com/markbeep/AudioBookRequest
links:
- name: Official Subreddit 
  uri: https://www.reddit.com/r/audiobookshelf
- name: Discord server
  uri: https://discord.gg/SsFRXWMg7s
- name: GitHub repo
  uri: https://github.com/markbeep/AudioBookRequest
description: Automates audiobook requests / downloads
---

# {{ page.meta.slug }}

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### AudioBookRequests

Upon launch, you'll be prompted to create a username/password. Once this is completed, you'll be able to access the app, and configure more users for requests.

Setup Prowlarr, (*hostname is `http://prowlarr:9696`*, find your API key in `Settings->General`*), and enable auto-downloading.

### Prowlarr

You'll need to configure [Decypharr][decypharr] as a downloader in Prowlarr itself, and ensure you have indexers added which can search for audiobooks (*Zilean cannot*).

!!! warning
    AudioBookRequests support is new, and bugs / issues are to be expected.

### Where are my downloads?

Currently, downloads will end up in `storage/symlinks/downloads/prowlarr`. There may be a future option to change this path, so that downloads can be directly make accessible to [AudioBookShelf][audiobookshelf].

{% include 'app_footer.md' %}