---
title: Magically automated new media aquisition based on user activity
slug: SuggestArr
description: SuggestArr is a project designed to automate media content recommendations and download requests based on user activity in media servers like Jellyfin, Plex, and now Emby.
upstream: https://github.com/giuseppe99barchetta/SuggestArr
sponsorship: 
- name: Buy Me A Coffee
  uri: https://buymeacoffee.com/suggestarr
---

# {{ page.meta.slug }}

SuggestArr is a project designed to automate media content recommendations and download requests based on user activity in media servers like Jellyfin, Plex, and now Emby. 

It retrieves recently watched content, searches for similar titles using the TMDb API, and sends automated download requests to Jellyseer or Overseer.

{% include 'app.md' %}

Features

* Multi-Media Server Support: Supports Jellyfin, Plex, and Emby for retrieving media content.
* TMDb Integration: Searches for similar movies and TV shows on TMDb.
* Automated Requests: Sends download requests for recommended content to Jellyseer or Overseer.
* Web Interface: A user-friendly interface for configuration and management.
* Real-Time Logs: View and filter logs in real time (e.g., INFO, ERROR, DEBUG).
* User Selection: Choose specific users to initiate requests, allowing management and approval of auto-requested content.
* Cron Job Management: Update the cron job schedule directly from the web interface.
* Configuration Pre-testing: Automatically validates API keys and URLs during setup.

{% include 'app_access.md' %}

## How to use it

Requirements

You'll need:

* [x] A streamer (*either [Plex][plex], [Emby][emby], or [Jellyfin][jellyfin])*)
* [x] Either [Overseerr][overseerr] or [Jellyseerr][jellyseerr]
* [x] A TMDB API key (*free, get it [here](https://www.themoviedb.org/)*) 

The SuggestAarr setup wizard will walk you through the following steps. At each step which requires configuration (API keys etc), it won't let you progress until its validated the settings. Take extra care when configuring your streamer URL, since the URL to use internally within ElfHosted is not a standard default.

### Step 1 / Pick Streamer

Pick your streamer:

![](/images/suggestarr-setup-choose-streamer.png)

### Step 2 / Setup TMDB

Enter and validate your TMDB API key:

![](/images/suggestarr-setup-tmdb-api.png)


### Step 3 / Setup Streamer

Validate your streamer (*will differ per-streamer*):

![](/images/suggestarr-setup-login-plex.png)

You may be warned that you're authorizing an device / application on a different IP to your own. This is expected, since SuggestAarr needs direct access to your Plex in order to scrape your watch history:

![](/images/suggestarr-setup-login-plex-2.png)

When configuring your streamer, use the **internal** URL, as follows:

* Plex: `http://plex:32400`
* Jellyfin: `http://jellyfin:8096`
* Emby: `http://emby:8096`

![](/images/suggestarr-setup-plex-1.png)

### Step 4 / Setup 'seerr

Setup Jellyseerr / Overseerr:

When configuring your 'seerr, use the **internal** URL, as follows:

* Overseerr: `http://overseerr:5055`
* Jellyseerr: `http://jellyseerr:5055`

Find your API key in your 'seerr, under `Settings -> General Settings`:

![](/images/suggestarr-setup-overseerr-1.png)

### Step 5 / Advanced Filter Configuration

Set your preferred TMDB rating threshold, filter out any genres you don't want, etc:

![](/images/suggestarr-setup-filter-configuration.png)

### Step 6 / Additional Configuration

Set final configuration, plus your cron schedule. Note that the app runs in the UTC timezone.

![](/images/suggestarr-setup-additional-configuration.png)

### Done 🎉

When your setup is complete, your SuggestAarr UI should look something like this:

![](/images/suggestarr-setup-done.png)

{% include 'app_footer.md' %}