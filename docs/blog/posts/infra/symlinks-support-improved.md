---
date: 2024-03-02
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Symlinks are further improved
description: Symlink folders are refactored and ElfBot can now delete broken symlinks
---
# Symlink folders refactored

We [recently refactored](/blog/2024/02/27/elfbot-reports-on-supercharged-symlinks/) where we store symlinks, for optimal I/O utilization. I've made a few adjustments based on early feedback, and updated the documentation here:

* [ElfBot][elfbot]
* [Radarr][radarr]
* [Sonarr][sonarr]

To summarize the changes since the [last update](/blog/2024/02/27/elfbot-reports-on-supercharged-symlinks/)..

1. `/storage/symlinks` is now 100Gb, because the aars were refusing to import new content to 1Gb volume, since they thought it wouldn't fit. We can't afford to give out 100Gb of NVMe storage to all users though, so this space is intended to utilized **only** for symlinks (*and so remain empty*), and a regular process will delete any files in `/storage/symlinks` which are **not** symlinks.
2. ElfBot will import symlinks to `/storage/symlinks/import`, so as not to conflict with library storage at `/storage/symlinks/{movies,series,etc}`
3. ElfBot can also symlink individual folders now, so for example, you could navigate to `/storage/realdebrid-zurg/shows/The Simpsons - All Seasons`, and run `elfbot symlink here`, and you'd end up with `/storage/symlinks/import/The Simpsons - All Seasons` to point Sonarr at.

!!! question "Need to migrate your symlinks?"
    Have you got thousands of symlinks sitting in `/storage/elfstorage/` on spinning rust, and need them migrated to `/storage/symlinks`? We'll have an illustrated guide available in a day or two, so sit tight, or create an [#elf-help][elf-help] ticket if you'd like a hand!

## ElfBot deletes broken symlinks

In addition to reporting on broken symlinks with `elfbot symlink report-broken`, you can now tell ElfBot to **delete** any broken symlinks, with `elfbot symlink delete-broken`

## Today's scoreboard

:material-target: Metric | Numberz | Delta
---------|----------|----------
:fontawesome-regular-circle-user: Total subscribers | 325 | +9
:fontawesome-solid-hard-drive: Storageboxes mounted | 18 | -
:alien: Zurg mounts: | 131 | +2
:floppy_disk: ElfStorage in TBs | 65 | +3
:material-dolphin: Tenant pods | 4097 | +38
:superhero: Elf-vengers | 4 | -
:student: Trainees | 2 | -
:material-bug: Bugz squished | 1 | -
:fontawesome-solid-gamepad: New toyz | 1 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"