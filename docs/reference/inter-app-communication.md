# Inter-app Communication

While each app is reachable externally as `https://<username>.<app name>.elfhosted.com`, winith your namespace, each app is reachable to each other app on its own hostname and port, as described below.

You may need these details when configuring inter-app communication, like connecting [Radarr](/Apps/Radarr) to [Plex](/Apps/Plex), or [Autobrr](/Apps/Autobrr) to [Deluge](/Apps/Deluge)..

## [Calibre](/Apps/Calibre)

* host: `calibre`
* port:`8081`
* username: `calibre`
* password: `calibre`

*already preconfigured in Readarr*

## [Deluge](/Apps/Deluge)

* host: `deluge`
* ui
	* port:`8081` (*for Arr apps*)
	* credentials: `deluge`
 
* daemon
  * port: `58846` (*for Autobrr, use type "Deluge 2"*)
  * user: `autobrr`
  * password: `c7RJKKt#KBcM5Z?a`
  
## [Deluge (Public)](/Apps/Deluge)

> This is an instance of Deluge intended for use with public trackers. Slower than the default, whitelisted-private-tracker-only instance of Deluge, but unrestricted.
{.is-warning}


* host: `delugepublic`
* ui
	* port:`8081` (*for Arr apps*)
	* credentials: `deluge`
 
* daemon
  * port: `58846` (*for Autobrr, use type "Deluge 2"*)
  * user: `autobrr`
  * password: `c7RJKKt#KBcM5Z?a`

## [Emby](/Apps/Emby)

* host: `emby`
* port: `8096`


## [Flaresolverr](/Apps/Flaresolverr)

* host: `flaresolverr`
* port: `8191`
  
## [Jellyfin](/Apps/Jellyfin)

* host: `jellyfin`
* port: `8096`

## [Lidarr](/Apps/Lidarr)

* host: `lidarr`
* port: `8686`
* credentials: `(get api key from UI at Settings -> General)`

## [NextPVR](/Apps/NextPVR)

* host: `nextpvr`
* port: `8866`

In Plex, use `nextpvr:8866` as your HDHomeRun network address

## [NZBGet](/Apps/NZBGet)

* host: `nzbget`
* port: `6789`
* credentials: `<none>`

## [Plex](/Apps/Plex)

* host: `plex`
* port: `32400`
  
## [Prowlarr](/Apps/Prowlarr)

* host: `prowlarr`
* port: `9696`
* credentials: `(get api key from UI at Settings -> General)`

Preconfigured in Radarr/Sonarr/Lidarr/Readarr/Mylarr

## [qBittorrent](/Apps/qBittorrent)

* host: `qbittorrent`
* port: `8080`
* credentials: `admin/adminadmin` (shouldn't be required)

## [qBittorrent (Public)](/Apps/qBittorrent)

> This is an instance of qBittorrent intended for use with public trackers. Slower than the default, whitelisted-private-tracker-only instance of qBittorrent, but unrestricted.
{.is-warning}

* host: `qbittorrentpublic`
* port: `8080`
* credentials: `admin/adminadmin` (shouldn't be required)

## [Radarr](/Apps/Radarr)

* host: `radarr`
* port: `7878`
* credentials: `(get api key from UI at Settings -> General)`

## [Readarr](/Apps/Readarr)

* host: `readarr`
* port: `8787`
* credentials: `(get api key from UI at Settings -> General)`

## [ruTorrent](/Apps/ruTorrent)

* host: `rutorrent`
* port: `8080`
* path: `plugins/rpc/rpc.php`

## [ruTorrent Public](/Apps/ruTorrent)

> This is an instance of ruTorrent intended for use with public trackers. Slower than the default, whitelisted-private-tracker-only instance of ruTorrent, but unrestricted.
{.is-warning}

* host: `rutorrent`
* port: `8080`
* path: `plugins/rpc/rpc.php`

## [SABnzbd](/Apps/SABnzbd)

* host: `sabnzbd`
* port: `8080`
* api key: `(get from sabnzbd under Config -> Genoral)`

## [Sonarr](/Apps/Sonarr)

* host: `sonarr`
* port: `8989`
* credentials: `(get api key from UI at Settings -> General)`

## [xTeVe](/Apps/xTeVe)

* host: `xteve`
* port: `34400`

In Plex, use `xteve:34400` as your HDHomeRun network address