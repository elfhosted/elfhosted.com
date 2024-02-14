---
title: ElfHosted Annatar Addon (torrentio alternative) from $0.15/day, $10 free credit
description: This guide describes how stream from Real-Debrid using your own Elf-Hosted torrentio alternative, Annatar
---
# How to use ElfHosted Annatar Addon (torrentio alternative)

This guide illustrates how to use the [Annatar][annatar] addon to stream content from debrid providers using [Stremio](https://stremio.com), sourcing content from your **own** torrent indexer ([Jackett][jackett]), rather than relying on the (*often-overloaded*) torrentio addon!

!!! tip "New accounts get $10 credit, enough to run this stack for >2 months!"
    Our services are subscribed to in "[ElfBuckz][elfbuckz]", our in-store account credit. All new users get $10 ElfBuckz upon [account creation](https://store.elfhosted.com/my-account/), in order to "kick the tyres" :red_car: before commitment.

The advantages of this solution are:

* Use the highly-polished, multi-platform Stremio app
* Reduce the impact of Torrentio outages / rate-limits
* Customize your indexer results for your country, language, or even private tracker accounts

The disadvantages, of course, are:

* Limited retention - you've only "got" the content as long as your Debrid subscription is current
* IP restriction - your Debrid provider's regular IP restriction policies apply, so be cautious of streaming from multiple locations simultaneously.
* Jackett's results will appear more slowly in streamio, compared to pre-cached results from other providers

!!! tip
    Consider our [Infinite Streaming Plex](guides/media/stream-from-real-debrid-with-plex/) guide if you'd like to Proxy your Real-Debrid access behind [Zurg][zurg] so that you **can** stream simultaneously from multiple source IPs

## Requirements

* [x] [Real-Debrid][real-debrid] / AllDebrid account (*other providers planned*)

And from the [ElfHosted store][store]:

* [x] [Jackett](https://store.elfhosted.com/product/jackett/)
* [x] [Annatar](https://store.elfhosted.com/product/annatar/)

Additionally, if your trackers are behind Cloudflare DDOS protection (*and therefore harder to automatically search*), add [Flaresolverr](https://store.elfhosted.com/product/flaresolverr/).

Add the apps above to your cart, or subscribe to all of the above, as a bundle to make it easier, here:

[Get all the apps, bundled, for $0.15/day! :gift:](https://store.elfhosted.com/product/annatar-jackett-bundle){ .md-button .md-button--primary }

## How to set it up

### Get the apps

1. [Create an ElfHosted account](https://store.elfhosted.com/my-account?), receive $10 free [ElfBuckz][elfbuckz] credit
2. [Subscribe to the bundle](https://store.elfhosted.com/product/stremio-jackett-bundle), using your ElfBuckz
3. Log into your ElfHosted dashboard, at `https://<your username>.elfhosted.com`

### Setup Jackett

Navigate to **Jackett** from your app dashboard (`https://<your username>.elfhosted.com`), add your preferred chosen indexers (*illustrated below*), and note your Jackett API key

![](https://user-content.gitlab-static.net/60db7355ad98b15185cdae787149722196f9ddee/68747470733a2f2f692e696d6775722e636f6d2f6759504e45794d2e706e67)

!!! tip "Don't go overboard"
    Every indexer you add slows down your query responses, so prefer to add **small** amounts of **high-quality** indexers. The ones indicated above are recommended by the developer and have been observed to return results in < 3s.

If your indexers require [Flaresolverr][flaresolverr], you can add it to your existing subscription (*But you'll need to do "renew now" to avoid waiting for the 24h renewal cycle*)

Once Flaresolverr is added to your account, configure it in Jackett simply as `http://flaresolverr:8191`

### Setup Annatar

Annatar is configured using environment variables. While most parameters are pre-configured, Jackett API key and indexers are expected to vary per-user, and must be manually configured. Use [ElfBot][elfbot] to set your environment, by pasting a variation of the following into the [Filebrowser][filebrowser] console:

```
elfbot env annatar JACKETT_API_KEY=myapikeyisawesome
elfbot env annatar JACKETT_INDEXERS=eztv,kickasstorrents-ws,thepiratebay,therarbg,torrentgalaxy,yts
```
!!! tip
    (You can re-run the commands to overwrite previous values, and you can confirm success by examining the `elfbot-annatar` ConfigMap using [Kubernetes Dashboard][kubernetes-dashboard].

### Install the Addon!

Click "**Install**" to allow your OS to open the link in Stremio, or right-click the **Install** button, and copy the long `stremio://` URL, and paste it into your Stremio search bar.

![](/images/annatar-install-addon.png)

A search will return results in a few seconds:

![](/images/stremio-jacket-example-search.png)

## How do I get help?

1. Annatar is a new project under active development. File issues [here](https://gitlab.com/stremio-add-ons/annatar/-/issues).
2. For specific support re your ElfHosted configuration / account, see the [ElfHosted support options](/get-help/)

--8<-- "common-links.md"