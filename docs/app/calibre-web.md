---
title: 🧝 Hosted Calibre-Web 🦸
slug: Calibre-Web
description: Calibre-Web is a web app providing a clean interface for browsing, reading and downloading eBooks using a valid Calibre database.
works_with:
- Readarr
- Calibre
upstream: https://github.com/janeczku/calibre-web
sponsorship: 
- name: PayPal
  uri: https://www.paypal.com/paypalme/calibreweb
---

# {{ page.meta.slug }}

Calibre-Web is a web app providing a clean interface for browsing, reading and downloading eBooks using a valid [Calibre][calibre] database.

{% include 'app.md' %}

{% include 'app_access.md' %}

## How do I use it?

The default credentials are:

* user: `admin`
* pass: `admin123`

### Set database location

If you're using Calibre-Web in combination with Calibre (*for Readarr integration, for example*), you can configure Calibre-Web to store the database independently of the book files, as follows:

![](/images/calibre-web-database-configuration.png)

([Calibre][calibre]'s database is stored in `/calibre/Calibre Library`, from the perspective of Calibre-Web)

### Basic settings

For conversion between ebook formats, set the following in your config:

![](/images/calibre-web-basic-configuration.png)


{% include 'app_footer.md' %}