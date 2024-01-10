---
title: Elf Hosted plex_debrid 🧝 from $0.05/day
slug: Plex-Debrid
description: Plex-debrid "glues" Plex, Zurg, and rclone together, to create an "infinite streaming" solution for Real Debrid
upstream: https://github.com/itsToggle/plex_debrid
links:
- name: Discord server
  uri: https://discord.gg/jMpyFryfaj
works_with:
- Plex
- Jellyfin
- Emby
- Zurg
- Overseerr
- Jellyseerr
price: 0.05
---

# {{ page.meta.slug }}

When combined with [Plex][plex], an rclone mount, and a Debrid service, plex_debrid facilitates "stremio-like" torrent streaming through Debrid Services.

In an ideal situation, you'd add a movie / TV show to your Plex watchlist / Trakt lists, [Overseerr] / [Jellyseerr], and then 10-20s later, it's available to stream it through your Plex instance, as per the upstream demo below:

[Get Elf Hosted {{ page.meta.slug }} from ${{ page.meta.price }}/day :magic_wand:](https://store.elfhosted.com/product/{{ page.meta.slug | lower }}/){ .md-button .md-button--primary }

![Screenshot of {{ page.meta.slug }}](/images/plex-debrid-demo.gif){ loading=lazy }

!!! warning "Advanced use"
    plex_debrid is an advanced and complex tool, you should expect to spend some time troubleshooting!

    Further, if you want to use it with your ElfHosted [Plex][plex] instance, plex_debrid requires an [rclone WebDAV mount](https://store.elfhosted.com/product/rclone-webdav-mount/) to your Debrid service, and if using Real-Debrid, you'll want [Zurg][zurg] plus the [Zurg-specific WebDAV mount](https://store.elfhosted.com/product/rclone-real-debrid/)!

{% include 'app_access.md' %}

## How do I use it ?

### Initial setup

Plex_debrid is unusual in that it requires a CLI-based setup. For this reason, we run it within a VNC-based browser session.

The first time you open plex_debrid, you'll be prompted with the "Initial Setup". Go through the wizard and enter the necessary details as prompted.

ElfHosted-specific config steps are illustrated below:

### Copy / Paste (CTRL-Shift-V)

Using plex_debrid over the VNC browser session can be a PITA. Use `ctrl-shift-v` to paste from your clipboard. Chrome and Edge may be able to copy/paste directly, but Firefox and other browsers require you to use the Kasm "clipboard" to transfer to/from the real_debrid clipboard.

For example, to paste in data from your clipboard, you'd expand the menu on the left-hand side, paste the API token into the clipboard window, and **then** use the "paste" function in the terminal to paste it, as illustrated below:

![Screenshot of {{ page.meta.slug }} copy / paste process](/images/plex-debrid-copy-paste.png){ loading=lazy }

### Connect Plex

When you connect to Plex, use the URL `http://plex:32400`

![Screenshot of {{ page.meta.slug }} connecting to plex](/images/plex-debrid-add-local-plex.png){ loading=lazy }

### Connecting to Overseerr / Jellyseerr

To optionally connect to Jellyseerr / Overseerr, enter their details per [Connecting Apps](/how-to/connect-apps/), as illustrated below:

![Screenshot of {{ page.meta.slug }} connecting to Jellyseerr](/images/plex-debrid-add-overseerr-jellyseerr.png){ loading=lazy }

### Editing / importing config

If you don't want to use the CLI UI to make config changes, you can edit the config directly in [FileBrowser][filebrowser], at `config/plex-debrid/settings.json`. Restart plex-debrid either using [ElfBot][elfbot], or close the terminal window in VNC, then right-click on the desktop and re-launch plex-debrid! :grin:

### Re-launch plex-debrid (blank desktop)

If you accidentally closed plex-debrid, and are now faced with a blank desktop, you can re-launch it by right-clicking anywhere on the blank desktop, and choosing to "re-launch plex-debrid"

If the entire KasmVNC session is **really** broken, you can restart the whole app using [ElfBot][elfbot].

{% include 'app_footer.md' %}