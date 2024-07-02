---
title: Elf Hosted plex_debrid 🧝 from $0.10/day
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
price: 0.10
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

### Edit settings.json

Plex_debrid is unusual in that it requires a CLI-based UI. For this reason, we run it within a xterm.js-based browser session.

Your plex_debrid config is stored in `config/plex-debrid/settings.json` - While you can edit most options using the CLI UI, the easiest way to get started is to manually edit it and make the required changes, as illustrated below:

### Add Plex Token

You'll need a plex token to allow Plex_debrid to scrape your watchlist, and to interact with your libraries.

See [this guide][plex-token] to get your Plex token.

Copy the token, and paste the value into `settings.json` as illustrated below:

```` json hl_lines="10" linenums="1"
    {
        "Content Services": [
            "Plex",
            "Trakt",
            "Overseerr"
        ],
        "Plex users": [
            [
                "your-username",
                "replace-me-with-plex-token"
            ]
        ],
````

!!! tip
    You can change the username, this is just used for reference within Plex Debrid, in case you have more than one user's watchlist to watch

### Add Debrid API key

Next, you'll need to add your Debrid provider's API key. Again in `settings.json`, add your key to the appropriate provider, as illustrated below:

```` json hl_lines="1" linenums="284"
    "Real Debrid API Key": "your-key-here",
    "All Debrid API Key": "",
    "Premiumize API Key": "",
    "Debrid Link API Key": "",
    "Put.io API Key": "",
````

### Restart Plex_debrid

The above (*Plex token and Debrid API key*) are the **minimal** changes necessary. To apply your changes, restart Plex_debrid by running `elfbot restart plex-debrid` in the [FileBrowser][filebrowser] console.

### Setup Zurg's updateplex.sh

To trigger a Plex library update from Zurg when your Real-Debrid content changes, edit `config/zurg/plex_update.sh` via [FileBrowser][filebrowser], find this line:

```
token="yourplextoken"
```

And replace `yourplextoken` with the same plex token you used when configuring plex_debrid.

## Troubleshooting

### RGB codes on console

Due to an as-yet-unsolved bug with the Wetty / xterm.js deployment, newly created sessions will sometimes include lots of control characters outputted to the screen. The simplest way to make these go away for the duration of the session is to just hit `ENTER`, which will refresh the screen and prevent further issuses.

{% include 'app_footer.md' %}