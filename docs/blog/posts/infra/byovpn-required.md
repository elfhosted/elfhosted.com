---
date: 2023-07-24
categories:
  - build-in-public
tags:
  - infra
title: ElfVPN is dead, long live BYOVPN
description: For reasons which make sense in hindsight, BYOVPN is now required for all torrent clients
---

# RIP ElfVPN

ElfVPN was a shared VPN which allowed the torrent clients (*[Deluge][deluge], [qBittorrent][qbittorrent], [rutorrent]*) to be evaluated / used without having to bolt-on a BYO VPN subscription.

Shortly after we ramped up our test users from [r/seedboxes](/blog/2023/07/21/bring-in-the-seedboxers/), the VPS which ran ElfVPN was terminated by the provider for DMCA abuse.

After some consideration (*details below*), I've decided not to replace it, and instead withdrawn the ElfVPN products from the store.

TL;DR - From now on, in order to use the torrent clients, you will need to BYO VPN...

<!-- more -->

## What will happen to existing subscriptions?

Because the product has been withdrawn from the store, it won't be included on your next (daily) subscription renewal. Please subscribe to one of the BYOVPN torrent clients instead.

!!! tip "Don't see your VPN provider? We can add it!"
    If you don't see your particular VPN provider, create an [#elf-help][elfhelp] ticket, and we should be able to add it for you. Typically any OpenVPN or Wireguard VPNs will work, but OpenVPN is priced higher due to its higher CPU requirements.

!!! question "What if I don't want to BYO VPN?"

    There are other options besides torrenting. We have NZB apps ([NZBget][nzbget] and [SABnzbd][sabnzbd]), as well as [RDTClient][rdtclient] for Premiumize/Debrid support.

## But why?

Here are the reasons:

### Limit drive-bys

While I want new users to try out the ElfHosted services, what I **don't** want, is to provide "free torrenting" to users who have no intention of sticking around, or just want to use up their $10 free ElfBuckz, and move on. Requiring a VPN in order to use torrent apps hopefully filters out some of this behaviour, since you'd need to have already invested in a VPN in order to use them (*which aligns with our target torrent users*).

### BYO FTW

Stick with the BYO philosophy

I'm liking the BYO philosophy (*especially for storage*) because it reduces the amount of responsibilty I feel for continuity of access to media. Seedplicity basically ran for 2 months after the shutdown announcement, simply to allow users time to offload their media. ElfHosted is built-in-public rapid prototype, and I hope it'll be sustainable long-term, but I want users to be able to pick up and leave with their data (*and VPN config!*) without any dependency on me.

(*This might end up being a standalone blog post*)

### Reduces cost and liability

Finally, running a VPN-terminating VPS obviously comes with a cost, which I can now avoid. I'm also wary of any perceived responsibilty for the actions of torrent users, and I felt that permitting the torrenting traffic through a VPN I own and manage would indicate implicit approval.

### Performance

As soon as we loaded up on users, the throughput rate of ElfVPN suffered. Running BYOVPN will result in a **much** improved user experience.

!!! tip "Got a suggestion, or found a bug?"
    Post your suggestion in [#elf-suggestions](https://discord.com/channels/396055506072109067/1128624284881915914), and your bugz in [#elf-bugz](https://discord.com/channels/396055506072109067/1128625389472841728)!

## Other changes

### Improvementz

* :white_check_mark: It turns out our nodes (Intel i9-9900K) support QuickSync, so some [#elf-a-testers](https://discord.com/channels/396055506072109067/1127350269794066585) are testing hardware transcoding in the streamers ([Jellyfin][jellyfin], [Emby][emby], [Plex][plex]). If you want to help test, hit me up to temporarily switch you to the alpha channel! :scientist:
* :white_check_mark: Feedback on the biometric / passkey logins has been positive, but there was a conflict between the original email verification flow, and the OwnID enrollment flow. I've removed the old 'verify your email' plugin, and enforced the OwnID login flow, since this ensures a user has a valid email anyway.
* :white_check_mark: Refactored the process which removes a user's "24h" orders, which wasn't working well. 24h app termination should now work correctly, and I'm working on the related storage cleanup flow. Effectively, after your app expires / fails to resubscribe, we'll hang onto the app data for `x`[^1] days, and then delete it
* :white_check_mark: Removed the troublesome Longhorn, which was not scaling well and contributing to node load.

### Upcoming

* [ ] Add a link on the store user account page to the app dashboard (*not done yet, but I've found out [how to do it](https://github.com/woocommerce/woocommerce/wiki/Customising-account-page-tabs)*)
* [ ] Send email to user with link to their dashboard (*enabled but needs testing*)
* [ ] Make checkout fields work better with browser auto-fill (*is this a Woocommerce/Wordpress issue?*)


### Summary

Thanks for building with us - stay tuned!

--8<-- "common-links.md"

[^1]: The value of `x` is under consideration, let me know your thoughts!

