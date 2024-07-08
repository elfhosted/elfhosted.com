---
title: Play media from WebDAV using Stremio
slug: davio
description: Davio is a Stremio addon which streams your WebDAV-accessible content
upstream: https://github.com/arvida42/davio
# sponsorship: 
# - name: Ko-fi
#   uri: https://ko-fi.com/annatar
---

# {{ page.meta.slug }}

Davio is a Stremio addon which streams your WebDAV-accessible content

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### Debrid content

To stream your Real-Debrid / Debrid-Link content, pick these from your `WebDAV provider` field, and enter your credentials

### Custom content

Since Davio can stream content from **any** accessible WebDAV endpoint, you can also stream any content from your ElfHosted-mounted storage, including [ElfStorage][elfstorage], [Hetzner Storageboxes][storagebox], or any other [rclone-compatible storage](https://store.elfhosted.com/product-category/storage).

You'll then pick `Custom` as your WebDAV provider, and enter your ElfHosted WebDAV details, as illustrated below:

![](/images/davio-webdav.png)

{% include 'app_footer.md' %}