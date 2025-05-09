---
date: 2024-07-10
categories:
  - infra
tags:
  - CHANGELOG
title: Upcoming pricing model changes
description: We've made some changes to pricing / plans, here's what you need to know
---

# Pricing model changes

!!! danger "Your subscription will sunset from 1 Aug. Take action as described below"

    Sorry for the big red message, but this is the TL;DR - unless you take action described below, your ElfHosted subscriptions **will** stop working some time after 1 Aug 2024. 
    
    We have a new pricing model / bundle structure which requires resubscriptions (*the store can't migrate daily to monthly subscriptions for us*)

    Details follow...

When ElfHosted was "born", the idea was to provide "pay-as-you-go" type hosting using a microservices model on "cheap" hardware, leveraging Kubernetes to make the platform resilient. We used ElfBuckz and daily subscriptions to "shoehorn" this model onto the store, and while it worked, it was confusing and hard to manage.

One year later, we're geared heavily towards debrid-focused media apps (*we only added real-debrid support in Feb 2024!*), and a "core feature" is our friendly Discord community, and our bundles which "just work".

$10 free ElfBuckz, daily subscriptions, and pricing based purely on measured / forecast resource usage no longer "fits", and so the following changes are rolling out..

<!-- more -->

## No more $10 free ElfBuckz

The intention of the free ElfBuckz on signup was to provide users with an opportunity to "kick the tyres" before committing. We now have trial periods on all apps/bundles, which serve the same purpose in a much more integrated fashion. 

ElfBuckz will remain in the store as a payment gateway (*you can still spend your remaining balance*) to facilitate refunds, but we're no longer giving away $10 credit to every new account.

## Monthly billing

All new subscriptions are billed monthly, with increasing pre-payed discounts available for 3/6/12 months periods. Daily renewals were buggy and noisy.

Switching to monthly "subscriptions" in Woocommerce affords us the following benefits:

* [x] Users can migrate between apps / bundles within a subscription, and the store will pro-rate any differences. So it's super-easy to switch from Aars to Riven and back again, for example.
* [x] We can alter bundles during a subscription - i.e., add an extra app to Hobbit/Ranger bundles, without having to delete and recreate the subscription (*the older bundle plugin didn't support this*)
* [x] We can offer trial periods on bundles

## Pricing tiers

There are only 5 price tiers. Every app fits into one of these tiers:

1. **$9/month**: Standard apps
2. **$19/month**: Complex apps (*apps with unusually high resource / support requirements*)
3. **$29/month**: [Starter kits](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/infinite-streaming-starter-kits)   (*a bundle with the minimal components for an Infinite Streaming setup*)
4. **$39/month**: [Hobbit bundles](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/hobbit) (*a complete Infinite Streaming setup, with hardware transcoding support and 1/8 resources of a node*)
5. **$59/month**: [Ranger bundles](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/infinite-streaming-plus) (*a complete Infinite Streaming setup, with hardware transcoding support with 1/4 resources of a node*)

These changes are already in place, and affect new subscriptions only.

## No more grandfathered pricing

On 1 Aug 2024, existing subscriptions will cancel and age out over the remaining subscription period.

This means, if you had a monthly bundle (*really 30 daily orders*) which renewed on the 27th July, it'll last until 27th Aug, but thereafter it won't renew again.

However, if you had a daily, ElfBuckz-based subscription, it'd stop after 1 final day.

## How to prepare

!!! tip "How to migrate"

    To avoid an unhappy surprise come 1 Aug, cancel your existing bundles subscriptions, let them age out, and switch to one of the new monthly ones. If possible, take advantage of the [Starter](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/infinite-streaming-starter-kits), [Hobbit](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/hobbit) or [Ranger](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/infinite-streaming-plus) bundles, since they're by far the best value for money at scale, considering all the apps which are bundled in.

    To assist with migration, if you create an [#elf-support][elf-support] ticket, an ElfVenger can "wash up" your remaining subscription into ElfBuckz, which can then be offset against the new subscription.

## Questions / issues

Got questions? We've setup a [dedicated thread](https://discord.com/channels/396055506072109067/1260399511491051541) in Discord to capture all questions / ideas / issues. Drop in, and let's talk!. This post will be updated to based on conversations in the thread.

Here are a few to get us started:

### Will my subscription transition automatically?

No, either you need to cancel it, or we do. If you don't care about the balance of the subscription (*i.e., it's a daily subscription*), then just cancel and resubscribe. If you'd like the balance washed up into ElfBuckz, create a [#elf-support][elf-support] ticket.

### What about Stremio addons?

Stremio addons are generally "Standard apps". [Comet][comet] (*and possibly [MediaFusion][mediafusion], in future*) is an exception, since it uses significant network bandwidth for "Proxy Stream" mode.

### What about revenue sharing for OSS devs?

As [previously announced](/blog/2024/06/12/riven-is-ready-for-testing/), we share 30% of app subscription revenue with "Elf-iliated" devs. This includes [Riven][riven] and [Comet][comet], and the change to monthly subscriptions will make accounting for this simpler.

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"

[^1]: Delta is meaningless in this case because the previous count included pods left running in error by the provisioning script