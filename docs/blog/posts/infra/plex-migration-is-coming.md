---
date: 2024-03-05
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Plex storage migration is coming
description: In the upcoming maintenance window, we'll migrate Plex instances' storage to reduce I/O congestion
---
# Plex storage migration approaches

We've started to run into I/O contention on the big, busy storage volumes, which use CephFS to make files available to multiple pods (*for example, to Plex for storage, but to FileBrowser for browsing config*).

In the next maintenance window, we'll be migrating users' Plex libraries (*some of which are >50GB!*) to Ceph "block" storage, which bypasses the I/O contention, at the cost of being unable to "view" your Plex metadata / DB / logs via FileBrowser (*we'll come up with an alternate solution as required*).

This migration has been observed to take a long time, especially for larger libraries (*roughly 2 min / GB of Library*), so we're trying to "stagger" it as best as possible, by shifting "earlybird" users onto the alpha channel, so that their migration can happen in a time of their choosing, rather than during maintenance.

If you've got a big(ish) Plex library, or you care quite a lot about when it goes down, create an [#elf-help][elf-help] ticket to arrange a time (*before the next maintenance window*) to have your Plex instance migrated.

## Auto-delete trash in Plex now disabled

Thanks to a suggestion from @pomnz, we're now explicitly setting Plex's setting **not** to delete trash automatically after a scan. (*This can cause confusion and re-downloads as deleted files disappear, and then Radarr/Sonarr attempt to re-download the content!*)

## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 354 | +29
:alien: Zurg mounts: | 131 | +2
:floppy_disk: ElfStorage in TBs | 65 | -
:material-dolphin: Tenant pods | 4368 | +271
:superhero: Elf-vengers | 4 | -
:student: Trainees | 2 | -
:material-bug: Bugz squished | - | -
:fontawesome-solid-gamepad: New toyz | 2 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"