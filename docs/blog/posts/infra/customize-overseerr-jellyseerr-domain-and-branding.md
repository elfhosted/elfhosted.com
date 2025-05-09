---
date: 2024-01-02
categories:
  - CHANGELOG
tags:
  - overseerr
  - jellyseerr
title: Custom domains, themes, branding now available for Overseerr and Jellyseerr
description: Now you can brand Overseerr / Jellyseerr with your own domain name, and snazzy logos!
---
# Geek out with custom domain names / branding for Jellyseer / Overseerr

Do you :one: love showing off your Overseerr / Jellyseerr to the family and friends you share your media with?

Do you :two: also love owning your own domain name, like `iamacouchpotato.com`?

Now, you can combine these two passions with custom domain names for Overseerr and Jellyseerr! :trophy:

## Setup custom domain for Jellyseer / Overseerr

Create a custom CNAME on your domain name (`noobflix.iamacouchpotato.com`, for example), pointed to the FQDN of your elfhosted service (i.e. `noobflix-overseerr.elfhosted.com`), and the pick up a custom domain addon for [Overseerr](https://store.elfhosted.com/product/overseerr-custom-domain-addon/) or [Jellyseerr](https://store.elfhosted.com/product/jellyseerr-custom-domain-addon/).

Plug your CNAME in, push the button, and within a few minutes we'll have generated the appropriate SSL certificate for your fancy new `https://noobflix.iamacouchpotato.com` instance!

Read on for details re changing the default logos too!

<!-- more -->

## Changing Overseerr / Jellyseerr branding

You can also now customize the [Overseerr][overseerr] / [Jellyseerr][jellyseerr] logos, by simple replacing 2 PNG files, using [FileBrowser][filebrowser]. Details are in each app's specific page.

## Visit the Theme Park

But it's not just Overseerr / Jellyseer.. You can also customize the theming of **multiple** apps at once, using [Theme Park](https://store.elfhosted.com/product/theme-park/). Just pick the theme you want, and it'll be applied to all [supported apps](https://docs.theme-park.dev/themes/) in one go!

## VPNs now accept DNS names

Every so often, a new subscriber adds a custom VPN to a torrent client / Plex, and (quite reasonably) uses a DNS name for their `VPN_SERVER_IP` value. This would be a common requirement if your VPN server changes IPs occasionally, and our only workaround until now, has been to explicitly set the server IP when purchasing the product.

This is a PITA, since it means that if your VPN server changes IP, you have to remove and re-subscribe to the product, just to update the host resolution. 

DNS resolution is a [popular feature request for gluetun](https://github.com/qdm12/gluetun/issues/788), which we use to manage our BYOVPN products, but is not currently available given gluetun's priority on not doing **any** network traffic until the VPN is established.

Chicken :chicken: vs egg :egg:, right?

I've "[MacGyvered](https://www.urbandictionary.com/define.php?term=Macgyver)" a solution using an initContainer in our helm chart, so that we look up the IP address before even starting gluetun. This is working (*:wave: to my inadvertent test user*), so hopefully we won't see any more support requests from confused users whose VPNs won't start properly!

### Summary

As always, thanks for building with us!

--8<-- "common-links.md"

