---
title: Streamio (Server) with Real-Debrid from multiple IP addresses simultaneously
description: This guide describes how use ElfHosted's Stremio Server subscription to stream from Real-Debrid using Stremio, from multilpe source IP addresses simultaneously
---
# How to stream from Real-Debrid with Stremio to multiple source IP addresses

This guide illustrates how to use the [Stremio Server][stremio-server] to stream content from debrid providers using [Stremio](https://stremio.com), to multiple Stremio clients on multiple source IPs, simultaneously. 

Note that while streaming/transcoding torrents works across all (tested) Stremio clients, the streaming of Debrid/HTTP streams is only [currently supported](#client-compatibility) in v5 of https://web.strem.io, and the [ElfHosted instance][stremio-web] of the same.

!!! tip
    This is a lightweight alternative to the [Infinite Streaming Plex](guides/media/stream-from-real-debrid-with-plex/) guide. The Infinite Streaming [Plex][plex] solution utilizes [Zurg][zurg] to permit simultaneous streams from multiple source IPs, but doesn't integrate as easily into the existing [Stremio Addons](/stremio-addons/) ecosystem.

The advantages of this solution are:

* Use the highly-polished, multi-platform Stremio app
* Isolate all your Stremio traffic behind your own VPN subscription
* Safely play debrid content from multiple clients / sources without triggering Debrid simultaneous-IP bans

The disadvantages are:

* All streams are played via ElfHosted's infrastructure, so it's inevitably not as speedy / performant as a "native" Stremio install, and throughput / transcodes are constrained. (*Currently 2 concurrent transcodes with 100Mbps throughput limit*)
* IP restriction - your VPN-connected Stremio Server still counts as an debrid source IP, so if you tried to stream media from any **other** source (*like an unconfigured Stremio client, or [Plex via Zurg](guides/media/stream-from-real-debrid-with-plex/)*), you'd still run into issues. The safest solution would be to use the Stremio Server for **all** your Stremio + Debrid activity.

## Requirements

Pre-existing:

* [x] An existing VPN subscription with a[ supported provider](https://github.com/qdm12/gluetun-wiki/tree/main/setup/providers)
* [x] [Stremio Server](https://store.elfhosted.com/product-category/consume-media/stremio-server) from the ElfStore

Optionally:

* [ ] [Stremio-Jackett Bundle](https://store.elfhosted.com/product/stremio-jackett-bundle) (*supports direct torrenting without Debrid*)
* [ ] [Stremio Web](https://store.elfhosted.com/product/stremio-web/)
* [ ] Any other [Stremio Addons](/stremio-addons/) you'd like

!!! question "What if I don't have a VPN?"
    [PrivateInternetAccess][pia] is known to work well with our solution, and is a whitelisted provider for RealDebrid - you can pick up a subscription for < $2/month with a multi-year commitment.

## How to set it up

### Get the apps

1. [Create an ElfHosted account](https://store.elfhosted.com/my-account)
2. [Subscribe to an instance of Stremio Server](https://store.elfhosted.com/product-category/consume-media/stremio)
3. Log into your ElfHosted dashboard, at `https://<your username>.elfhosted.com`

### Setup Stremio

Navigate to **Stremio Server** from your app dashboard (`https://<your username>.elfhosted.com`) - the Stremio Web UI will automatically configure your streaming server.

Confirm the setup by navigating to **Settings** --> **Streaming**, and configure per the screenshot below - set your transcoding profile to `vaapi-renderD128`.

![](/images/stremio-server-setup-1.png)

Now stream your media! You can check your pod logs using [Kubernetes Dashboard][kubernetes-dashboard] to confirm it's being correctly transcoded.

{% include 'stremio_server_faq.md' %}

## How do I get help?

For specific support re your ElfHosted configuration / account, see the [ElfHosted support options](/get-help/)

[^1]: Other than an entrypoint change to enforce waiting for a VPN to be established before running the server!

--8<-- "common-links.md"