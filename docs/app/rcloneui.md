---
title: Elf Hosted Rclone UI 🪄 FREE
slug: Rclone
description: Rclone is the defacto tool for managing multiple remote storage endpoints
upstream: https://rclone.org/
---

# {{ page.meta.slug }}

Rclone is the defacto tool for managing multiple remote storage endpoints

![Screenshot of {{ page.meta.slug }}](/images/screenshots/{{ page.meta.slug | lower }}.png){ loading=lazy }

{% include 'app_access.md' %}

## How do I use it?

When you first load the Rclone UI, you'll be prompted for a password. Enter any user/pass (*they're not validated*) to login.

### Set bandwidth limit

From the dashboard, set a reasonable bandwidth limit to avoid impacting all users:

![Setting rclone bandwidth limit](/images/rclone-bandwidth.png)

### Add remotes

Use the UI to add and test your remotes (S3, dropbox, etc)

### Add alias remotes for local mounts

In order to interact with locally-attached mounts (storagebox, elfstorage, etc), you'll need to add each as an "alias" remote. The process is illustrated below:

![Add alias remote](/images/rclone-add-remote-1.png)

![Add alias remote](/images/rclone-add-remote-2.png)

### Transferring data

Use the "Explorer" interface in split-screen mode to open two remotes at once, and then drag/drop folders between them to trigger a transfer:

![Add alias remote](/images/rclone-add-remote-3.png)

{% include 'app_footer.md' %}