---
title: sElfHosted NZBGet 🪄 from $0.15/day
slug: NZBGet
description: NZBGet is an efficient usenet downloader
upstream: https://nzbget.net
links:
- name: subreddit
  uri: https://www.reddit.com/r/nzbget
works_with:
- LazyLibrarian
- Lidarr
- Mylar
- Prowlarr
- Radarr
- Readarr
- Sonarr
price: 0.15
---

# {{ page.meta.slug }}

NZBGet is an efficient usenet downloader

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

The default of the configuration is already fine-tuned for our environment (*so take care making changes!*), but you'll want to configure your own news servers before NZBGet will download anything.

## How does /tmp work?

!!! warning
    Because `/tmp` is on a tmpfs (*to make it uber-fast to download and unpack, before transferring to storage*), if you restart the pod, you'll lose everything currently in `/tmp`. If you're going to restart NZBGet, you'll want to pause downloads, ensure that any pending downloads have been moved to `/storage`, and **then** perform the restart.

{% include 'app_footer.md' %}