---
title: ElfHosted Jackettio from $0.05/day with $10 free credit
slug: Jackettio
description: Jackettio is a Stremio addon which searches that resolve streams using Jackett and Debrid. It seamlessly integrates with private trackers.
works_with:
- Jackett
- Flaresolverr
upstream: https://github.com/arvida42/jackettio
# sponsorship: 
# - name: Ko-fi
#   uri: https://ko-fi.com/annatar
---

# {{ page.meta.slug }}

Jackettio is a Stremio addon which searches that resolve streams using Jackett and Debrid. It seamlessly integrates with private trackers.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### Setup Jackett

Jackettio relies on [Jackett][jackett] for returning results, so start with adding your indexers to Jackett.

### Configure your environment

Jackettio is configured using environment variables. While most parameters are pre-configured, the Jackett API key will vary per-user, and must be manually configured. Use [ElfBot][elfbot] to set your environment, by pasting a variation of the following into the [Filebrowser][filebrowser] console:

```
elfbot env jackettio JACKETT_API_KEY=myapikeyisawesome
```

!!! tip
    (You can re-run the commands to overwrite previous values, and you can confirm success by examining the `elfbot-jackettio` ConfigMap using [Kubernetes Dashboard][kubernetes-dashboard].

Now visit your Jackettio URL from your dashboard, enter your debrid provider API key, pick your indexers (may as well pick 'em all!), and click `Install`!

{% include 'app_footer.md' %}