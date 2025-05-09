---
date: 2024-07-12
categories:
  - infra
tags:
  - CHANGELOG
title: Trials are gone, Elf-ferrals are back!
description: With the remove of trials, we gain referrals and bundle-hopping!
---

# Trials are gone, Elf-ferrals are back!

!!! warning "Old / daily subscriptions will sunset from 1 Aug. Take action as described below"

    We have a new pricing model / bundle structure which requires resubscriptions (*the store can't migrate daily to monthly subscriptions for us*). Unless you take action described [here](/blog/2024/07/10/pricing-model-updated/), your ElfHosted subscriptions **will** stop working some time after 1 Aug 2024. 

    Details [here](/blog/2024/07/10/pricing-model-updated/)!

## Trials are gone

Further to the [original announcement](/blog/2024/07/10/pricing-model-updated/), it quickly became clear that the 7-day trials were more trouble than they were worth. A trial period prevented users from using their ElfBuckz as part-payment on a subscription, as well as "bundle-hopping" between different subscriptions.

Trials also represented an abuse risk - Wordpress doesn't have a way to prevent a user from trialing, cancelling, and re-trialing to continuously extend a trial indefinitely.

So, no more trials. Instead, we'll offer a 14-day refund based on a conversation - if a user is unhappy with the service, and we can't make them happy, we'll refund the unused portion of their subscription, within the first 14 days.

Oh, and the other issue with trials was that they made the referral process exploitable, so...

## Referrals are back!

With the transition to monthly billing, and the removal of trials, it's now safe to re-instate the Elf-erral program! 

Here's the deal - every user you refer with [your unique referral code](https://store.elfhosted.com/my-account/myreferrals) gets $5 off their first order, and **you** get a $5-off coupon! (*\$10 free ElfBuckz, reborn!*)

## Storage mounts are free

Everything in the store now falls into one of the [5 product tiers](/open/pricing/), and I couldn't work out where storage mounts fitted in.

Rather than overcomplicate the product tiers, **all storage mounts are now free**, with an initial $9 setup fee (*both to cover support and to deter abuse*).

If you're migrating from an older subscription to a monthly one, drop us a [note][elf-support], we'll refund the setup fee for your storage mounts.

And there's more...

<!-- more -->

## TorBox mounts added

Speaking of storage, there's a [RealDebrid service degradation](https://x.com/RealDebrid/status/1811459211760439762) going on currently, and we've just added a [new product](https://store.elfhosted.com/product/torbox-mount) to mount your [TorBox](https://torbox.app/) storage to `/storage/torbox`. We're also now listed on the [TorBox integrations page](https://torbox.app/integrations)!

!!! note 
    Note that TorBox are working through their own storage upgrades currently, so there's some scheduled degradation on the platform over the weekend.

## Merch werks

On a roll with the store, we figured out how to make the [merch](https://store.elfhosted.com/product-category/merch) work. I've ordered myself a pair of socks and some stickers to test, and it's all working (*they're in the mail*). We chose [Printify](https://printify.com/) as the print-on-demand provider - they have a reputation for quality and reliability, but their shipping rates can be a bit shocking - they seems to vary from product to product, and country to country.

!!! tip "Suggest some merch!"
    If you've got ideas for merch you'd like to see, drop into #elf-friends and let us know!

## ElfTerm has arrived

Tired of the weird FileBrowser "console"? Check out [ElfTerm][elfterm], which provides access to [ElfBot][elfbot], and to Kubernetes, in a beautiful and geeky CLI!

![](/images/blog/elfterm-kubectl-get-pods.png)

## plex-debrid is un-broked

Plex-debrid's Trakt integration has been broken for a while - it seems as if the original project's Trakt oauth credentials have expired, so we [updated our fork](https://github.com/elfhosted/plex_debrid/commit/c678fa1e5974a5c666b2fe70d65228c6fdfb4047) to allow passing of credentials to the process in environment variables.

The takeaway here, is [plex-debrid][plex-debrid] is working now! :partying_face:

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"
