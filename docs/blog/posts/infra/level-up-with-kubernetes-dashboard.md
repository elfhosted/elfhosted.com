---
date: 2024-01-03
categories:
  - CHANGELOG
title: Go behind the scenes with Kubernetes Dashboard, sponsorships
description: Want to go deeper into the geeky rabbit hole? Check out your apps with Kubernetes Dashboard! Also, let's sponsor our favorite developers!
---
# Go behind the scenes with Kubernetes Dashboard

As you'll no doubt have read, ElfHosted is not a traditional seedbox, VPS, or shared hosting provider, but rather something new - we run the apps you choose, on a selection of appropriate hosts, in a highly-available and fault-tolerant way, using [Kubernetes](https://geek-cookbook.funkypenguin.co.nz/kubernetes/). And we [open-source it all](/open/).

## Kubernetes

### What's the downside?

This distinction has many advantages (*automation, scalability, resilience...*), and some complex implications - for one, your apps don't necessarily run on the same hardware, so it may be that [Radarr][radarr], [Sonarr][sonarr], and [qBittorrent][qbittorrent] are all running on different hosts with different storage and processor capabilities. Our streamers ([Plex][plex], [Jellyfin][jellyfin], [Emby][emby]), for example, run on hosts with Intel Quicksync support, for hardware transcoding support.

We can't (*easily*) provide TCP-based access for services like SSH or FTP, which is why we rely on rlcone and [WebDAV][webdav] for data migrations, and we can't provide "root access" because each app runs on an as-locked-down-as-possible container, dispersed across our cluster.

One previously negative implication has been (*until now...*) that it's not simple to see app's real-time CPU / memory usage, or to watch logs in realtime. Certainly, these are available at a cluster-admin level, but without complicated authentication integrations, it's not possible to provide a user with visibility into their own resources, without exposing the privacy of **other** users.

### A sexy solution!

We now have a solution I'm particularly proud of, because it exposes our Kubernetes environment on a per-user basis, in a way that's safe, while still providing all the cool visibility.. which I'm happy to now be able to share with you...

<!-- more -->

Behold, the mighty [Kubernetes Dashboard][kubernetes-dashboard]!

![Screenshot of Kubernetes Dashboard](/images/screenshots/kubernetes-dashboard.png){ loading=lazy }

(*Read more for the sexy solution, plus details on which Open Source projects we sponsor, and how we help you to help your favorite app devs!*)

Using your own dedicated, locked-down and SSO-secured [Kubernetes Dashboard][kubernetes-dashboard] instance, you can see your app (*pod*) CPU/RAM usage, watch logs in realtime, and even restart apps (*an alternative to [ElfBot][elfbot]*).

In time, I plan to expand this to limited editing of ConfigMaps, which will allow easy[^1] customizing of app environments, for more complex apps which rely on many ENV variables.

## Support your favorite app devs

When I posted recently in the [TRaSH-Guides Discord](https://trash-guides.info/discord) about ElfHosted, I was challenged by a user on why I was "selling" free software (*Radarr, etc*), and whether or not I did anything to support the devs behind the projects I was "profiting from"[^2].

I did clear up the misunderstanding (*we're not "selling" free software, we're selling the resources and management to let you **run** that free software*), but since then I've wanted to do more to support the devs behind the projects we rely on.

I don't have an easy or prescriptive solution, but what I've decided to do currently is to [sponsor the tools which make the whole platform work](/open/sponsorship/), and to make it easy for individual users to choose how / whether to sponsor / support the developers of the software they use. I'll be adding sponsorship as an ongoing expense to our monthly "Elf-Disclosure" [progress reports](/open/), since these components are critical to the operation of our platform.

I created the ["sponsorship" page](/open/sponsorship/), to detail the projects I sponsor, and my rationale behind this decision.

I've also added links to every app's page (*i.e., [Calibre][calibre] or [Jellyfin][jellyfin], to pick at random*) to the project's direct sponsorship / donation options.

## Bug fix : NZBGet /config volume

A user support request unearthed another bug yesterday - [NZBGet][nzbget]'s `/config` volume was previously set to a maximum of 1GB (*as many apps are*). It turns out that if you have a big queue, and `/config` fills up, NBZGet doesn't tell you, but fails when adding new NZBs, resulting in a confusing and complicated fault-finding process!

Consequently, NZBGet's `/config` volume is now expanded to 2GB!

(*There's a related, as-yet-unfixed bug preventing the dashboard from highlighting this full-uppage to you in a big, red banner!*)

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers [^1]| 131
:fontawesome-solid-hard-drive: Storageboxes mounted | 22
:material-sync: Rclone mounts | 14
:material-dolphin: Tenant pods | 1202
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 2

### Summary

As always, thanks for building with us!

--8<-- "common-links.md"

[^1]: This is already possible using [ElfBot][elfbot], but in a limited, one-at-a-time fashion
[^2]: See our [monthly reports](/open/) to gauge the "profiting from" factor :P