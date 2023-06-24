---
slug: Readarr
description: Readarr is a ebook collection manager for Usenet and BitTorrent users
upstream: https://wiki.servarr.com/readarr
links:
- name: subreddit
  uri: https://www.reddit.com/r/radarr
- name: GitHub
  uri: https://github.com/Radarr/Readarr
works_with:
- Audiobookshelf
- Calibre
- Calibre-Web
- Deluge
- Gotify
- NZBGet
- qBittorrent
- ruTorrent
- SABnzbd
---

# {{ page.meta.slug }}

Readarr is a ebook collection manager for Usenet and BitTorrent users.

It can monitor multiple RSS feeds for new books from your favorite authors and will interface with clients and indexers to grab, sort, and rename them.

{% include 'app.md' %}
{% include 'app_access.md' %}

## Calibre Integration

If [Calibre][calibre] is purchased along with Readarr, then Readarr will automatically send new downloads to Calibre, to be processed and become available in [Calibre-Web][calibre-web].

## eBook and Audio libraries

The Calibre integration described above can result in errors / messy libraries when using Readarr to source audio books (*since Calibre can't process audio books*). At the same time, Readarr isn't capable of saving the **audio** version of a book in a separate root folder to the **ebook** version. 

The cleanest solution is to run a second Readarr app, dedicated to audiobooks (*no need to send to Calibre*). When purchasing Readarr via the store, the options for ebook / audiobook versions are available.

{% include 'app_footer.md' %}