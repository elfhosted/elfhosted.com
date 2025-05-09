---
date: 2024-02-18
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Annatar Arrives Afficially!
description: We're expanding our collection of Stremio / Debrid-related addons, by sponsoring the official public Annatar instance
---

# Annatar Arrives "Afficially"

A [casual offer of hosting to a new addon announced in r/StremioAddons](https://www.reddit.com/r/StremioAddons/comments/1apghdn/comment/kq7uq7u/) has turned into rewarding partnership with [Annatar](https://gitlab.com/stremio-add-ons/annatar), a Stremio addon which leverages Jackett and Redis to provide a cached, just-in-time torrent search for Stremio.

The official, community site is at https://annatar.elfhosted.com, and we (\@brett and I) have been geeking out over the [public "GrafAnnatar" metrics](https://grafana.elfhosted.com/public-dashboards/c78ab8d31f084ef4bccb7017b4518588?orgId=1&refresh=30s).

Once the public instance was up, I added [ElfHosted bundles to the store](https://store.elfhosted.com/product/annatar-jackett-bundle) - these private instances benefit from the shared redis cache, which is well-seeded by the public instance, but allow users to configure their own selection of torrent indexers in their own Jackett backend.

<!-- more -->

## Zurg updated to 2.9.3 hotfix.11

Tonight's maintenance window updated us to Zurg 2.9.3-hotfix.11, which is purported to [fix the current intermittent refresh issues](https://www.reddit.com/r/debridmediamanager/comments/1atkd4s/zurg_v093hotfix11_i_think_ive_finally_resolved/) noted by some users.

## Bugfix: Fresh Aars removing downloads

Recently I updated the default config for Radarr/Sonarr to auto-provision a connection to RDTClient. Unfortunately I missed unchecking the box labeled "Remove completed downloads from client", and so fresh Aars were successfully downloading content via RDTClient, and then happily deleting it, which removed it from the debrid provider, creating a dead symlink! :man_facepalming:

This is now fixed!

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"