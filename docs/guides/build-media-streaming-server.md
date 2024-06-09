---
title: How to build your own ElfHosted media server
description: ElfHosted provides all the apps you need to build, manage, consume and share your own media collection with no hardware, configuration, or management overhead
---

# Build your ElfHosted media streaming stack

ElfHosted provides all the apps you need to build, manage, consume and share your own media collection with no hardware, configuration, or management overhead.

Combine your own [storage](#add-storage), [content](#import-your-media), [providers](#add-usenet-providers), [indexers](#add-usenet-indexers), [trackers](#add-torrent-trackers) and [VPN](#get-a-vpn), and assemble your ideal media stack. 

New accounts get $10 credit, enough to trial a basic media server for ~1 month.

Pay only for what you use, and walk away without lock-in, anytime.

## Basic setup

### Create account, get $10 credit

[Sign up for an account](https://store.elfhosted.com/my-account/), and confirm your $10 [ElfBuckz][elfbuckz] (*store credit*) balance.

### Add streaming apps

Add one (or more) of these media-streaming apps:

* [Jellyfin][jellyfin] - Most popular free app
* [Plex][plex] - The most popular / polished app, but requires a VPN, and a paid PlexPass is required for some features like hardware transcoding.
* [Emby][emby] - Competitor to Plex, some features required paid "Emby Premier" subscription (*Jellyfin is an open-source fork of Emby*)

### Add storage

You get 100GB free "[ElfStorage][elfstorage]", but this won't be enough for any sort of media collection (*other than perhaps [books][calibre-web]!*) Pick one (or more) of the options below:

1. Add more [ElfStorage][elfstorage] at $0.20/TB/day (*so $6/TB/month*)
2. [Buy a storagebox][storagebox] from Hetzner
3. [Mount][store/storage] your existing (*rclone-compatible*) cloud storage

### Import your media

Now that you have some storage, import any media you'd like per the [migration instructions](/how-to/migrate/).

### Stream your media!

That's it! Use your media streamer to stream your media!

## Add media via NZBs (optional)

See [r/torrents](https://reddit.com/r/usenet) for general details about acquiring media using usenet.

### Add apps

Add one (or more) of these the NZB downloading apps:

1. [NZBget][nzbget] 
2. [SABnzbd][sabnzbd] 

And whichever of the following apps you'd like:

* [Radarr][radarr] (movies)
* [Sonarr][sonarr] (tv)
* [Lidarr][lidarr] (music)
* [Readarr][readarr] (books)
* [Mylar][mylar] (comics)

And to make it all nice and automatic, optionally add [Prowlarr][prowlarr] to sync indexers across all the above tools.

### Add Usenet providers

Choose one or more [usenet providers](https://www.reddit.com/r/usenet/wiki/providers/), and add them to your NZB client. Some of them offer free trial accounts.

!!! question "What Usenet provider should I choose?"
    If you have no idea what to chose, try [UsenetFarm](https://usenet.farm?a=elfhosted.com) (*affiliate link*), who offer a free 10GB trial to get you started.

Configure your usenet provider in your apps (above)

### Add Usenet indexers

To find content to download form Usenet, you'll need a indexer. See [here for a detailed collection](https://www.reddit.com/r/usenet/wiki/indexers/).

Add your indexers to Prowlarr, and sync to the apps, so that each app can query the indexers.

## Add media via Torrents (optional)

See [r/torrents](https://reddit.com/r/torrents) for general details about aquiring media using torrents.

### Get a VPN

If you want to use bittorrent clients, you'll need to bring your existing VPN subscription. If you don't yet **have** a VPN subscription, we can recommend [Private Internet Access](https://www.privateinternetaccess.com/pages/buy-a-vpn/1218buyavpn?invite=U2FsdGVkX18CE8WQvq-yt5OJ9UFpALCzci2Oz_px1uA%2CGuAfcPbAeh-UmP4KJ2uroADgSdY) (*referral link*), who are currently running a big 3-year special, and whose port-forwarding implementation is known to work well. 

!!! question "What VPN providers can you support?"
    Typically any providers which support WireGuard or OpenVPN.
    
    OpenVPN incurs higher subscription pricing due to its CPU usage compared to WireGuard.

### Add apps

Add one (or more) of these the torrent clients - pick the BYO VPN option specific to your VPN in the store:

1. [qBittorrent][qbittorrent] 
2. [Deluge][deluge] 
3. [ruTorrent][rutorrent] 

And whichever of the following apps you'd like:

* [Radarr][radarr] (movies)
* [Sonarr][sonarr] (tv)
* [Lidarr][lidarr] (music)
* [Readarr][readarr] (books)
* [Mylar][mylar] (comics)

And to make it all nice and automatic, optionally add [Prowlarr][prowlarr] to sync indexers across all the above tools.

### Add torrent trackers

You'll need to use a tracker to find .torrent files to download. Here's an [exhaustive list of public trackers](https://github.com/ngosang/trackerslist), and here's an [r/trackers wiki page explaining the difference between public and private trackers](https://www.reddit.com/r/trackers/comments/tw4ji0/tracker_faq_and_recommended_sites/), and where to go next.

Add your trackers to Prowlarr, and sync to the apps, so that each app can query the trackers.

## Other options

Here are a few less-mainstream sources for media aquisition:

### OpenBooks

Use [Openbooks][openbooks] to source ebooks from irc.irchighway.net

### Premiumize / Debrid

If you're a Premiumize.me / Real Debrid user, use [RDTClient][rdtclient] to manage your downloads

## Questions

### Why not just self-host?

[Self-hosting](https://reddit.com/r/selfhosted) is a fun and rewarding way to have complete control over your applications and content. If you're into self-hosting, check out [Funky Penguin's Geek Cookbook](https://geek-cookbook.funkypenguin.co.nz), specifically the [AutoPirate](https://geek-cookbook.funkypenguin.co.nz/recipes/autopirate/) stack.

Reasons **not** to self-host your media server may include:

* [x] You want to avoid the hardware / power costs involved
* [x] You want more reliability / uptime for your media, while your self-hosting / homelab is for tinkering
* [x] You want media management to **just work** (*we manage app updates, hardware, connectivity, security, etc.*)

## What now?

That's it, you're done. Hope into our [friendly Discord server][discord] if you have questions or suggestions!

--8<-- "common-links.md"
{% include 'testimonials.md' %}