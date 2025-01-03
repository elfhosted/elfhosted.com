---
title: ElfHosted TorBox
slug: TorBox
description: TorBox is a next-generation "Debrid" provider, offering 
upstream: https://torbox.app
links:
works_with:
- RDTClient
- Prowlarr
- Blackhole
---

# {{ page.meta.slug }}

TorBox is a popular newcomer to the "debrid" downloader landscape. TorBox's core differentiator is that they do not limit users to a set amount of IP addresses, but rather they allocate download "slots". Once the slots on your plan are full, you can continue to add downloads to a queue, which will be serviced as slots become available.

You can use TorBox with ElfHosted to:

* Stream media via Stremio, using our [Stremio addons][stremio-addons]
* (Previous guides re Plex libraries have been removed since their use would conflict with [TorBox's abuse system](https://support.torbox.app/en/articles/10336778-the-torbox-abuse-system), and given cached items are [removed from a user's library after 30 days](https://intercom.help/torbox-support/en/articles/9923071-how-does-the-torbox-cache-work))

--8<-- "common-links.md"