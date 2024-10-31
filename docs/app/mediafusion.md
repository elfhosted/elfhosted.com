---
title: Install ElfHosted MediaFusion Stremio Addon
slug: MediaFusion
description: MediaFusion is a Stremio Addon, which is especially popular for watching Tamil, Hindi, Malayalam, Kannada, English, and dubbed movies & series
upstream: https://mediafusion.elfhosted.com
links:
- name: GitHub Repo
  uri: https://github.com/mhdzumair/MediaFusion
---

# {{ page.meta.slug }}

MediaFusion is a Stremio Addon, which is especially popular for watching Tamil, Hindi, Malayalam, Kannada, English, and dubbed movies & series. ElfHosted provides a public, community version of MediaFusion at https://mediafusion.elfhosted.com (*with individual and global rate-limits*), and per-user, private, un-rate-limited instances.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### Set the API password

Since MediaFusion v4, every instance **must** include an `api_password` ENV var, to secure the instance from unwanted public tampering. 

Every ElfHosted instance defaults its API password to `changemeelfie`, but you can (and should) reset this using [ElfBot][elfbot], by running:

```
elfbot env mediafusion api_password=whateveryouwant
```

{% include 'app_footer.md' %}