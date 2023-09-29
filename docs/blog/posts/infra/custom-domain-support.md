---
date: 2023-09-29
categories:
  - CHANGELOG
tags:
  - uptime-kuma
title: Custom domains now available!
description: Would you prefer your apps to be accessible on your own domain name? We can do that now!
---
# Custom domains now available

Until today, all your ElfHosted services could only be served on `https://<user>-<app>.elfhosted.com`. After some development effort, we now have the pieces in place to allow you to access your apps on your own custom domain name, so instead of https://funkypenguin-uptime-kuma.elfhosted.com, you might prefer something like https://status.funkypenguin.co.nz (*see how it works?*)

The elfhosted.com URL will continue to work, and your dashboard will remain pointing to the ElfHosted link (*in case the DNS record goes away again*).

## How do custom domains work? 🙋‍♂️

How does this work? Like GitHub Pages, if you create a DNS CNAME record on your domain (`mattermost.spankypants.com`) and point it to your ElfHosted URL (`spankypants-mattermost.elfhosted.com`), we can request a LetsEncrypt certificate for that domain, validate it, and serve your app on that URL using our Traefik ingress controller.

## Which apps can get custom domains?

Custom domains don't make sense for all apps, and I've not tested the impact on SSO (*since auth cookies are domain-based*), but as I add the option to apps, you'll find custom domains available at https://store.elfhosted.com/product-category/custom-domains/, and instructions added to the docs for the various apps. 

For example, here are the instructions for [using a custom domain with Uptime Kuma](/app/uptimekuma/#can-i-use-my-own-domain-name)!

<!-- more -->

## WebP gets ownEd

As [highlighted in our Discord #general chat](https://discord.com/channels/396055506072109067/396055506663374849/1157007533630832773) this morning, there's a nasty WebP CVE being actively exploited, so here's your friendly reminder to ensure all of your software is up-to-date (*ElfHosted apps are automatically updated from upstream, and rolled out during the nightly maintenance window*)

## Deprovisioning bug deprovisioned

There was a logic flaw in the way our services are provisioned / deprovisioned, resulting in services not being properly deprovisioned after being cancelled (*free services!*). I've corrected this, but the deprovisioning logic ended up being a little too aggressive, and accidentally pruned a few active users whose daily subscriptions were on the verge of renewing! :facepalm:

If this was you - my apologies, the solution is simply to perform an early renewal from your [account page](https://store.elfhosted.com/my-account/). I've extended the grace time to 3 days, so there's an extra 48h for a service to be remediated before it gets deprovisioned. 

The next obvious task is to ensure that users are aware when their ElfBuckz balances are getting low, which is the next Wordpressy/dev task on my list!

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:material-dolphin: Healthy (subscribed) tenant pods | 430 [^1]
:fontawesome-regular-circle-user: Total subscribers | 43
:fontawesome-solid-hard-drive: Storageboxes mounted | 19
:material-sync: Rclone mounts | 11
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 1

### Summary

As always, thanks for building with us!

[^1]: You'll note almost a 50% drop compared to yesterday - this is the extent of the deprovisioning bug!

--8<-- "common-links.md"