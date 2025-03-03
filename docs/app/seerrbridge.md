---
title: 🧝 Hosted SeerrBridge 📚
slug: SeerrBridge
description: SeerrBridge uses smart symlinking to organize your debrid libraries for tidy streaming from Plex
upstream: https://github.com/Woahai321/SeerrBridge
works_with:
- ListSync
- Overseerr
- Jellyseerr
sponsorship:
- name: GitHub Sponsors
  uri: https://github.com/sponsors/Woahai321
links:
- name: Discord
  uri: https://discord.com/invite/Dy5xNzEHKw
---

# {{ page.meta.slug }}

SeerrBridge is a browser automation tool that integrates Jellyseer/Overseerr with Debrid Media Manager. It listens to movie requests via Overseerr webhook. It automates the torrent search and download process using Debrid Media Manager via browser automation, which in turn, gets sent to Real-Debrid. This streamlines your media management, making it fast and efficient.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How to use SeerrBridge

You'll need some environment variables before you launch SeerrBridge, and even more environment variables to actually make it work!

### Overseerr

Navigate to your Overrseerr, to `Settings` -> `General` and retrieve your API key

### Trakt

Create a Trakt.tv account and sign in
Navigate to <https://trakt.tv/oauth/applications/new> to create a new app

You can use anything (I.e., `https://google.com`) as the redirect URI

![](/images/seerrbridge_trakt_setup.png)

Copy the Client ID (*not the secret!*), which you'll need to provide to SeerrBridge:

![](/images/seerrbridge_trakt_setup_2.png)

### DebridMediaManager

Navigate to https://debridmediamanager.com, and authenticate with RealDebrid.

In your browser, use developer tools to inspect the page, and capture your RealDebrid tokens from local storage, as illustrated below:

![](/images/seerrbridge_dmm_setup.png)

Use the values you find to prepare the following:

```
RD_ACCESS_TOKEN='{"value":"your_token","expiry":123}'
RD_CLIENT_ID=YOUR_CLIENT_ID
RD_CLIENT_SECRET=YOUR_CLIENT_SECRET
RD_REFRESH_TOKEN=YOUR_REFRESH_TOKEN
```

### SeerrBridge

While usually environment variables can be managed via [ElfBot][elfbot], since `RD_ACCESS_TOKEN` contains quotes and spaces, it's simpler and safer to bypass ElfBot, and create a ConfigMap directly in Kubernetes Dashboard.

From Kubernetes Dashboard, click the `+` icon to create a new resource:

![](/images/gluetun-configmap-1.png)

Copy the example YAML below, edit it to include the values you need for your config, and paste it in:


```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: elfbot-seerrbridge
data:
  RD_ACCESS_TOKEN: 'YOUR_RD_TOKEN_FROM_DMM'
  RD_CLIENT_ID: YOUR_CLIENT_ID
  RD_CLIENT_SECRET: YOUR_CLIENT_SECRET
  RD_REFRESH_TOKEN: YOUR_REFRESH_TOKEN
  TRAKT_API_KEY: YOUR_TRAKT_TOKEN
  OVERSEERR_API_KEY: YOUR_OVERSEERR_TOKEN
```

!!! tip "Syntax matters"
    Ensure you enclose the **entire** `RD_ACCESS_TOKEN` value in single quotes, as illustrated above.

Save your changes to create the ConfigMap. SeerrBridge should restart. If you need to make subsequent changes to the ConfigMap, find it under ConfigMaps and edit it directly. (*or use ElfBot for minor changes*)

#### Filtering (optional)

The [upstream docs](https://github.com/Woahai321/SeerrBridge?tab=readme-ov-file#-custom-regex-filtering) provide details about how search results can be filtered by using regexs.

As of v0.4.5, a global maximum for movie and episode size can also be set.

Optionally, edit your ConfigMap to apply the following values:

```
  MAX_MOVIE_SIZE: "60"
  MAX_EPISODE_SIZE: "5"
  TORRENT_FILTER_REGEX=^(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
```


{% include 'app_footer.md' %}