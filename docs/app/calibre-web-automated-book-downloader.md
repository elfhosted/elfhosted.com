---
title: 🧝 Hosted Calibre-Web 🦸
slug: Calibre-Web-Automated-Book-Downloader
description: Calibre-Web-Automated Book Downloader is an intuitive web interface for searching and requesting book downloads, designed to work seamlessly with
works_with:
- Calibre-Web
upstream: https://github.com/calibrain/calibre-web-automated-book-downloader
---

# {{ page.meta.slug }}

Calibre-Web-Automated Book Downloader is an intuitive web interface for searching and requesting book downloads, designed to work seamlessly with [Calibre-Web-Automated][calibre-web]. This project streamlines the process of downloading books and preparing them for integration into your Calibre library.

{% include 'app.md' %}

{% include 'app_access.md' %}

## How do I use it?

### Where are my books?

By default, books are downloaded to `/tmp`, which is ephemeral, and will be flushed upon app restart. (*You can, however, download the book locally via your browser*).

To integrate CWA-Book-Downloader with your ElfHosted Calibre-Web (*[rclone-attached](/how-to/use-rclone/) storage requiredh*), you'll need to set the `INGEST_DIR` environment variable to match what CWA expects, using [ElfBot][elfbot], like this:

```
elfbot env calibre-web-automated-book-downloader INGEST_DIR=/storage/rclone/whateverpath
```

{% include 'app_footer.md' %}