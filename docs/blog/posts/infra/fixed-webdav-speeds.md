---
date: 2023-12-29
categories:
  - CHANGELOG
tags:
  - infra
title: LowEndSpirit user influx surfaces fresh bugs
description: Thanks to a post on LowEndSprit, we saw a 40% jump in subscribers (10-20% fraudulent though), which helped to identify a few new bugs 
---
# Moar users = Moar bugz

I made a [post on LowEndSpirit](https://lowendspirit.com/discussion/7090/50-off-storage-3-tb-at-elfhosted-until-2024#latest) yesterday, mentioning the 50% off on storage. This got some attention, resulting in an influx of new users, bumping us from 90 to 128 subscribers overnight!

The extra user load brought some issues to light, which I've spent today chasing down..

<!-- more -->

## Referral fraud refactors referrals

As exciting as the user influx was, at least 10 of these were fake accounts, created by a handful of users who figured out how to "game" our referrals system for extra ElfBuckz. It turns out that I **thought** that the referral plugin would only credit the referrer 10% of their referree's ElfBuckz topups, but what it **actually** did was credit them 10% of **all** their referee's purchases, to be **spent** on their own ElfBuckz topups.

So one particularly smart / sneaky user managed to refer himself a handful of accounts, burn through each account's $10 ElfBuckz with 100TB of ElfStorage for a day, and credit himself $1 extra ElfBuckz as a result!

I've personally thanked these users for highlighting the bug, let them hang onto their ill-gotten ElfBuckz gainz, and readjusted the referrals system as follows:

1. When you send a referral link to a friend, and they **register** their account, you get a coupon for $1 ElfBuckz :moneybag:
2. When that friend completes their first order (*using their ElfBuckz*), they get a coupon for $5 off their next ElfBuckz topup :moneybag: :moneybag: :moneybag: :moneybag: :moneybag:
3. If further fraud is detected, the defrauder will forfeit all their ElfBuckz :scream_cat:

You can find your [personal referral link on your account page](https://store.elfhosted.com/my-account/myreferrals/).

## WebDAV speeds fixed

It turns out I'd accidentally restricted our WebDAV endpoints to 1.25MB/s, instead of 10MB/s as intended. This is now fixed, so if you're using [WebDAV][webdav] to access your storage externally, you'll now be able to transfer at up to 80Mbps, or 8% of a single node's 1Gbps link[^2].

### Summary

As always, thanks for building with us!

[^1]: Includes users testing the platform with $10 free ElfBuckz
[^2]: Subject to contention on the node as physically enforced by the 1Gbps NIC

--8<-- "common-links.md"