---
title: Elf Hosted NZBHydra
slug: NZBHydra
description: NZBGet is an efficient usenet downloader
upstream: https://github.com/theotherp/nzbhydra2
---

# {{ page.meta.slug }}

NZBHydra 2 is a meta search for newznab indexers and torznab trackers. It provides easy access to newznab indexers and many torznab trackers via [Jackett[jackett]]. 

You can search all your indexers and trackers from one place and use it as an indexer source for tools like [Sonarr][sonarr], [Radarr][radarr] or [Lidarr][lidarr].

NZBHydra is a supported external search integration for [TorBox](https://torbox.app), and is a popular choice for TorBox user who require NZB searching capabilities to "bolt onto" their TorBox subscription.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### Authorization

Configuring authorization is not required, since your NZBHydra is protected by your ElfHosted SSO. Any external interactions (i.e., from TorBox) are secured with your own API keyy.

### TorBox

The following illustrates how to setup an ElfHosted NZBHydra instance with TorBox:

![](/images/nzbhydra-torbox.png)

{% include 'app_footer.md' %}