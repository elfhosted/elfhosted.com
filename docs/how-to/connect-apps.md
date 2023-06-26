# Inter-app Communication

While each app is reachable externally as `https://<username>.<app name>.elfhosted.com`, winith your namespace, each app is reachable to each other app on its own hostname and port, as described below.

You may need these details when configuring inter-app communication, like connecting [Radarr](/Apps/Radarr) to [Plex](/Apps/Plex), or [Autobrr](/Apps/Autobrr) to [Deluge](/Apps/Deluge)..

## [Calibre][calibre]

* host: `calibre`
* port:`8081`
* username: `calibre`
* password: `calibre`

*already preconfigured in Readarr*

## [Deluge][deluge]

* host: `deluge`
* ui
	* port:`8081` (*for Arr apps*)
	* credentials: `deluge`
 
* daemon
  * port: `58846` (*for Autobrr, use type "Deluge 2"*)
  * user: `autobrr`
  * password: `c7RJKKt#KBcM5Z?a`

## [Emby][emby]

* host: `emby`
* port: `8096`


## [Flaresolverr][flaresolverr]

* host: `flaresolverr`
* port: `8191`
  
## [Jellyfin][jellyfin]

* host: `jellyfin`
* port: `8096`

## [Lidarr][lidarr]

* host: `lidarr`
* port: `8686`
* credentials: `(get api key from UI at Settings -> General)`

## [NextPVR][nextpvr]

* host: `nextpvr`
* port: `8866`

In Plex, use `nextpvr:8866` as your HDHomeRun network address

## [NZBGet][nzbget]

* host: `nzbget`
* port: `6789`
* credentials: `<none>`

## [Plex][plex]

* host: `plex`
* port: `32400`
  
## [Prowlarr][prowlarr]

* host: `prowlarr`
* port: `9696`
* credentials: `(get api key from UI at Settings -> General)`

Preconfigured in Radarr/Sonarr/Lidarr/Readarr/Mylarr

## [qBittorrent][qbittorrent]

* host: `qbittorrent`
* port: `8080`
* credentials: `admin/adminadmin` (shouldn't be required)

## [Radarr][radarr]

* host: `radarr` (*or `radarr4k`*)
* port: `7878`
* credentials: `(get api key from UI at Settings -> General)`

## [Readarr][readarr]

* host: `readarr` (*or `readarraudio`*)
* port: `8787`
* credentials: `(get api key from UI at Settings -> General)`

## [ruTorrent][rutorrent]

* host: `rutorrent`
* port: `8080`
* path: `plugins/rpc/rpc.php`

## [SABnzbd]([sabnzbd]

* host: `sabnzbd`
* port: `8080`
* api key: `(get from sabnzbd under Config -> Genoral)`

## [Sonarr][sonarr]

* host: `sonarr`  (*or `sonarr4k`*)
* port: `8989`
* credentials: `(get api key from UI at Settings -> General)`

## [xTeVe][xteve]

* host: `xteve`
* port: `34400`

In Plex, use `xteve:34400` as your HDHomeRun network address