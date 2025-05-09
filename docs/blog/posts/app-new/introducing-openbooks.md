---
date: 2023-08-07
categories:
  - new-app
tags:
  - openbooks
title: Introducing OpenBooks, Bitcoin payments, PayPal issues
description: Today we added Openbooks, a beautifully simple tool which allows you to download ebooks from irc.irchighway.net quickly and easily
---
# Introducing Openbooks

Today we added [Openbooks][openbooks], a tool which allows you to download ebooks from irc.irchighway.net quickly and easily.

![Screenshot of Openbooks](/images/screenshots/openbooks.png)

Currently, Openbooks is hard-coded to save downloaded content to `/storage/elfstorage/downloads/completed/books`, and changing this is non-trivial, since it's a commandline argument fed to the application binary, rather than a user-configurable UI setting. If changing the download location is important to you, we may be able to effect this in future using [ElfBot][elfbot].

While [Readarr][readarr] -> [Openbooks][openbooks] -> [Calibre][calibre] -> [Calibre-Web][calibre-web] would be the "holy grail", it doesn't look like we'll see Readarr integration. However, I have noticed some issues on the [Openbooks GitHub repo](https://github.com/evan-buss/openbooks) which explain how to setup a [Calibre][calibre] "auto-add" directory, which would create the "slightly-less-holy grail" of [Openbooks][openbooks] -> [Calibre][calibre] -> [Calibre-Web][calibre-web]. For this to work, we need to switch to the VNC-in-browser version of Calibre, which I'll try to do over the next few days.

See more on the [app][openbooks] page, or perform a 24h trial / subscription at the [store](https://store.elfhosted.com/product/openbooks/)!

More news...

<!-- more -->

## :simple-unraid: unRAID guide for "outsourced" media aquisition

After helpful input from an elf-a-tester, I created a guide describing how to leverage ElfHosted to augment a local unRAID system, and [posted it in r/unRAID](https://www.reddit.com/r/unRAID/comments/15kfyd0/run_torrent_clientsarrs_remotely_save_to_hetzner/). The takeaway is that ElfHosted would eliminate some of the hassle re running Arrs / torrent apps for an unRAID user, but they could still consume the content locally by mounting a storagebox into unRAID.

## :simple-paypal: Paypal subscriptions coming soon

Some users have reported issues topping up their ElfBuckz balances with PayPal. I've raised an issue with PayPal, but it'll take a few days to resolve, I expect, since I now have to do additional KYC to enable the "advanced features" necessary to sell subscriptions (*to [ElfBuckz topups](https://store.elfhosted.com/product/elfbuckz-topup/)*) via PayPal.

!!! tip "Wait, you can **subscribe** to ElfBuckz topups?"
    Yessir! Once you have a rough feeling for how much ElfBuckz you'll need every month, you can [subscribe to a monthly ElfBuckz topup](https://store.elfhosted.com/product/elfbuckz-topup/), to avoid all those pesky manual topups!

## :simple-bitcoin: Bitcoin payments now accepted

While monkeying with PayPal, I also added a Bitcoin payment processor, so that you can now top up your ElfBuckz with Bitcoin, if that's your thing! (*cue laser-eyes*)

--8<-- "common-links.md"

