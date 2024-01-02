---
title: Elf Hosted ruTorrent 🧝 from $0.10/day
slug: ruTorrent
description: ruTorrent is a popular Bittorrent client for power users, which includes the unique ability (among our torrent apps) to create torrents from its web UI.
upstream: https://github.com/Novik/ruTorrent
links:
works_with:
- LazyLibrarian
- Mylar
- Radarr
- Readarr
- Sonarr
price: 0.10
---

# {{ page.meta.slug }}

ruTorrent is a popular Bittorrent client for power users, which includes the unique ability (*among our torrent apps*) to create torrents from its web UI.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it ?

### Set inbound port

If you're using Private Internet Access, or ProtonVPN, then your inbound port will be automatically configured for you.

If you're using a different VPN provider, you may need to manually configure a port assigned to you by your VPN provider. In this case, use [FileBrowser][filebrowser] to create `/config/rutorrent/forwarded-port-override`, populated with the port number you'd like rtorrent to listen on.

For example, for port 40000, you'd ensure that this file contained only the string `40000`.

Restart rutorrent using [ElfBot][elfbot], and the port will be fixed at the one you specified.

### Make permanent config changes

ruTorrent (*really, rtorrent*) can be tricker to customize than our other torrent clients. The GUI allows you to make some temporary changes, but to effect permanent changes, use [FileBrowser][filebrowser] to edit the config file at `config/rutorrent/.rtorrent.rc`.

#### Set rtorrent download path

In `config/rutorrent/.rtorrent.rc`, you'll find config like this:

```
    method.insert = cfg.basedir, private|const|string, (cat,"/data/rtorrent/")
    method.insert = cfg.download, private|const|string, (cat,"/storage/elfstorage/downloads/")
    method.insert = cfg.download_complete, private|const|string, (cat,(cfg.download),"completed/")
```

To change the default ruTorrent download path, replace `/storage/elfstorage/downloads/` in the config above with your target directory, and restart ruTorrent using [ElfBot][elfbot]

### Using ephemeral /tmp

ruTorrent can be configured to download torrents to one location, and then move them to another location upon completion. This can alleviate disk I/O constraints during the initial download process, speeding up the overall download and reducing resource usage.

Our ruTorrent pods are provisioned with a 1TB, HDD-backed, ephemeral `/tmp` volume. Ephemeral volumes only exist for as long as the pod is running, and so while unsuitable for long-term storage (*because they are recreated upon restart*), they are ideal for temporary, I/O-heavy operations like torrenting, unpacking, uncompressing, etc.

To use the 1TB ephemeral `/tmp` volume with rutorrent, use [FileBrowser][filebrowser] to edit the config file at `config/rutorrent/.rtorrent.rc`, and uncomment this line:

```
    # directory.default.set = (cat,(cfg.download_temp))
```

Comment out this line:

```
    directory.default.set = (cat,(cfg.download_complete))
```

And finally, uncomment the highlighted lines below:

``` hl_lines="2-4"
    # Move finished (no need Autotools/Automove plugin on ruTorrent)
    # method.insert = d.get_finished_dir, simple, "cat=$cfg.download_complete=,$d.custom1="
    # method.insert = d.move_to_complete, simple, "d.directory.set=$argument.1=; execute=mkdir,-p,$argument.1=; execute=mv,-u,$argument.0=,$argument.1=; d.save_full_session="
    # method.set_key = event.download.finished,move_complete,"d.move_to_complete=$d.data_path=,$d.get_finished_dir="
```

Restart ruTorrent using [ElfBot][elfbot] - now new downloads will go to `/tmp`, and upon completion, they'll be moved to the permanent location you specified in `cfg.download` above.

!!! question "What happens if my pod restarts before a download is completed?"
    Then the contents of `/tmp` will be lost. Restarts will be infrequent, occurring at most once during the maintenance window. Provided you don't have any in-progress torrents when this happens, you won't be affected. This design won't suit users who download large torrent files with few seeders over several days, but it does offer considerable advantages to speeding up small, discrete downloads.

{% include 'faq_use_mam.md' %}
{% include 'app_footer.md' %}