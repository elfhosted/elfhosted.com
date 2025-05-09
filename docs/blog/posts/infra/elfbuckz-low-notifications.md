---
date: 2023-10-10
categories:
  - CHANGELOG
tags:
  - elfbuckz
title: Notifications enabled on low ElfBuckz balances
description: Now you'll be notified when your ElfBuckz balance is running low
---
# Notifications enabled on low ElfBuckz balances

A longstanding issue we've been dealing with is that the [Wordpress plugin we use to provide ElfBuckz](https://woocommerce.com/document/account-funds/) doesn't include the ability to notify users when their balance is running low. So unless you manually keep track of your ElfBuckz balance, you're at risk of having your services stop when your ElfBuckz run out, without notice! :scream:

Since we recently fixed the deprovisioning bug, this has become even more important, so today I finally got my hands dirty and modified the plugin myself, adding the ability to notify users when their account balance goes low.

So.. you should now be alerted whenever your ElfBuckz balance drops below $1, which should give you plenty of time to arrange a [topup](https://store.elfhosted.com/product/elfbuckz-topup/) (*of course, once you subscribe to a top-up with the appropriate quantity, your ElfBuckz will "refill" every month, and you may never see these notifications*)

<!-- more -->

## Maintenance window shifted 1h earlier

Now that NZ has "sprung ahead" to daylight savings time, I've moved our maintenance window an hour earlier, so that I can perform routine maintenance between 10pm-11pm NZ time, and still get enough sleep to function! In 6 months or so, this'll shift an hour later again. 

As a reminder, the maintenance window is an **opportunity** to perform app / infrastructure updates, and your apps **may** be briefly impacted, but most of the time they're not!

## Jellystat, anyone?

I noticed [Jellystat](https://github.com/CyferShepard/Jellystat) mentioned in a [post in r/selfhosted](https://www.reddit.com/r/selfhosted/comments/173qtly/jellystat_is_for_jellyfin_what_tautuli_is_for_plex/) - it looks like it may be useful for Jellyfin "power users". If Jellystat would be useful to you, hit me up in [Discord][discord] and we can trial it ;)

### Summary

As always, thanks for building with us!

--8<-- "common-links.md"