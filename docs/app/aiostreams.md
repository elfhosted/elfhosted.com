---
title: How to host AIOStreams
slug: AIOStreams
description: AIOStreams is a popular Stremio Addon which combines search results from other addons
upstream: https://github.com/Viren070/AIOStreams
links:
- name: GitHub
  uri: https://github.com/Viren070/AIOStreams
sponsorship: 
- name: GitHub Sponsors
  uri: https://github.com/sponsors/Viren070
- name: Ko-Fi
  uri: https://ko-fi.com/Viren070
---

# {{ page.meta.slug }}

AIOStreams combines search results from popular addons, and makes all results able to be "proxy-streamed" using [MediaFlow Proxy][mediaflow-proxy]

{% include 'app.md' %}
{% include 'app_access.md' %}

### How to use AIOStreams

AIOStreams needs to know MediaFusion's API password, in order to properly encrypt your own configuration. When used with the [public MediaFusion](https://mediafusiono.elfhosted.com), this is preconfigured, but if you're using a private MediaFusion instance, you'll need to **tell** AIOStreams about the `api_password` value you set for MediaFusion.

To do so, use [ElfBot][elfbot], to run:

```bash
elfbot env aiostreams MEDIAFUSION_API_PASSWORD=<same api_password as mediafusion>
```

{% include 'app_footer.md' %}