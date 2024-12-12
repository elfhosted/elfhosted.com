---
title: Ultimate guide to Plex, AllDebrid, and Riven
description: The following page guides the user through the process of establishing an ElfHosted stack using Plex, with media stored on AllDebrid, and with content acquisition managed by Riven
hide:
  - navigation # Hide navigation
  # - toc        # Hide table of contents
---
# Ultimate guide to Plex, AllDebrid, and Riven

The following page guides the user through the process of establishing an ElfHosted stack using Plex, with media stored on AllDebrid, and with content acquisition managed by Riven.

!!! note "BYO VPN required"
    Because AllDebrid won't work with datacenter IPs, this setup requires a user to bring their own (BYO) VPN provider credentials. While any gluetun-supported provider can **technically** work, we've had the best experience with [PrivateInternetAccess][pia], which can usually be purchased for < $2/month on a 3-year term.

The stack described below is available in all of our [regular stack bundles](https://store.elfhosted.com/product-category/streaming-bundles/), and free trials are available on the [starter](https://store.elfhosted.com/product/starter-plex-alldebrid-riven/) and [hobbit](https://store.elfhosted.com/product/hobbit-plex-alldebrid-riven/) bundles.

[Get your 7 day free trial!](https://store.elfhosted.com/product/starter-plex-alldebrid-riven/){ .md-button .md-button--primary }

{% include 'scribe_gluetun.md' %}
{% include 'scribe_plex_claim.md' %}
{% include 'scribe_plex_libraries_symlinks.md' %}
{% include 'scribe_alldebrid_riven.md' %}

--8<-- "common-links.md"


{% include 'testimonials.md' %}