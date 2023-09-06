---
date: 2023-09-06
categories:
  - new-app
tags:
  - miniflux
title: Introducing Miniflux, minimalistic and opinionated feed reader
description: Today we added Miniflux, which has been my go-to self-hosted feed reader for years
---
# Introducing Miniflux

I've been a fan of [Miniflux](https://miniflux.app/) since I [publicaly ditched TinyTinyRSS](https://www.funkypenguin.co.nz/blog/miniflux-lightweight-self-hosted-rss-reader/) for it, 6 years ago. (*read all about it!*)

![Screenshot of Miniflux](/images/screenshots/miniflux.png)

Miniflux is part of a class of apps I'm hoping to add more of - standalone apps which leverage an external database backend (*like MySQL or postgreSQL*). In this class we already have [Seafile][seafile] and [Mattermost][mattermost], and I hope to add NextCloud in the near future. (*and hopefully eventually [Radarr][radarr] and [Sonarr][sonarr]!*)

Using a "real" database (*as opposed to sqlite*) makes backup / migration a little tricker, but I've implemented automatic daily backups for the database component (*they'll go to `/storage/elfstorage/backups/<app>/`*), alongside whatever backup / export option the app natively provides.

See more on the [app][miniflux] page, or perform a 24h trial / subscription at the [store](https://store.elfhosted.com/product/miniflux/)!

More news...

<!-- more -->

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers[^1] | 37
:fontawesome-solid-hard-drive: Storageboxes mounted | 16
:material-sync: Rclone mounts | 11
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 1

### Bugz squished

#### Dashboards no longer broken

The SSL certs for the old app-naming convention (`https://<user>.<app>.elfhosted.com`) were about to expire, and it's been about 2 months since we migrated to the new convention (`https://<user>-<app>.elfhosted.com`), so I removed the deprecated ingressroutes. 

Unfortunately, at the same time, I removed the ingressroutes pointing to users' dashboards, so `https://<user>.elfhosted.com` was returning 404s for half the day! :facepalm:. This was fixed with an out-of-schedule hotfix during the day.

### Summary

As always, thanks for building with us - feel free to share suggestions, ideas, and whatever you ate for breakfast today! :cooking:

[^1]: I changed this metric to count subscribers as reported by Wordpress, rather than provisioned users (*72 currently*), because (a) I have some un-provisioning scripts to fix, and (b) I think subscribers is a more accurate measure of current growth.
[^2]: Just in time for the Aug 2023 elf-disclosure report this weekend!

--8<-- "common-links.md"