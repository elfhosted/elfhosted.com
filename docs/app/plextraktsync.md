---
title: Elf Hosted PlexTraktSync 🧝
slug: PlexTraktSync
description: PlexTraktSync adds a two-way-sync between trakt.tv and Plex Media Server
upstream: https://github.com/Taxel/PlexTraktSync
---

# {{ page.meta.slug }}

PlexTraktSync adds a two-way-sync between trakt.tv and Plex Media Server. This app is a standalone instance, which runs continuously in "watch" mode, as opposed to the one-time "sync" mode built into ElfTerm.

!!! note
    If you don't **need** continuous sync, you can simple use the `plextraktsync` command built into [ElfTerm][elfterm]

{% include 'app.md' %}
{% include 'app_access.md' %}

## How to use PlexTraktSync

### Updating server URL

The first time PlexTraktSync runs, it'll create a `servers.yml` file based on the known servers in your Plex account. In our case, your server is **always** addressed on `http://plex:32400`, so you'll need to edit `config/plextraktsync/servers.yml` using ]FileBrowser][filebrowser], and replace the automatic collection of URLs with **just** `http://plex:32400`

{% include 'app_footer.md' %}
