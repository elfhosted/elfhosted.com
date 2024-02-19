---
date: 2024-02-19
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Xtremio IPTV Addon for Stremio added to collection
description: ElfBot can force-restart pods now, and another Stremio Addon (Xtremio IPTV) joins our collection
---

# Xtremio Excels Excellently

After our recent hosting of public [TorrentIO](https://torrentio.elfhosted.com) / [Knightcrawler](https://knightcrawler.elfhosted.com) and [Annatar](https://annatar.elfhosted.com) instances, I was approached to take over hosting of another community Addon, the "Xtremio IPTV" addon. This one doesn't use Real-Debrid at all, but if you plug in your paid IPTV subscription details (*assuming your provider supports xtreme codes*), you can stream all your IPTV content inside Stremio!

It was a fun little addon to integrate, since there's no persistence or database required - you can see the final result at https://xtremio.elfhosted.com, and the public traefik stats [here](https://grafana.elfhosted.com/public-dashboards/cecd587de25d4731b48b5752b127682a?orgId=1).

We do now offer hosted instances of [Xtremio][xtremio], which provide the same features, but with a higher rate-limit.

<!-- more -->

## ElfBot can now force-kill pods

While it doesn't happen as often as it used to (*we have 20 nodes now for tenant workloads*), we still sometimes see the occasional #badelf, and users find pods that are "stuck" in a terminating state. I'm working on more [automated remediations](https://github.com/medik8s/node-healthcheck-operator) for situations like this, but in the meantime, I've given ElfBot the power to "force-restart" such stuck pods. See details on the [ElfBot][elfbot] docs.

## Disk usage message refactored, I/O load reduced

At the top of your ElfHosted dashboard is a summary of your current disk usage. This **used** to include links to a per-volume-generated "tree" view helping to identify disk usage across each volume, but with the proliferation of "infinite" streaming libraries now, and the volume of users, I suspect that this tree view generation (*which happened hourly*) was contributing significant I/O load.

I've refactored the message so that it'll still refresh the disk used/free stats hourly, but the process of calculating **where** your disk space is going, is now a manual process using [ElfBot][elfbot].

## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 273 | +8
:fontawesome-solid-hard-drive: Storageboxes mounted | 17 | +1
:alien: Zurg mounts: | 108 | +1
:floppy_disk: ElfStorage in TBs | 57 | -
:material-dolphin: Tenant pods | 3657 | +81
:superhero: Elf-vengers | 4 | -
:student: Trainees | 2 | -
:material-bug: Bugz squished | 1 | -
:fontawesome-solid-gamepad: New toyz | 2 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"