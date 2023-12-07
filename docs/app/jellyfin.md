---
title: Elf Hosted Jellyfin Accounts 🧝 from $0.15/day
slug: Jellyfin
description: Jellyfin is the volunteer-built media solution that puts you in control of your media. Stream to any device from your own server, with no strings attached.
works_with:
- Jellyseerr
- Jellyfin-Accounts
- NextPVR
- xTeVe
upstream: https://jellyfin.org
links:
- name: subreddit
  uri: https://www.reddit.com/r/jellyfin/
price: 0.15
---

# {{ page.meta.slug }}

Jellyfin is the volunteer-built media solution that puts you in control of your media. Stream to any device from your own server, with no strings attached.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

When you first connect, you'll be prompted to configure your admin account, setup your libraries, etc.

### Enable Hardware transcoding

Our nodes support Intel QuickSync for Video (QSV). Enable this under the admin dashboard's Playback settings.

### From media players

When you configure the Jellyfin app in your media player, use `https://<username>-jellyfin.elfhosted.com` as the address (*if a port is required, use `443`*)

## Solutions to common issues

### Playback stalls

Jellyfin may be trying to transcode the media, based on a detected incompatibilty with your client/app, and running into CPU limitations. For optimal performance and quality, try to direct-play media where possible. You could also try enabling hardware transcoding (*above*), which will improve transcoding performance.

{% include 'app_footer.md' %}