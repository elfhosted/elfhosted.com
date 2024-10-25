---
title: Magically automated new media aquisition based on user activity
slug: suggestarr
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
{% include 'app_footer.md' %}