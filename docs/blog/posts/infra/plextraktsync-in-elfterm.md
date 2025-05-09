---
date: 2024-07-25
categories:
  - infra
tags:
  - CHANGELOG
title: PlexTraktSync comes to ElfTerm
description: To aid you in backing up / migrating your Plex libraries between apps, ElfTerm now includes PlexTraktSync!
---

# PlexTraktSync comes to ElfTerm

!!! warning "Old / daily subscriptions will sunset from 1 Aug. Take action as described below"

    We have a new pricing model / bundle structure which requires resubscriptions (*the store can't migrate daily to monthly subscriptions for us*). Unless you take action described [here](/blog/2024/07/10/pricing-model-updated/), your ElfHosted subscriptions **will** stop working some time after 1 Aug 2024. 

    Details [here](/blog/2024/07/10/pricing-model-updated/)!

With the increasing stability / popularity of [Riven][riven], we're seeing users regularly asking "*how can I switch from plex_debrid to Riven, keeping my Plex library?*"

There's no "import" option in Riven, but now we have the next-best thing - using PlexTraktSync within [ElfTerm][elfterm], you can:

* :one: "sync" your Plex library with Trakt, 
* :two: remove your old plex_debrid-managed libraries, and then
* :three: start "from scratch" with Riven, letting it sync back your library content from Trakt!

Read on for more...

<!-- more -->

## Plex now auto-repairs

[PlexDBRepair](https://github.com/ChuckPa/PlexDBRepair/tree/master) is now built into our Plex container, so every time you restart Plex, it'll give your library a tidy/check/optimize, avoiding any "weirdness" behind the scenes.

If you want to see the latest DBRepair results for your database, take a look at the `repair-db` container logs in your plex pod, using [Kubernetes Dashboard][kubernetes-dashboard]!

??? "Example output"
    ```
    k logs -n aa-funkypenguin funkypenguin-plex-95656778f-9mm6x repair-db



          Plex Media Server Database Repair Utility (User Defined)
                          Version v1.07.00

    [2024-07-25 05.08.07]       PlexSQLite = '/usr/lib/plexmediaserver/Plex SQLite'
    [2024-07-25 05.08.07]       Databases  = '/config/Library/Application Support/Plex Media Server/Plug-in Support/Databases'

    [2024-07-25 05.08.07] Automatic Check,Repair,Index started.
    [2024-07-25 05.08.07]
    [2024-07-25 05.08.07] Checking the PMS databases
    [2024-07-25 05.08.08] Check complete.  PMS main database is OK.
    [2024-07-25 05.08.08] Check complete.  PMS blobs database is OK.
    [2024-07-25 05.08.08]
    [2024-07-25 05.08.08] Exporting current databases using timestamp: 2024-07-25_05.08.07
    [2024-07-25 05.08.08] Exporting Main DB
    [2024-07-25 05.08.08] Exporting Blobs DB
    [2024-07-25 05.08.08] Successfully exported the main and blobs databases.
    [2024-07-25 05.08.08] Start importing into new databases.
    [2024-07-25 05.08.08] Importing Main DB.
    [2024-07-25 05.08.08] Importing Blobs DB.
    [2024-07-25 05.08.09] Successfully imported databases.
    [2024-07-25 05.08.09] Verifying databases integrity after importing.
    [2024-07-25 05.08.09] Verification complete.  PMS main database is OK.
    [2024-07-25 05.08.09] Verification complete.  PMS blobs database is OK.
    [2024-07-25 05.08.09] Saving current databases with '-BACKUP-2024-07-25_05.08.07'
    [2024-07-25 05.08.09] Making repaired databases active
    [2024-07-25 05.08.09] Repair complete. Please check your library settings and contents for completeness.
    [2024-07-25 05.08.09] Recommend:  Scan Files and Refresh all metadata for each library section.
    [2024-07-25 05.08.09]
    [2024-07-25 05.08.09] Backing up of databases
    [2024-07-25 05.08.09] Backup current databases with '-BACKUP-2024-07-25_05.08.09' timestamp.
    [2024-07-25 05.08.09] Reindexing main database
    [2024-07-25 05.08.09] Reindexing main database successful.
    [2024-07-25 05.08.09] Reindexing blobs database
    [2024-07-25 05.08.09] Reindexing blobs database successful.
    [2024-07-25 05.08.09] Reindex complete.
    [2024-07-25 05.08.09] Automatic Check, Repair/optimize, & Index successful.
    ```

## WebDAV includes configs

As of today, your [WebDAV][webdav] access (*used to manage your files externally when FileBrowser falls short*) can also see your `/config` volumes, just like FileBrowser can!

## Merch arrived!

Today, to great delight of my children who all tried to claim it, the first of my [ElfHosted merch](https://store.elfhosted.com/product-category/merch) arrived!

![](/images/blog/elfhosted-merch-arrived-sticker.jpeg)

(*You, too, could be rocking this fine "[kiss-cut](https://store.elfhosted.com/product/kiss-cut-stickers)" sticker*)

Thanks \@BSM for making the merch happen! :thumbsup:

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"
