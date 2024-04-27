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
* [x] Attach your own storage or just use ours.
* [x] Only pay for the apps you need, swap them out when you want to, billed from $0.10/day

[See the apps :gift:](/apps/){ .md-button .md-button--primary } [Get started with FREE $10 credit :moneybag:](https://store.elfhosted.com){ .md-button .md-button--primary }

## NEW! Infinite storage / streaming with Plex and Debrid

Recently (2024), a selection of our apps used to integrate media streaming (Plex) and downloaders (Real-Debrid) have been popular. Here's a quick guide..

<div class="grid cards" markdown>

- :gift_heart: **Get your own private Stremio Addons!** 

    ---

    Customize your Stremio experience with your own instance of popular [Stremio Addons](/stremio-addons)!

- :people_with_bunny_ears_partying: **Simultaneously Stream from Stremio** 

    ---

    Need to stream torrents or consolidate your Debrid downloads from one source IP? [Use Stremio Server](/guides/media/stream-from-real-debrid-with-stremio-from-with-multiple-ip-addresses-simultaneously/)!

- :tv: **Simply stream from Debrid with Plex**

    ---

     Here's all you need for [infinite streaming from Real Debrid with Plex](/guides/media/stream-from-real-debrid-with-plex/), stat!

- :scientist: **Advanced Debrid streaming with Aars** 

    ---

    Want to use familiar tools for advanced searching / quality? Here's the [Advanced guide to infinite streaming / storage](/guides/media/stream-from-real-debrid-with-plex-radarr-sonarr-prowlarr/)!
</div>

## What users say..

> "Just wanted to check in here and let \@Darth-Penguini and anyone/everyone else know...WOW. I have been struggling with storage for years, maintenance of Docker containers, upkeep, all of it. Elfhosted is so freeing. It's an amazing service that I hope to be a member of for a long, long time!"  - \@Fingers91 (*[Discord](https://discord.com/channels/396055506072109067/1118645576884572303/1233758587835383908)*)

> "I just have to say, I am an incredibly satisfied customer. I had been collecting my own content for nearly 20 years. Starting off with just a simple external HD before eventually graduating to a seedbox with 100TB of cloud storage attached and fully automated processes with Sonarr and Radarr . However, the time came when the glory days of unlimited Google Drive storage ended. I thought my days of having my full collection at my fingertips via :plex: were behind me, until I found Real-Debrid and ElfHosted. 
> 
> Now I essentially have the exact same access to content as I had before, but even better. Superior support and community involvement. Content is available almost immediately after being identified. A plethora of tools at my fingertips that give me more control and automation than ever before. Wonderfully well done and impressive! I am looking forward to being a customer for a very long time! Massive kudos to @funkypenguin 🤟 - \@BSM (*[Discord](https://discord.com/channels/396055506072109067/1118645576884572303/1233057353390231655)*)

> "I would recommend ElfHosted to anyone. It has been great so far and made life a lot easier than running my own setups. If you’re in the fence give them a try and help support this great community." - [Zestyclose_Teacher20](https://old.reddit.com/r/StremioAddons/comments/1b5wqdx/elfhosteds_elfdisclosure_report_for_feb_2024/ktayicr/)

> "thanks for the help and must say this is the best host I every had for my server 🙂 10/10 🙂 All other places I have try have I got a lot buff etc. Your host can even give me full power on a 4K Remux on 200GB big movie file . That's damn awesome 😄" - \@tjelite (*Discord*)


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