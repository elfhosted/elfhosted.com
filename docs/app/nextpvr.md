---
slug: NextPVR
description: NextPVR provides IPTV support for Jellyfin/Emby/Plex
upstream: https://nextpvr.com/
links:
- name: forum
  uri: https://forums.nextpvr.com/
- name: wiki
  uri: https://github.com/sub3/NextPVR/wiki
---

# {{ page.meta.slug }}

NextPVR provides IPTV support for [Jellyfin][jellyfin] / [Emby][emby] / [Plex][plex]

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

The default login is:

* Username: `admin`
* Password: `ireadthedocs`

See [here][connect-apps] for details re connecting to Jellyfin / Emby / Plex

## Can I save recordings?

No, you can't currently. Although NextPVR _thinks_ it has access to a `/recordings` and `/buffers` folder, these are simply tmpfs folders, limited to 1GB, and exceeding them will cause the pod to restart.

{% include 'app_footer.md' %}