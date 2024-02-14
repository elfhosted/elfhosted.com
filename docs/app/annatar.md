---
title: ElfHosted Annatar from $0.05/day with $10 free credit
slug: Annatar
description: Annatar is the fastest just-in-time torrent/debrid search add-on for Stremio, providing results in under 3s
works_with:
- Jackett
upstream: https://gitlab.com/stremio-add-ons/annatar
sponsorship: 
- name: Ko-fi
  uri: https://ko-fi.com/annatar
---

# {{ page.meta.slug }}

Annatar is the fastest just-in-time torrent/debrid search add-on for Stremio, providing results in under 3s.

{% include 'app.md' %}

Annatar searches torrent and debrid sites for cached content to provide instantly available content for Stremio. Results from Annatar typically arrive in 3s or less. Annatar achieves its speed by using several fanout queries and map-reduce functions to gather the fastest and most accurate results using [Jackett][jackett] APIs.

From the [developer](https://gitlab.com/stremio-add-ons/annatar):

> There are other plugins that are similar to Annatar, but my experience with them has been not great. Results typically take over 10s which is far from ideal. Annatar is fast enough that the short delay does not bother me. 
> Content is cached using \[redis]. This includes debrid links, Torrent metadata, and Jackett search results.
> Cache is built based on user-requests. Each new imdb id will be cold requested from Jackett, Cinemeta, and Debrid. Subsequent requests will retrieve cache (given some TTLs depending on arbitrary logic).

{% include 'app_access.md' %}

## How do I use it?

### Setup Jackett

Annatar relies on [Jackett][jackett] for returning results, so start with adding your indexers to Jackett, as illustrated below:

![](https://user-content.gitlab-static.net/60db7355ad98b15185cdae787149722196f9ddee/68747470733a2f2f692e696d6775722e636f6d2f6759504e45794d2e706e67)

### Configure your environment

Annatar is configured using environment variables. While most parameters are pre-configured, Jackett API key and indexers are expected to vary per-user, and must be manually configured. Use [ElfBot][elfbot] to set your environment, by pasting a variation of the following into the [Filebrowser][filebrowser] console:

```
elfbot env annatar JACKETT_API_KEY=myapikeyisawesome
elfbot env annatar JACKETT_INDEXERS=eztv,kickasstorrents-ws,thepiratebay,therarbg,torrentgalaxy,yts
```

!!! tip
    (You can re-run the commands to overwrite previous values, and you can confirm success by examining the `elfbot-annatar` ConfigMap using [Kubernetes Dashboard][kubernetes-dashboard].

Now visit your Annatar URL from your dashboard, enter your debrid provider API key, pick your indexers (may as well pick 'em all!), and click `Install`!

{% include 'app_footer.md' %}