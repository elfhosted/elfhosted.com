---
date: 2024-09-18
categories:
  - infra
tags:
  - CHANGELOG
title: Bundle subscribers get tiered discounts
description: Tiered discounts on supplemental apps for bundle subscribers
---

# Tiered discounts on supplemental apps for bundle subscribers

## Get your discounted apps!

In Aug, we [standardized pricing](https://elfhosted.com/open/pricing/) across our non-bundled products at $9/month for simple apps, and $19/month for complex apps. This has enabled self-service "app-hopping" :rabbit:, since the store will allow the exchange of one app, for another equally priced app, without charge.

We've also [explained in the FAQ](/faq/#how-do-you-justify-the-cost) that even "low-touch" apps incur a support / development / time and attention cost, which is why they're priced the way they are.

Recent feedback touched on the increased cost of adding [supplemental apps](https://store.elfhosted.com/product-category/apps/), for "*nice-to-haves*" like [custom domains](https://store.elfhosted.com/product-category/custom-domains), [storage mounts](https://store.elfhosted.com/product-category/storage), etc, with some respondents avoiding experimenting with these as a result.

We've now added the functionality to the store to offer bundled subscribers discounted pricing on additional apps, as detailed below..

<!-- more -->

Bundle | Discount | Simple App | Complex App
---------|----------|---------|---------
 - | - | $9/month | $18/month [^1]
 [Hobbit](https://store.elfhosted.com/product-category/streaming-bundles/hobbit) [1/8 dedicated] | 22% | $7/month | $14/month
 [Ranger](https://store.elfhosted.com/product-category/streaming-bundles/ranger) [1/4 dedicated] | 44% | $5/month | $10/month
 [Halfling](https://store.elfhosted.com/product-category/streaming-bundles/halfling) [1/2 dedicated] | 66% | $3/month | $6/month
 [Nazgul](https://store.elfhosted.com/product-category/streaming-bundles/nazgul) [all yours!] | 88% | $1/month | $2/month

If you've already added non-bundled apps (*custom domains, storage mounts, etc*) to your bundle, you'll need to cancel / re-subscribe these to to take advantage of the discounted pricing. Create an [#elf-help][elf-help] ticket if you need a hand with this!

!!! question "What are Halfling / Nazuguls?"
    They're upcoming bundles which would give you 1/2 or fully dedicated nodes to yourself. They're on backorder for final testing, reach out if you're interested!

## Petio

Speaking of discount-worthy supplemental apps, we've just finished adding [Petio][petio]! Petio is an alternative to Overseerr. Its future is questionable (*[development](https://github.com/petio-team/petio) doesn't seem very active*), but it's pretty, and quite workable as-is, and it features in [Puks-The-Pirates' famous guide](https://savvyguides.wiki/sailarrsguide/).

![](/images/screenshots/petio.png)

## Blackhole

Unlike Petio, [Blackhole][blackhole] **is** a bundled app, so it won't cost you anything to play with (*on Hobbits+*). The idea of Blackhole is that it's a far simpler solution to RDTClient's "find stuff on RD and symlink it" function. 

That's it. 

That's all it does. 

It doesn't even have a UI, but you basically plug in your RD key using [ElfBot][elfbot], add a blackhole downloader to your Aars, and watch it run!

The rationale behind the inclusion of Blackhole is (1) it's popular among the self-hosting debrid community, (2) it provides an alternative to the not-always-well-behaved RDTClient, and (3) it supports Torbox (*as a backup to RealDebrid*).

For details on setting up Blackhole, see [here][blackhole].

## US DC to expand 200%, add HA

Some brave living-on-the-edge power-users / beta testers [migrated their stacks](/how-to/migrate-datacenters/) to our US datacenter within the past week or so, unearthed a few bugs, and are enjoying 200% bandwith as they stream to locations closer to the US.

Since the solution seems to have legs, and there's still considerable demand / opportunity, I pulled the trigger on another 2 controlplane nodes (*for a HA controlplane*), and another 3 worker "yankee" nodes for the US cluster.

Provisioning is not "*within the hour*" like it is with Hetzner, but we should have more capacity in the US DC in a week or two.

Enough time to squash those remaining bugs! :bug:

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 246 | -8
🐬 Tenant pods | 3186 | -56
🐛 Bugz squished | 1 | -
🕹️ New toyz | 3 | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"

[^1]: Down from $19/month to make percentages neater!
