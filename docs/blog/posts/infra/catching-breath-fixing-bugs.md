---
date: 2024-01-11
categories:
  - CHANGELOG
tags:
  - autoscan
  - elfbuckz
title: Fixing bugs, catching breath
description: It's been a busy few days, with the plex-debrid bundle now available! No new toyz today, but we did find some bugz to fix...

---
# Beware, here be bugz

After yesterday's [plex-debrid][plex-debrid] business, [Discord][discord] (*and the ticket channels*) were surprisingly quiet today. Either the hiccups are gone and users are happily streaming, or they've given up and gone outside with the [rest of r/realdebrid](https://www.reddit.com/r/RealDebrid/comments/193ogzd/is_rd_down/)!

One minor improvement to note - you can now do a once-off [top-up of ElfBuckz][elfbuckz], without it turning into a monthly subscription.

We did find a few bugs today, which I'll list below, in order of criticality:

<!-- more -->

## ElfBuckz top-ups not topping-up

In a few reported cases now, users have topped up their ElfBuckz, paid their $$, and found that their ElfBuckz balance hasn't changed! I've created a support issue with the developer of the "[Account Funds](https://woocommerce.com/document/account-funds/)" plugin we use - the problem seems to be caused by the PayPal Payments plugin grumbling about missing metadata, when paying with a credit card (*i.e., PayPal is sad it's not invited to play*). Sad plugins shouldn't affect our top-ups though, so I'll progress this via the devs.

If you suspect that your ElfBuckz top-ups are missing, create an [#elf-help][elf-help] ticket, and I'll straighten it out!

## Subscriptions flapping

Some users have noticed their entire subscription disappearing, and then quickly re-appearing again. This seems to be related to the 72h grace period on expired subscriptions, and a race when merging YAML files to update services after daily renewals.

I've refactored the provisioning script to be less complicated therefore less fragile, and these issues should be a thing of the past now, but the effect may take up to 24h to roll out. 

If you suddenly find yourself with no apps, and your ElfBuckz are in the green, [you know what to do][elf-help]...

## Autoscan missing for Plex users

If you were one of the users who recently migrated from Plex+VPN back to regular Plex, you'd have been seeing health alerts about [autoscan][autoscan] being down. This was a missing conditional on the autoscan service, and is now fixed.

## Autoscan 30min delay on updates

Speaking of autoscan, it turns out there's was a default 30min delay before autoscan will update libraries in [Plex][plex], [Jellyfin][jellyfin], or [Emby][emby]. This has changed to 1min for new users, but existing users can make the change themselves, by editing `config/autoscan/config.yml`, and setting:

```yaml
minimum-age: 1m
```

## Zurg and plex_debrid, snuggling

Yesterday's change to better spread the debrid-dealing pods out over our nodes was effective, but I realized that a user with both [RDTClient][rdtclient] **and** [Zurg][zurg] could find themselves downloading from [Real-Debrid][real-debrid] from two different IPs simultaneously, and therefore triggering an account ban.

I've added a [podAffinity](https://github.com/geek-cookbook/elf-charts/blob/98918e0f05fb35e59ccbb608661097795a0d0000/charts/other/myprecious/values.yaml#L8058) to ensure that if you **do** have Zurg **and** RDTClient, they'll snuggle together on the same node, so they'll have the same source IP address!

### Summary

As always, thanks for building with us - feel free to share suggestions, and your own ideas for new apps to add!

--8<-- "common-links.md"

[^1]: The big increase here is due to all the Zurg mounts!