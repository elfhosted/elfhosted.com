---
title: Plex hosting with hardware transcoding for $0.15/day
slug: Plex
description: ElfHosted provides simple Plex hosting - including hardware transcoding
works_with:
- Ombi
- Overseerr
- Tautulli
upstream: https://plex.tv
links:
- name: subreddit
  uri: https://www.reddit.com/r/plex
price: 0.15
---

# {{ page.meta.slug }}

Plex is a power media player with support across a large range of platforms

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

Use [ElfBot][elfbot] to apply your [plex claim](https://www.plex.tv/claim/), and reboot. Then access Plex from your dashboard.

You'll be prompted to setup your libraries, etc.

### From media players

When you configure the Plex app in your media player, use `https://<username>-plex.elfhosted.com` as the address (*if a port is required, use `443`*)

### Enable Hardware transcoding

Our nodes support Intel QuickSync for Video (QSV). If you're a PlexPass user, you can enable hardware transcoding.

## Solutions to common issues

### Playback stalls

Plex may be trying to transcode the media, based on a detected incompatibilty with your client/app, and running into CPU limitations. For optimal performance and quality, try to direct-play media where possible. You could also try enabling hardware transcoding (*above*), which will improve transcoding performance.

### Database is corrupt

Certain unplanned events (power outages, etc) can result in Plex's database becoming corrupted. Fortunately, Plex makes its own, internal backup of its database at regular intervals, so it's possible to restore from a backed-up version of the database.

Here's the process to restore Plex to a database backup:

1. "Pause" Plex, using [ElfBot][elfbot]
2. In [FileBrowser][filebrowser], navigate to `config/plex/Library/Application Support/Plex Media Server/Plug-in Support/Databases`
3. Rename `com.plexapp.plugins.library.db` to `com.plexapp.plugins.library.db-corrupt`, and then pick the most recent, dated version of `com.plexapp.plugins.library.db-<date>`, and rename it to `com.plexapp.plugins.library.db`.

When Plex starts after the pause, the backup database will be used! :thumbsup:

{% include 'app_footer.md' %}