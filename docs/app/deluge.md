---
title: 🧝 Hosted Deluge from $0.15/day
slug: Deluge
description: Deluge is a lightweight, Free Software, cross-platform BitTorrent client
works_with:
- Autobrr
- Lidarr
- Prowlarr
- Radarr
- Readarr
- Sonarr
upstream: https://deluge-torrent.org
price: 0.10
sponsorship: 
- name: Patreon
  uri: https://www.patreon.com/deluge_cas
---

# {{ page.meta.slug }}

Deluge is a lightweight, Free Software, cross-platform BitTorrent client.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### What's the password for Deluge?

The default credentials are:

* password: `deluge`

See [here][connect-apps] for details re connecting with your other apps.

### I can't connect my Arr apps to Deluge

Deluge requires the "Label" plugin for compatibilty with Arr, which is already enabled on our default Deluge config.

### Using ephemeral /tmp

Deluge can be configured to download torrents to one location, and then move them to another location upon completion. This can alleviate disk I/O constraints during the initial download process, speeding up the overall download and reducing resource usage.

Our Deluge pods are provisioned with a 1TB, HDD-backed, ephemeral `/tmp` volume. Ephemeral volumes only exist for as long as the pod is running, and so while unsuitable for long-term storage (*because they are recreated upon restart*), they are ideal for temporary, I/O-heavy operations like torrenting, unpacking, uncompressing, etc.

To use the 1TB ephemeral `/tmp` volume with qBittorrent, configure **Preferences** -> **Downloads** -> **Download to** to `/tmp`, as illustrated below:

![Using /tmp in Deluge](/images/deluge-ephemeral-tmp.png)

!!! question "What happens if my pod restarts before a download is completed?"
    Then the contents of `/tmp` will be lost. Restarts will be infrequent, occurring at most once during the maintenance window. Provided you don't have any in-progress torrents when this happens, you won't be affected. This design won't suit users who download large torrent files with few seeders over several days, but it does offer considerable advantages to speeding up small, discrete downloads.

{% include 'faq_use_mam.md' %}

{% include 'app_footer.md' %}