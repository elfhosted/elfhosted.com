---
date: 2024-04-12
categories:
  - CHANGELOG
tags:
  - infrastructure
title: RDTClient rebased on mainstream, secured
description: we've switched to the "vanilla" RDTClient based on the original upstream source, and it's much faster, with some extra features!
---

# RDTClient Updated, tested

In the past we've had issues with updates to RDTClient, since the version which we initially used (*based on [the laster13 fork](https://github.com/laster13/rdt-client) of https://github.com/rogerfar/rdt-client*) ran as root (*later dropping privileges*), and was hard to lock down.

Today an intrepid team of elves worked on refactoring and testing the latest official upstream (*v2.0.73 currently, but it changes fast!*), which I'm happy to report is working well, and is noticeably faster than the old version.

By the time you read this, you'll have been auto-upgrade to the latest version, and subsequent upstream updates will be automatically applied (*no more testing required after each upstream release*).

!!! tip "Show @rogerfar some :heart:"
    If you'd like to encourage RDTClient's developer, @rogerfar, to continue making bug fixes and feature improvements, weigh in on or just add some reactions to [this issue](https://github.com/rogerfar/rdt-client/issues/463)!

<!-- more -->

## Bugfixes

### Fresh Plex Install bug fixed

Yesterday's update tidied up Plex's PhotoTranscoder cache, but this ended up breaking Plex for brand-new users. I manually mitigated this for any new users who joined in the past 24h, but now that the fix has rolled out, new Plex users can use Plex right away again, without issue.

## Coming Soon

### TRaSH Guides

\@LayeZee has been helping users implement TRaSH Guides custom formats to optimize their media selection for streaming (*without transcoding*). We added [Recyclarr][recyclarr], but it's still a tedious process to build a config file. \@LayeZee has been working on a ELI5 guide on the process of manually setting up formats, and \@pomnz has suggested we pre-configure the Aars with all the custom formats etc, to make new user setup easier.

Watch this space, and shout out if you have experience with the TRaSH setups and how best to implement / maintain them.

(*This weekend's project!*)

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 364 | -14
👾 Zurg mounts: | 155 | -3
💾 [ElfStorage](https://elfhosted.com/what-is/elfstorage/) in TBs | 91 | +1
🐬 Tenant pods | 3949 | -61
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 4 | -
🧑‍🎓 Trainees | 2 | -
🐛 Bugz squished | 1 | -
🕹️ New toyz | 1 | -

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"

