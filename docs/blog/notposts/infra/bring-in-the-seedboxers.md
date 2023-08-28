---
date: 2023-07-21
categories:
  - build-in-public
tags:
  - infra
title: Seedboxers unpack more bugs
description: Some improvements courtesy of the r/seedboxes betatesters
---

# r/seedboxes invasion

After the last few days of relative stablity, I posted an [introduction to the r/seedboxes subreddit](https://www.reddit.com/r/seedboxes/comments/1543vct/new_vendor_introduction_elfhosted_perapp_perday/), inviting more testers and feedback.

Here's the impact of this, in graph form :grin:

![Prometheus graph showing pod count over 2 day period, from stable 270 to a recent peak of 340](/images/blog/pod-count-20-jul-2023.png)

And here's a brief summary of the bugs squashed and improvements made...

<!-- more -->

## Bugz

* :bug: Password resets weren't working. Turns out the [MailPoet Wordpress plugin](https://wordpress.org/plugins/mailpoet/) (*which I setup to "improve" email sending*), was sending email from the wrong domain (*funkypenguin.co.nz instead of elfhosted.com*), and breaking DMARC.
* :bug: PayPal happily plasters its "Pay with PayPal" button all over the place, even when paying for services with ElfBuckz, which can lead to user confusion or worse, actually **paying** $0.05 for a service, only to find it removed again the next day when PayPal fails to process the renewal!

## Improvementz

* :white_check_mark: Instructing users to create an account in order to get $10 ElfBuckz was too clunky, and the username-validation plugin doesn't provide enough output on account creation. Instead, I created a "$10 ElfBuckz TopUp" product, with a $10-off coupon code (`ELFELFBABY`), so that users can just buy the topup, and create an account at checkout - a smoother user experience.
* :white_check_mark: Users were confused about the "manually provisioned rclone mount", assuming it to always be a manual process. I [updated the product](https://store.elfhosted.com/product/rclone-mount-other-request-new-product/) to indicate that it's simply a conversation about what parameters are required in order to create a new auto-provisioned rclone mount product.
* :white_check_mark: After feedback, I "hid" all 15 BYOVPN variations of the torrent clients, replacing them with an "app group" product per-client, to tidy up the "Download Media" category, which now fits on a single page!

## Next Up

* [ ] Add a link on the store user account page to the app dashboard
* [ ] Send email to user with link to their dashboard
* [ ] Make checkout fields work better with browser auto-fill (*is this a Woocommerce/Wordpress issue?*)
* [ ] Add Wordpress caching plugin to reduce load issues (*at one point, the DO node running Wordpress stopped responding for 5 min!*)

### Summary

Thanks for building with us - stay tuned!

--8<-- "common-links.md"

