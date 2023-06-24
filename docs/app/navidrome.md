---
slug: Navidrome
description: Navidrome allows you to enjoy your music collection from anywhere, by making it available through a modern Web UI and through a wide range of third-party compatible mobile apps, for both iOS and Android devices
upstream: https://www.navidrome.org
links:
- name: subreddit
  uri: https://www.reddit.com/r/navidrome
---

# {{ page.meta.slug }}

Navidrome allows you to enjoy your music collection from anywhere, by making it available through a modern Web UI and through a wide range of third-party compatible mobile apps, for both iOS and Android devices.

{% include 'app.md' %}
{% include 'app_access.md' %}

### From mobile apps

Connect your subsonic-compatible app to `https://<username>.navidrome.elfhosted.com`

## Where's my music?

Navidrome will automatically index and display music from the `/storage/elfhosted/music` folder. To change the target folder, create `/config/navidrome/navidrome.toml`, and populate with the [desired configuration options](https://www.navidrome.org/docs/usage/configuration-options/#basic-configuration). Use [ElfBot][elfbot] to restart Navidrome after saving changes.

{% include 'app_footer.md' %}