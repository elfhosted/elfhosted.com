---
title: Stream from real-debrid with Zurg
slug: Zurg
description: Zurg is middleware, half of a clever solution which lets you stream from Real Debrid directly using Plex, Emby, or Jellyfin
upstream: https://github.com/debridmediamanager/zurg-testing
works_with:
- plex
- jellyfin
- emby
sponsorship:
- name: GitHub Sponsors
  uri: https://github.com/sponsors/debridmediamanager
- name: Patreon
  uri: https://www.patreon.com/debridmediamanager
- name: PayPal
  uri: https://www.paypal.com/paypalme/yowmamasita
---

# {{ page.meta.slug }}

Zurg is middleware, half of a clever solution which lets you stream from [Real-Debrid][real-debrid] directly using [Plex][plex], [Emby][emby], or [Jellyfin][jellyfin].

It works like this - you give Zurg your [Real-Debrid API token](https://real-debrid.com/apitoken), and a bunch of regular expressions (*regexes*) explaining roughly what filenames match to what kind of content.

[Step #1: Add Zurg to your ElfHosted apps](https://store.elfhosted.com/product/zurg/){ .md-button .md-button--primary }

Zurg then scrapes your Real-Debrid account, applies the regexes, and presents a WebDAV endpoint to "browse" your files. You can confirm the folder structure by browsing `https://<your username>-zurg.elfhosted.com`, and adjust the regexes at `https://<your username>-filebrowser.elfhosted.com/files/config/zurg/config.yml`. 

Use [ElfBot][elfbot] to restart Zurg if you make any changes to the config file.

Next, purchase an pre-prepared zurg WebDAV mount - we'll attach the zurg-exposed WebDAV URL to your apps at `/storage/real-debrid-zurg`.

[Step #2: Add a Zurg mount to your ElfHosted apps](https://store.elfhosted.com/product/rclone-real-debrid/){ .md-button .md-button--primary }

 Now, in `/storage/real-debrid-zurg`, you'll find directories matching the regexes you defined (*"movies", "tv", "music", etc*). 
 
 If you add `/storage/real-debrid-zurg` to your Plex / Jellyfin / Emby libraries, suddenly you can stream from Real-Debrid as if the media were locally attached, without any delay for download / transfer, etc! 

## Access zurg externally via WebDAV

If you'd rather just use Zurg's WebDAV endpoint, and attach to your existing clients, you can "expose" Zurg using basic auth (user/password). Add the "[Zurg Exposed](https://store.elfhosted.com/product/zurg-exposed)" product to your subscription, choosing a secure password.

Your Zurg instance will now be available via WebDAV on `https://<username>-zurg.elfhosted.com/dav/`

To change your username/password, edit `config/zurg/config.yml` via [FileBrowser][filebrowser], and then trigger a Zurg restart using [ElfBot][elfbot].

--8<-- "common-links.md"