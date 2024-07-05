---
title: Proxy your RealDebrid Stremio experience with Comet!
slug: Comet
description: Comet ☄️ is a Stremio addon with super-powers! 🦸 It can search public DMM hashlists, and it can proxy your streams, bypassing RealDebrid's one-ip-per-account limitation!
works_with:
- Jackett
upstream: https://gitlab.com/stremio-add-ons/annatar
sponsorship: 
- name: Ko-fi
  uri: https://ko-fi.com/annatar
---

# {{ page.meta.slug }}

Comet is an innovative new Stremio addon which differentiates itself from the existing [Stremio Addons][stremio-addons] with the superpowers of:

* :white_check_mark: Scraping all public DMM content
* :white_check_mark: Proxying Debrid requests, allowing you to use multiple IPs with one RD account!

!!! tip "Comet gets revenue sharing! :heart:"
    Comet is an "Elf-illiated" Premium [Stremio Addon][stremio-addons] - the developer maintains an active support channel ([#elf-comet](https://discord.com/channels/396055506072109067/1256404447723126916)) in our [Discord][discord] community, the app itself is tuned to work perfectly with ElfHosted "out-of-the-box", and 30% of your subscriptions are contributed to the developer!

{% include 'app.md' %}

{% include 'app_access.md' %}

## How do I use it

### Environment variables

Comet is configured using environment variables. You can use either [ElfBot][elfbot] or [Kubernetes Dashboard][kubernetes-dashboard] to set your environment variables.

### With Prowlarr

Set the following environment variables:

```
elfbot env comet INDEXER_MANAGER_TYPE=jackett
elfbot env comet INDEXER_MANAGER_URL=http://jackett:9117
elfbot env comet INDEXER_MANAGER_API_KEY=<YOUR JACKETT API KEY>
elfbot env comet INDEXER_MANAGER_INDEXERS='["EXAMPLE1_CHANGETHIS", "EXAMPLE2_CHANGETHIS"]
```

(*Or edit the `elfbot-comet` ConfigMap in Kubernetes Dashboard*)

### With Jackett

```
elfbot env comet INDEXER_MANAGER_TYPE=prowlarr
elfbot env comet INDEXER_MANAGER_URL=http://prowlarr:9696
elfbot env comet INDEXER_MANAGER_API_KEY=<YOUR PROWLARR API KEY>
elfbot env comet INDEXER_MANAGER_INDEXERS='["EXAMPLE1_CHANGETHIS", "EXAMPLE2_CHANGETHIS"]
```

(*Or edit the `elfbot-comet` ConfigMap in Kubernetes Dashboard*)

!!! tip
    (You can re-run the commands to overwrite previous values, and you can confirm success by examining the `elfbot-annatar` ConfigMap using [Kubernetes Dashboard][kubernetes-dashboard].

Now visit your Comet URL from your dashboard, enter your debrid provider API key, pick your indexers (*may as well pick 'em all!*), and click `Install`!

### Debrid Stream Proxying

Here's how Debrid Stream Proxying works

=== ":nerd: Normal mode"

    Here's how Comet works as a "regular" Stremio addon:

    ```mermaid
    sequenceDiagram
        Stremio->>+Comet: Search movie
        Comet->>+Indexer: Search movie
        Indexer->>Comet: Search Results
        Comet->>Stremio: Search results
        Stremio->>Comet: Play movie
        Comet->>RealDebrid: Get link
        RealDebrid->>Comet: Here's link
        Comet->>Stremio: Here's link
        Stremio->>RealDebrid: Play link
        RealDebrid->>Stremio: Enjoy!
    ```

    Stremio searches/requests content via Comet, and Comet returns an "unrestricted" RD download link to Stremio, which uses that link to stream the content.

=== ":superhero: Stream Proxy mode"

    But **here's** how Comet works in Proxy Stream mode:

    ```mermaid
    sequenceDiagram
        Stremio->>+Comet: Search movie
        Comet->>+Indexer: Search movie
        Indexer->>Comet: Search Results
        Comet->>Stremio: Search results
        Stremio->>Comet: Play movie
        Comet->>RealDebrid: Get link
        RealDebrid->>Comet: Here's link
        Comet->>Stremio: Here's proxy link
        Stremio->>Comet: Play proxy link
        Comet->>RealDebrid: Play link
        RealDebrid->>Comet: Enjoy!
        Comet->>Stremio: Enjoy!
    ```

    Unlike regular mode, in Proxy Stream mode, Comet doesn't return the unrestricted download link to Stremio, rather it returns a **Comet** download link, and when Stremio requests that link, Comet downloads the **real** dowload link from RealDebrid, and serves it to Stremio.

    Thus, **all** interaction with RealDebrid is done from Comet. Stremio talks to Comet exclusively, and streams the content **through** Comet. Therefore, only a single source IP is in use, from the perspective of Stremio!

!!! danger "Use comet consistently"
    If you're going to use Comet in Stream Proxy mode, remember that ElfHosted will be the IP that RealDebrid sees when you stream from Stremio. If you use other addons to stream on one device, while using Comet on another, you'll again trigger the multiple-source-IPs problem.

    In Stream Proxy mode, use Comet **exclusively, everywhere**!

{% include 'app_footer.md' %}