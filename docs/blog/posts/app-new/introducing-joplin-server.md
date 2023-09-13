---
date: 2023-09-13
categories:
  - new-app
tags:
  - joplin-server
title: Introducing Joplin Server, sync, edit, and publish your notes from anywhere
description: Today we added Joplin Server, a native sync backend for Joplin, allowing for multi-client editing, publishing, etc.
---
# Introducing Joplin Server

Today's new app is a fresh request from one of our fellow elfies.. [Joplin](https://joplinapp.org/) is a 100% open-source , markdown-driven note-taking app, similar to [Obsidian](https://obsidian.md/) or [Logseq](https://logseq.com/). There are [apps](https://joplinapp.org/) for Mac, Windows, and Linux, even a terminal app!

[Joplin Server][joplin-server] is the open-source version of the sync engine behind https://joplincloud.com, which takes you beyond simple apps, by enabling cross-device sync, sharing, publishing, etc.

![Screenshot of Joplin](/images/screenshots/joplin-server.png)

Adding Joplin Server to your "Elf Stack" will let you utilize your ElfStorage (*pass go, collect 100GB*) for storing notes, attachments, etc.

The "publish note" feature is pretty - [here's an example](https://funkypenguin-joplin-server.elfhosted.com/shares/6m2JjKW5zUqtZrWNMj1lNI) of what a published note looks like - it's published by joplin-server (*so you can edit it with any client on any device*), and it's auto-updated whenever the note is updated.

If you don't trust a seedy seedbox host with your super secret notes (*and why should you?*), you can enable E2E encryption in the client apps, which (*like [Seafile][seafile]*) means that all that's stored in ElfStorage is the encrypted blobs, and some metadata in the postgresql database.


<!-- more -->

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers[^1] | 39
:fontawesome-solid-hard-drive: Storageboxes mounted | 17
:material-sync: Rclone mounts | 11
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 1

### Bugz squished

#### Radarr 4K dashboard stats fixed

Although it may one day no longer be required (Radarr will eventually support multiple qualtiy profiles at once!), some of us are stuck using 2 instances of Radarr if we want 1080P and 4K content to co-exists. Those of us were seeing an unhappy red question mark in our dashboards, where the Radarr 4K stats should appear. This was due to an API key muddle-up when implementing the [exposed API services](/blog/2023/08/31/exposing-apis-without-sso/), which is now fixed!

### Summary

As always, thanks for building with us - feel free to share suggestions, and your own ideas for new apps to add!

--8<-- "common-links.md"