---
title: ElfHosted KnightCrawler Addon (self hosted torrentio instance)
description: This guide describes how stream from Real-Debrid using your own Elf-Hosted torrentio instance
---
# How to use ElfHosted KnightCrawler Addon (self hosted torrentio instance)

This guide illustrates how to use our ElfHosted [Torrentio][torrentio] addon to stream content from debrid providers using [Stremio](https://stremio.com), avoiding torrentio.strem.fun outages and rate-limits.

## How does it work?

* ElfHosted maintains a KnightCrawler instance for our users' apps (*[Prowlarr][prowlarr], Iceberg, etc*) to use, without rate-limiting.
* This instance is publically available at ([rate-limited](https://github.com/elfhosted/infra/blob/main/traefik-middleware/middleware-rate-limit-public-stremio-addon.yaml)) at https://knightcrawler.elfhosted.com.
* Users can subscribe to their own instance of the addon (*still using the internal database*), with much more generous rate-limits

The advantages of this solution are:

* Use the highly-polished, multi-platform Stremio app
* Reduce the impact of Torrentio outages / rate-limits
* Share your addon with friends and family!

The disadvantages, of course, are:

* IP restriction - your Debrid provider's regular IP restriction policies apply, so be cautious of streaming from multiple locations simultaneously.
* Less history - we're working on more seeding, but our internal instance doesn't have the years of content that torrentio.strem.fm has.

!!! tip
    Consider our [Infinite Streaming Plex](/guides/media/stream-from-real-debrid-with-plex/) guide if you'd like to Proxy your Real-Debrid access behind [Zurg][zurg] so that you **can** stream simultaneously from multiple source IPs

## Requirements

* [x] An account with a supported Debrid provider

And from the [ElfHosted store][store]:

* [x] [KnightCrawler](https://store.elfhosted.com/product/knightcrawler/) subscription

## How to set it up

### Get the app

1. [Create an ElfHosted account](https://store.elfhosted.com/my-account)
2. [Subscribe to the torrentio](https://store.elfhosted.com/product/knightcrawler)
3. Log into your ElfHosted dashboard, at `https://<your username>.elfhosted.com`

### Install the Addon!

Navigate to **KnightCrawler** from your app dashboard (`https://<your username>.elfhosted.com`), add your debrid provider API key, and click "**Install**" to allow your OS to open the link in Stremio, or right-click the **Install** button, and copy the long `stremio://` URL, and paste it into your Stremio search bar:

![](/images/torrentio-install-stremio-addon)

Pick your content, and you should see results, like this:

![](/images/torrentio-what-to-expect.png)

## How do I get help?

1. For specific support re your ElfHosted configuration / account, see the [ElfHosted support options](/get-help/)

--8<-- "common-links.md"


{% include 'testimonials.md' %}