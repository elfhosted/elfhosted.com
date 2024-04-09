---
title: Stremio Web - Hosted, free trial
slug: Stremio-Web
description: Stremio Web is an instance of the Stremio web client
upstream: https://github.com/Stremio/stremio-web
links:
- name: Subreddit (Official)
  uri: https://www.reddit.com/r/Stremio/
- name: r/StremioAddons
  uri: https://www.reddit.com/r/StremioAddons
---

# {{ page.meta.slug }}

Stremio is a modern media center that's a one-stop solution for your video entertainment. You discover, watch and organize video content from easy to install addons. Stremio Web is a self-hostable instance of the WebUI, which can be used in combination with [Stremio Server][stremio-server] or as a standalone client.

!!! question "What's the relationship to Official Stremio?"
    The ElfHosted Stremio Web subscription is simply the hosting of an [un-modified](https://github.com/geek-cookbook/containers/blob/main/apps/stremio-web/Dockerfile) instance of the [publically available](https://github.com/Stremio/stremio-web) docker image, exactly as distributed by Stremio, and subject to the same [terms and conditions](https://www.stremio.com/tos) as any other Stremio installations.

    There's nothing proprietary to the solution, and the subscription price is for the **hosting** components of the service (*CPU, RAM, bandwidth, etc*), and not the Stremio app itself, nor the content consumed by the user.

{% include 'app.md' %}
{% include 'app_access.md' %}
{% include 'app_footer.md' %}
