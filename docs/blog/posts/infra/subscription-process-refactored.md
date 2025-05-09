---
date: 2024-05-20
categories:
  - infra
tags:
  - jellyfin
title: Jellyfin fixes, webhook refactoring, YouTube stardom
description: The past week we've seen a major Jellyfin release (and subsequent bugfix patches), a refactoring of our subscription backend (no more overwritten subscriptions on upgrade to monthly), and the humble beginnings of our YouTube channel!
---

# Jellyfin 10.9 is out! (and now, fixed)

[Jellyfin 10.9 was released](https://jellyfin.org/posts/jellyfin-release-10.9.0/) last week, with new features including "trickplay" (*live video scrobbing*), admin UI revamping, and improved ffmpeg transcoding powerz.

Unfortunately there was a [significant bug in 10.9 causing random lockups](https://github.com/jellyfin/jellyfin/issues/11624), but we were unable to roll back because of database upgrades. While the devs were working on the fix, we rolled out some changes to our health checks - rather than a TCP connection to confirm Jellyfin is alive (*but, sadly, still locked up*), we now use an HTTP test against the API's health endpoint, which fails when Jellyfin is locked up, so that we can at least quickly kill and restart a stuck Jellyfin instance.

The bugfix has rolled out in 10.9.2, so hopefully this is now a non-issue!

It also turns out that Jellyfin was not consistent in where it stored its transcoding data, and some instances were defaulted to `/config/transcodes` (*`/config` is backed by our expensive NVMe network storage, not where we want to be sending GBs of temporary transcoding data!*), while others were set to `/transcode` (*correct*) or `/config/cache/transcode` (*also incorrect*).

Tonight's update symlinks all of these combinations to `/transcode`, the 50GB ephemeral NVMe-backed disk on the local node, avoid stressing our network storage. In summary, you can ignore the transcode path in Jellyfin. We'll make it work in the backend :)

<!-- more -->

## Subscription process improvements

Since we priced in April 2024, and introduced trial periods for our apps, our provisioning webhooks have been a little "fragile", and more than one user was caught out when they upgraded from a daily to a monthly subscription, and the store removed all of their pods because of the sequence of changes! :facepalm:

Today I learned to use the Wordpress / Woocommerce REST API, and refactored how we process subscription changes, such that the store is the "source of truth" re the state of subscriptions, rather than whatever webhooks arrive in whatever sequence.

As a result, we should no longer have issues with subscriptions being truncated because webhooks arrived out-of-order, or because pending-cancellation orders finally expired.

An unexpected bonus was that when applying a "full sweep" of all subscriptions, we ended up dropping a bunch of unpaid/expired-but-not-removed subscriptions, reducing our pod count by ~25%! (*from 4200ish to 2900ish*)

Account provisioning / updates are particularly hard to debug / pre-test, so if I've made an error and you've lost some subscriptions which you **should** have, drop me an [#elf-help ticket][elf-help] and I'll debug!

##  "Please like and subscribe..." :fontawesome-brands-youtube:

I've been experimenting with creating video tutorials, with the goal of making some of our more complex setups easier / more accessible, and expanding our discoverability. I thought I'd start small, and experiment with some Stremio Addons - so far I've published two videos to the ["ElfHostMe" channel](https://www.youtube.com/@elfhostme ) - I'm trying to find a workflow which doesn't require me to spend hours editing videos, but still looks polished and neat enough to attract attention.

Here's my latest experiment:

<iframe width="560" height="315" src="https://www.youtube.com/embed/t90mk8fD33I?si=TpK3mFazZEsNKOeq" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

If you have feedback on these videos (*what to improve, what to ignore*), I'd love to hear it!

## Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"
