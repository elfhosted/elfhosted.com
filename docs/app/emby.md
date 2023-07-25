---
slug: Emby
works_with:
- Overseerr
- Jellyseerr
- NextPVR
- xTeVe
upstream: https://emby.media
links:
- name: subreddit
  uri: https://www.reddit.com/r/emby
---

# {{ page.meta.slug }}

Emby - Bringing all of your home videos, music, and photos together into one place has never been easier.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

When you first connect, you'll be prompted to configure your admin account, setup your libraries, etc.

### Enable Hardware transcoding

Our nodes support Intel QuickSync for Video (QSV). Enable this under the admin dashboard's Playback settings.

### From media players

When you configure the Emby app in your media player, use `https://<username>-emby.elfhosted.com` as the address (*if a port is required, use `443`*)

## Solutions to common issues

### Playback stalls

Emby may be trying to transcode the media, based on a detected incompatibilty with your client/app, and running into CPU limitations. For optimal performance and quality, try to direct-play media where possible. You could also try enabling hardware transcoding (*above*), which will improve transcoding performance.

{% include 'app_footer.md' %}