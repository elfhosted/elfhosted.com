---
slug: Sonarr
description: Sonarr is a PVR for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them
upstream: https://sonarr.tv/
links:
- name: wiki
  uri: https://wiki.servarr.com/sonarr
- name: subreddit
  uri: https://www.reddit.com/r/Sonarr
---

# {{ page.meta.slug }}

Sonarr is a PVR for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them. 

It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available. 

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

Once you've enabled it in [your account](https://elfhosted.com/tenant/apps/0), launch the app via your dashboard.

Sonarr will be pre-configured for the other supported apps. By default, Sonarr HD is configured to seek out only 1080P content which can reliably be direct-played / transcoded on a range of equipment and bandwidth constraints. If you have the hardware / bandwidth to direct-play 4K content, you'll need to update the profiles yourself.

!!! warning
    Be aware that our platform won't transcode 4K content for you reliably!

{% include 'app_footer.md' %}