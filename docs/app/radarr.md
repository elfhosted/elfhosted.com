---
slug: Radarr
description: Radarr is a movie collection manager for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new movies and will interface with clients and indexers to grab, sort, and rename them
upstream: https://radarr.video/
links:
- name: subreddit
  uri: https://www.reddit.com/r/radarr
- name: wiki
  uri: https://wiki.servarr.com/radarr
- name: GitHub
  uri: https://github.com/Radarr/Radarr
works_with:
- Deluge
- Emby
- Gotify
- Jellyfin
- NZBGet
- Plex
- qBittorrent
- ruTorrent
- SABnzbd
---

# {{ page.meta.slug }}

Radarr is a movie collection manager for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new movies and will interface with clients and indexers to grab, sort, and rename them.

It can also be configured to automatically upgrade the quality of existing files in the library when a better quality format becomes available.

{% include 'app.md' %}
{% include 'app_access.md' %}

## HD and 4K Libraries

Radarr isn't able to keep multiple copies of the same movie in different formats - it tries to upgrade a lower-quality format when a higher-quality one becomes available. It's sometimes desirable to keep multiple versions in your storage though, so that [Plex][plex] / [Jellyfin][jellyfin] / [Emby][emby] can prompt you which version you'd like to play.

To this end, a "4K" version of Radarr is available, which can either be manually managed, or configured to sync with the "regular" (HD) Radarr.

{% include 'app_footer.md' %}