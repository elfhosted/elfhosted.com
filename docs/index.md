---
title: ElfHosted / self hosting that works like magic
description: ElfHosted runs popular self-hosted apps for you, behind polished automation and SSO
hide:
  - navigation # Hide navigation
  # - toc        # Hide table of contents
---
# 👋 Welcome to ElfHosted!

![](/images/logo.png){ align=left }

* [x] We run popular self-hosted apps for you, securely and reliably.
* [x] Attach your own storage

[See the apps :gift:](/apps/){ .md-button .md-button--primary } [Get started with the guides :books:](/guides/media/){ .md-button .md-button--primary }

## NEW! Infinite storage / streaming with Plex and Debrid

Recently (2024), a selection of our apps used to integrate media streaming ([Plex][plex]) and downloaders (Real-Debrid) have been popular. Here's a quick guide..

<div class="grid cards" markdown>

- :gift_heart: **Get your own private Stremio Addons!** 

    ---

    Customize your Stremio experience with your own instance of popular [Stremio Addons](/stremio-addons)!

- :people_with_bunny_ears_partying: **Simultaneously Stream from Stremio** 

    ---

    Need to stream torrents or consolidate your Debrid downloads from one source IP? [Use Stremio Server](/guides/media/stream-from-real-debrid-with-stremio-from-with-multiple-ip-addresses-simultaneously/) or [Comet][comet]! :comet:

- :tv: **Simply stream from Debrid with Plex**

    ---

     Here's all you need for [infinite streaming from Real Debrid with Plex](/guides/media/stream-from-real-debrid-with-plex/), stat!

- :scientist: **Advanced Debrid streaming with Aars** 

    ---

    Want to use familiar tools for advanced searching / quality? Here's the [Advanced guide to infinite streaming / storage](/guides/media/stream-from-real-debrid-with-plex-radarr-sonarr-prowlarr/)!
</div>

{% include 'testimonials.md' %}

## The back-story

> I love self-hosting[^1], and have been publishing [guides on building self-hosting platforms and running apps](https://geek-cookbook.funkypenguin.co.nz) since 2016. Over time, I've updated my own platform from [Docker Swarm](https://geek-cookbook.funkypenguin.co.nz/docker-swarm/) to [Kubernetes](https://geek-cookbook.funkypenguin.co.nz/kubernetes/) (*several iterations*).

> Somewhere along the way, building automated / resilient / scalable systems in Kubernetes became my [DayJob(tm)](https://www.funkypenguin.co.nz/work-with-me), and I spent 2 years consulting/co-investing in a seedbox provider. 

> When this provider shut down, I took the opportunity to take my self-hosting to the next level. I leveraged what I'd built / learned over those past 2 years to build ElfHosted - a multi-tenant, resilient, automated and scalable app hosting platform, running on "budget" bare-metal cloud hardware. I wanted to be able to rapidly deploy new self-hosted apps in a templatized way, and I wanted to invite other geeks to join in / observe the process.

> \- David (@funkypenguin)

## But.. but..

### ElfHosted vs Selfhosting

Question:
> "Why wouldn't I just run the app myself?"

Answer:

Totally valid. Here are some guides I wrote for doing just that on [Docker Swarm](https://geek-cookbook.funkypenguin.co.nz/docker-swarm/) or [Kubernetes](https://geek-cookbook.funkypenguin.co.nz/kubernetes/).

ElfHosted is for users (*like me, post-kids!*) who don't necessarily have the time / inclination to run (*and maintain!*) certain apps locally, want it to "Just Work(tm)".

[^1]: Defined as controlling and managing the apps I use, regardless of where they run

--8<-- "common-links.md"