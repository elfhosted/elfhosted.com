---
title: ElfHosted / self hosting that works like magic
description: ElfHosted runs popular self-hosted apps for you, behind polished automation and SSO
hide:
  - navigation # Hide navigation
  # - toc        # Hide table of contents
---
# 👋 Welcome to ElfHosted!

* [x] We run popular self-hosted apps for you, securely and reliably.
* [x] Attach your own storage or just use ours.
* [x] Only pay for the apps you need, swap them out when you want to, billed from $0.05/day

[See the apps :gift:](/apps/){ .md-button .md-button--primary } [Get started with FREE $10 credit](https://store.elfhosted.com){ .md-button .md-button--primary }


## Quick Start Guides

<div class="grid cards" markdown>

- :baby: **New user?**

    ---

     Here's [how to get started](/how-to/get-started/), stat!

- :pickup_truck: **Migrating from elsewhere?** 

    ---

    Got data / settings to bring across? [Here's a guide](/how-to/migrate/)

- :scientist: **How does this work?**

    ---

    What makes us [~~different~~ special](#elfhosted-vs-seedbox)?

- **Where my elfies :elf: at?**

    ---

    Join our friendly :fontawesome-brands-discord:{ .discord .lg .middle } [Discord](http://discord.elfhosted.com) community for help and fun!
</div>


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

### ElfHosted vs Seedbox

The following highly-detailed, meticulously researched[^2], and slightly-tongue-in-cheek table highlights the primary differences between ElfHosted and a seedbox. Provided those differences start with an "s":

Feature | ElfHosted | Seedbox | Notes
---------|----------|----------|----------
 :lock: Security | :white_check_mark: | :man_shrugging: | Your apps are protected by single sign-on (SSO). BYO VPN for torrenting apps.
 :vertical_traffic_light:Simplicity | :white_check_mark: | :scientist: | Preconfigured integrations between supported apps. Apps appropriately resourced for reasonable use.
 :tractor: Stability | :white_check_mark: | :fire: | Kubernetes, HA, and GitOps ensures it all "Just Works"
 :gift: Selection | :white_check_mark: | :t_rex: | Apps are added / updated frequently. Pay for only what you use.
 :floppy_disk: Storage | :white_check_mark: | :man_shrugging: | Bring your cloud storage, or buy from us!
 :people_with_bunny_ears_partying: Sexy | :white_check_mark: | :thumbs_down: | Built by geeks. In public. [Join us!][discord]

Question:

> "Why not just get a [seedbox](https://reddit.com/r/seedboxes)?"

Answer:

Yes, you could, and depending on what you want, it may be more customizable, cheaper, bigger, more performant, or more suitable for classic seeding / torrent racing / ratio-chasing. 

That's not necessarily our jam though, consider this alternative 👇

!!! note "How to build a classic seedbox on ElfHosted for 50c/day"

    You could buy the following apps:

    * [Plex][plex] (*$0.15/day*)
    * [Radarr][radarr] (*$0.05/day*)
    * [Sonarr][sonarr] (*$0.05/day*)
    * [Prowlarr][prowlarr] (*$0.05/day*)
    * [NZBGet][nzbget] (*$0.15/day*)

    For \$0.45/day (*\$13.50/month*), you have the basic Arrs, a download client, and a streaming client. For storage, you buy a 1TB [Hetzner Storagebox](https://www.hetzner.com/storage/storage-box) (*\$4/month*), and mount it to your apps (*\$0.05/day*).

    Now you have a basic seedbox, plus 1TB storage, for $0.50/day, and importantly, if ElfHosted fails, **you own your storage**, and you can migrate it / mount it to another provider 💪

[^1]: Defined as controlling and managing the apps I use, regardless of where they run
[^2]: Sarcasm, people! DYOR! :stuck_out_tongue:

--8<-- "common-links.md"