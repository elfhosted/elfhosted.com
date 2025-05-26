---
title: Hosted YourIPTV for Stremio
slug: Wizarr
description: YourIPTV is a Stremio Addon which lets you watch your paid IPTV streams in Stremio
upstream: https://docs.wizarr.dev/
links:
- name: GitHub
  uri: https://github.com/wizarrrr/wizarr
- name: Discord
  uri: https://discord.gg/Wwaceqha
sponsorship: 
- name: GitHub Sponsors
  uri: https://github.com/sponsors/mtthidoteu
works_with:
- Plex
- Jellyfin
- Emby
- Ombi
- Overseerr
- Jellyseerr
---

# {{ page.meta.slug }}

Wizarr is an automatic user invitation system for Plex, Jellyfin, and Emby.
Create a unique invite link and share it with users — they’ll be automatically added to your media server and guided through downloading apps, accessing request systems, and more!

The problem: Inviting your Friends/Family to your Plex server Is complicated and tedious. It's also a hard concept for them to get their head around.

The solution: Wizarr makes it easy to invite users to your server by simply sending them a link, and guides them through the process of getting set up.

{% include 'app.md' %}

Features:

* 🤖 Automatic invitations for [Plex][plex], [Jellyfin][jellyfin], and [Emby][emby]
* 🔒 Secure, user-friendly invitation process
* 🏷️ Multi-tiered invitation access
* ⏳ Time-limited membership options
* 📖 Setup guide for media apps (like Plex)
* 📬 Request system integration ([Overseerr][overseerr], [Ombi][ombi], etc.)
* 💬 Discord invite support

{% include 'app_access.md' %}

## How to use 

Upon first setup, you're asked to configure your streamer server

### With Plex

* Server Name: `ElfHosted`
* Server Type: `Plex`
* Server URL: `http://plex:32400`
* API Key: [token you generated][plex-token]
* Overseerr/Ombi URL: Set to the **public** URL of your Overseerr / Ombi

### With Jellyfin

* Server Name: `ElfHosted`
* Server Type: `Jellyfin`
* Server URL: `http://jellyfin:8086`
* API Key: API Key generated within Jellyfin
* Overseerr/Ombi URL: Set to the **public** URL of your Overseerr / Ombi

### With Emby

* Server Name: `ElfHosted`
* Server Type: `Emby`
* Server URL: `http://emby:8086`
* API Key: API Key generated within Emby
* Overseerr/Ombi URL: Set to the **public** URL of your Overseerr / Ombi

{% include 'app_footer.md' %}