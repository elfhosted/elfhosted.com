---
slug: Plex
description: Plex is a power media player with support across a large range of platforms
works_with:
- Ombi
- Overseerr
- Tautulli
upstream: https://plex.tv
links:
- name: subreddit
  uri: https://www.reddit.com/r/plex
---

# {{ page.meta.slug }}

Plex is a power media player with support across a large range of platforms

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

Use [ElfBot][elfbot] to apply your [plex claim](https://www.plex.tv/claim/), and reboot. Then access Plex from your dashboard.

You'll be prompted to setup your libraries, etc.

### From media players

When you configure the Plex app in your media player, use `https://<username>.plex.elfhosted.com` as the address (*if a port is required, use `443`*)

### Enable Hardware transcoding

Our nodes support Intel QuickSync for Video (QSV). If you're a PlexPass user, you can enable hardware transcoding.

## Solutions to common issues

### Playback stalls

Plex may be trying to transcode the media, based on a detected incompatibilty with your client/app, and running into CPU limitations. For optimal performance and quality, try to direct-play media where possible. You could also try enabling hardware transcoding (*above*), which will improve transcoding performance.

{% include 'app_footer.md' %}