---
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
---

# {{ page.meta.slug }}

Jellyfin is the volunteer-built media solution that puts you in control of your media. Stream to any device from your own server, with no strings attached.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

When you first connect, you'll be prompted to configure your admin account, setup your libraries, etc.

### From media players

When you configure the Jellyfin app in your media player, use `https://<username>.jellyfin.elfhosted.com` as the address (*if a port is required, use `443`*)

{% include 'app_footer.md' %}