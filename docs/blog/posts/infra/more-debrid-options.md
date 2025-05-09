---
date: 2024-01-20
categories:
  - CHANGELOG
tags:
  - rdtclient
  - zurg
  - jellyfin
  - emby
title: More debrid options, +100% compute capacity
description: We've added 100% compute capacity, and more toys for debrid users, including alldebrid, and Jellyfin/Emby support

---
# Mooar debrid toys

It's too soon to tell whether it's "just a passing phase", but the "infinite" streaming app bundles seem to be a popular alternative to traditional torrenting / usenet. It's a good fit for us, since (a) the apps can be complicated to interconnect, (*and automating complexity is our jam*), and (b) they rely primarily on compute and network resources, which are cheap and easily expandable, rather than storage, which is a stone-age PITA :rock:.

So for your instant-streaming enjoyment, I present the following "instant streaming" guides:

* :gift: [Plex, with "infinite storage"](/guides/media/stream-from-real-debrid-with-plex)
* :gift: [Plex, with "infinite storage", managed with Arrs](/guides/media/stream-from-real-debrid-with-plex-radarr-sonarr-prowlarr/)
* :gift: [Jellyfin, with "infinite storage", managed with Arrs](/guides/media/stream-from-real-debrid-with-jellyfin-radarr-sonarr-prowlarr/)
* :gift: [Emby, with "infinite storage", managed with Arrs](/guides/media/stream-from-real-debrid-with-emby-radarr-sonarr-prowlarr/)

We've also got an [alldebrid bundle](https://store.elfhosted.com/product/advanced-infinite-arr-plex-alldebrid-streaming-bundle) ready for a trial, if that's your flavor. 

Read more for capacity expansion, and changes to TDarr and WebDAV access to meet resourcing constraints...

<!-- more -->

## 100% more compute

All these new trial users have put some pressure on our nodes, and rather than loosing the momentum of new trials, or turning users off with a bad experience, I've added 100% more compute nodes to manage the load.

I'm taking the opportunity to experiment with "right-sizing" our compute nodes, based on what's available to us on [Hetzner's server auction](https://www.hetzner.com/sb?location=FSN). It turns out that we max out the nodes on CPU well before RAM becomes a constraint, so our i9-9900K 128GB nodes may be too "dense". It may be more effective to replace these with more 64GB nodes, and a combination of i9s (*QSV support*) and i7s (*no hardware transcoding*), letting Kubernetes schedule the streamer pods onto the QSV-supporting nodes.

## BYO compute

A [conversation in #elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303/1197437976481890304) sparked a left-field idea.. users with large Plex libraries / audiences may not "fit" in our regular product usage.. and may want more CPU, RAM, transcoding space, or network capacity.

It's hard to accommodate these users on our shared infrastructure, but it may be possible to provide services on "dedicated" nodes - for example, we'd be able to offer "Plex Unchained" on a dedicated i9-9900K 64GB node like this one:

![](/images/blog/example_hetzner_i9900k_64gb_node.png)

We'd have to work out the details like setup fees, pre-payment (*I have to pre-pay for the nodes*), and management overhead, but we could effectively dedicate an entire node to an individual user, giving them **all** the CPU / GPU for their streaming / transcoding requirements.

If this is interesting to you, reach out and let's talk :)

## Tdarr removed for bad behaviour

There have been a few kernel lockups over the past few days, and the evidence seems to suggest it's related to [TDarr][tdarr] instances (*unless configured explicitly per the [docs][tdarr], TDarr will eat much more RAM than allocated, quickly get itself OOMKilled, rinse and repeat, causing storage i/o drama and generally making a nuisance of itself*). I've taken it "off the menu" for now, and may need to bring it back if / when BYO compute is a thing.

If you were one of the handful of users with TDarr on your subscription, it'll be removed, so you won't be charged for it any longer.

## WebDAV egress dropped to 5MB, ingress unlimited

Until now, WebDAV access (*which provides the facility to "exfiltrate" your data and config from any attached storage*) has been throttled to 10MB/s via rclone CLI arguments. On a hunch that this may be doing more harm than good re long I/O delays, I've removed the CLI arguments, but used Cilium instead to limit the **egress** of WebDAV to 5MB/s.

This means that taking data **out** of ElfHosted is limited to 5MB/s, but putting data **in** will go as fast as the storage can handle (*we've seen about 40MB/s for one user today*)

!!! question "Why drop egress to 5MB/s?"
    It's relatively expensive to move data around, especially if using [ElfStorage][elfstorage] - it implies moving data from storage nodes (*disk i/o + bandwidth*), through rclone apps (*compute + bandwidth*), and out our reverse proxies (*more compute + bandwidth*). At $0.05/day for 10MB/s, a user is consuming 2-3x more resources than a user who's streaming 4K via Plex, but who's paying 3x as much.

    Users who want to use ElfHosted primarily to download content for shipping home, should use a [StorageBox][storagebox], rather than ElfStorage, since that way the data can be downloaded directly via FTP / SMB / SSH, without traversing ElfHosted infrastructure :thumbsup:

### Summary

As always, thanks for building with us - feel free to share suggestions, and your own ideas for new apps to add!

--8<-- "common-links.md"

[^1]: The big increase here is due to all the Zurg mounts!