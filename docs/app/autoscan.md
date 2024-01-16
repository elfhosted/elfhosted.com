---
title: Autoscan bundled free with Plex/Jellyfin/Emby
slug: Autoscan
description: Autoscan works with the Arrs to trigger Plex/Jellyfin/Emby to scan targeted folders when new media has been added
works_with:
- Radarr
- Sonarr
- Lidarr
- Readarr
upstream: https://github.com/Cloudbox/autoscan
sponsorship: 
- name: GitHub Sponsors
  uri: https://github.com/sponsors/l3uddz
---

# {{ page.meta.slug }}

Autoscan replaces the default Plex and Emby behaviour for picking up file changes on the file system. Autoscan integrates with [Sonarr][sonarr], [Radarr][radarr], [Readarr][readarr] and [Lidarr][lidarr] to fetch changes in near real-time without relying on the file system.

Autoscan is bundled **FREE** with your ElfHosted streamer (*[Plex][plex], [Jellyfin][jellyfin], or [Emby][emby]*), and pre-setup in the Arrs.

## How do I use it?

### Configure autoscan

Using [FileBrowser][filebrowser], navigate to `/config/autoscan`, and edit `config.yml`.

Uncomment your streamer of choice, and enter in an API token / key as described below.

After changing the autoscan config, restart autoscan using [ElfBot][elfbot], by running `elfbot restart autoscan`.

### Setup Aars 

Configure your Aars (*if they predate our preconfiguring*) by adding a new webhook connection in **Settings** -> **Connect**, with only the following parameters (*see [here][connect-apps] for arr-specific details*)

* **Name**: Autoscan
* **Notification Triggers**:
    * **On Import**
    * **On Upgrade**
* **URL**: `http://autoscan:3030/triggers/<name of app>`

Here's an example:

![](/images/autoscan-arr-example.png)

### Setup Streamers

#### Plex

Follow [these instructions](https://www.plexopedia.com/plex-media-server/general/plex-token/) to retrieve your Plex token, and paste it into the appropriate place in `config.yml`

#### Jellyfin

Navigate to **Advanced > Scheduled Tasks**, and disable the "Scan Media Library" task.

Navigate to **Advanced > Api Keys** in your Jellyfin dashboard, create a new API key for autoscan, and paste it into the appropriate place in `config.yml`

#### Emby

Navigate to **Advanced > Scheduled Tasks**, and disable the "Scan Media Library" task.

Navigate to **Advanced > Api Keys** in your Emby dashboard, create a new API key for autoscan, and paste it into the appropriate place in `config.yml`

## How do I know it's working?

You should be able to test the webhook in the Aars, which will confirm that you've setup the connection correctly.

To confirm that Autoscan is working as intended, examine `/config/autoscan/activity.log` in Filebrowser.

{% include 'app_footer.md' %}