---
title: Elf Hosted Emby 🧝
description: Emby brings all of your home videos, music, and photos together into one place.
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
price: 0.15
---

# {{ page.meta.slug }}

Emby - Bringing all of your home videos, music, and photos together into one place has never been easier.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

When you first connect, you'll be prompted to configure your admin account, setup your libraries, etc.

### Enable Hardware transcoding

Our nodes support Intel QuickSync for Video (QSV). Enable this under the admin dashboard's Playback settings. Note that Emby Premier is required to enable hardware transcoding.

### From media players

When you configure the Emby app in your media player, use `https://<username>-emby.elfhosted.com:443` as the address (*if a port is required, use `443`*)

### Using Emby Connect

Optionally, you can use Emby Connect to simplify the connection to your server from various apps. There are a few extra steps required to inform Emby Connect of the external URL to your server (*because we use a reverse proxy, Emby doesn't "know" what its URL is..*)

Under `Server -> Network`, set the following:

* Public HTTPS port number : `443`
* External domain: `<your username>-emby.elfhosted.com`
* Secure connection mode: `Handled by reverse proxy`

Illustrated below:

![](/images/emby-connect-setup.png)

When accessing the server dashboard, the `Remote (WAN) access` should now be identified as `https://<your username>-emby.elfhosted.com:443`, and Emby Connect should work.

## Solutions to common issues

### Playback stalls

Emby may be trying to transcode the media, based on a detected incompatibilty with your client/app, and running into CPU limitations. For optimal performance and quality, try to direct-play media where possible. You could also try enabling hardware transcoding (*above*), which will improve transcoding performance, provided you have an Emby Premier subscription.

{% include 'app_footer.md' %}