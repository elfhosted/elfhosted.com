---
title: Elf Hosted qBittorrent 🧝 from $0.05/day
slug: qBittorrent
description: The qBittorrent project aims to provide an open-source software alternative to µTorrent
upstream: https://www.qbittorrent.org
links:
- name: subreddit
  uri: https://www.reddit.com/r/qBittorrent
works_with:
- Deluge
- LazyLibrarian
- NZBGet
- Radarr
- Readarr
- ruTorrent
- SABnzbd
- Sonarr
price: 0.10
sponsorship:
- name: www.qbittorrent.org/donate
  uri: https://www.qbittorrent.org/donate
---

# {{ page.meta.slug }}

The qBittorrent project aims to provide an open-source software alternative to µTorrent.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it ?

### Can I use public trackers?

{% include 'faq_public_trackers.md' %}

{% include 'faq_use_mam.md' %}

### Alternate themes

Our qBittorrent apps include the popular [VueTorrent](https://github.com/WDaan/VueTorrent) alternative theme, which can be enabled in by setting "Use alternative Web UI" to `/vuetorrent` as illustrated below:

![Set alternative WebUI in qBittorrent](/images/qbittorrent-vuetorrent.png)

### Using ephemeral /tmp

qBittorrent can be configured to download torrents to one location, and then move them to another location upon completion. This can alleviate disk I/O constraints during the initial download process, speeding up the overall download and reducing resource usage.

Our qBittorrent pods are provisioned with a 1TB, HDD-backed, ephemeral `/tmp` volume. Ephemeral volumes only exist for as long as the pod is running, and so while unsuitable for long-term storage (*because they are recreated upon restart*), they are ideal for temporary, I/O-heavy operations like torrenting, unpacking, uncompressing, etc.

To use the 1TB ephemeral `/tmp` volume with qBittorrent, configure **Options** -> **Downloads** -> **Keep incomplete torrents in** to `/tmp`, as illustrated below:

![Using /tmp in qBittorrent](/images/qbittorrent-ephemeral-tmp.png)

!!! question "What happens if my pod restarts before a download is completed?"
    Then the contents of `/tmp` will be lost. Restarts will be infrequent, occurring at most once during the maintenance window. Provided you don't have any in-progress torrents when this happens, you won't be affected. This design won't suit users who download large torrent files with few seeders over several days, but it does offer considerable advantages to speeding up small, discrete downloads.

{% include 'app_footer.md' %}