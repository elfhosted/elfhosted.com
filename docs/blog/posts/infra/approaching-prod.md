---
date: 2023-07-29
categories:
  - build-in-public
tags:
  - infra
title: Moving into "production"
description: Our code is public, our GitOps magic is strong, ready for numbers!
---

# Approaching production

Although it's fairly arbitrary, July was our month of beta testing (*June being "alpha", when things were only semi-working*), and August will be our first month of "production". Most of the design questions are stabilized now (*for example, BYO VPN for torrent clients, hardware transcoding, etc*), the guts of the platform is [now open-sourced](https://elfhosted.com/open/), and it feels as if the next step is to increase the user base, in order to (a) fund the infrastructure, and (b) surface any further issues / improvements to be found.

<!-- more -->

## Promotion efforts

To this end, I've been focusing on promotion, or making ElfHosted more discoverable, with mixed results. After their API changes, Reddit is not what it once was for technical communities, Twitter is "icky", and my attempt to engage r/selfhosted was a disaster, eventually deleted by the mods for being "unrelated to selfhosting".

One of our elf-a-testers who's active in the unRAID community suggested I work on detailed "guides" targeting specific use-cases, so I wrote up a guide for unRAID users who want to use our VPN'd torrent clients to download to storageboxes, mounted to their unRAIDs. If this lands well, I'll invest more time in community / application-specific guides, which will hopefully engender goodwill, and some positive organic search results too.

## What's this GitHub noise?

You may have noticed that the git-hub connected channels in Discord, specifically [#elf-infra](https://discord.com/channels/396055506072109067/1119488567312400404) and [#elf-charts](https://discord.com/channels/396055506072109067/1119488426358603807) are quite noisy. The reason these exist in Discord is to provide transparency to ongoing changes - they're there if you're interested in what's happening behind the scenes, but if it's not your jam, just mute / ignore the whole category :grin:

## RIP Seedplicity

Today also marks the final day of Seedplicity, after a long, protracted shutdown period for user migrations. The [big red switch](https://discord.com/channels/907016842873278474/973461820427878410/1134495324887588985) was flipped today :material-grave-stone:

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total users | 45
:material-bug: Bugz squished | 2
:fontawesome-solid-gamepad: New toyz | 0

### Bugz squished

* :bug: SurfShark BYO VPN is now working
* :bug: Calibre uses correct path for initial library creation (`/storage/elfstorage/books`, rather than `/media/books`)

### Upcoming

* [ ] Add a link on the store user account page to the app dashboard (*not done yet, but I've found out [how to do it](https://github.com/woocommerce/woocommerce/wiki/Customising-account-page-tabs)*)
* [ ] Send email to user with link to their dashboard (*enabled but apparently not working, grr*)
* [ ] Make checkout fields work better with browser auto-fill (*is this a Woocommerce/Wordpress issue?*)

Thanks for building with us - stay tuned!

--8<-- "common-links.md"