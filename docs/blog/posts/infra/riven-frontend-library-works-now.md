---
date: 2024-08-03
categories:
  - infra
tags:
  - CHANGELOG
title: Riven Frontend's library works now
description: With a few config fixes, Riven's beautiful frontend is now more beautiful, and we may have a fix for broken symlinks
---

# Riven's Frontend Fixed (Library view)

## Fantastic Frontend

We've been using Riven since before the frontend was working nicely, so we've all assumed that the 500 errors on the "Library" view of the frontend was normal, indicating a work in progress.

It turns out, this has been fixed for a while, but we were presenting the database parameters to the frontend in the wrong syntax - now that the syntax is fixed, your Riven frontend's library tab should look more like this:

![](/images/blog/riven-frontend-library-fixed.png)

Thanks to \@zombie :zombie: in Discord, we've unearthed another possible bug...

<!-- more -->

Our Zurg config has always had these options set:

```
retain_folder_name_extension: false
retain_rd_torrent_name: true 
```

... which can cause a "race condition", such that **sometimes** the folders created by Zurg are detected by Riven using their original name, but then subsequently renamed by Zurg after it identifies that they contain movies/shows.

I quote:

```
it's only a problem if riven detects the file between
a) zurg seeing the torrent
b) zurg displaying the torrent in webdav
c) rclone showing the file
d) zurg realising it's a movie with .mkv or mp4 extension and renaming the dir

if riven sees the file between c) and d) you get a broken symlink
```

So... this **may** have something to do with the odd broken symlinks our Riven users see. I've updated our defaults (*on a fresh Zurg install*) to:

```
retain_folder_name_extension: true
retain_rd_torrent_name: true 
```

.. and curious / brave users may want to adjust these settings themselves, and restart zurg to test :fingers_crossed:

## US DC testing

Speaking of testing, the elfhosted.us cluster is nearly ready for beta testing, so if you're a US user who sees a significant difference between https://speed.elfhosted.com (*Falkenstein, Germany*) and https://speed.elfhosted.us (*Washington State*), read on..

If you'd like to help test, with either your main account, or a temporary test account, please drop into [this thread](https://discord.com/channels/396055506072109067/1269247618983268382) and add your details.

## WebDAV bundled with Hobbits / Rangers

[WebDav Access][webdav] is now included in the Hobbits and Ranger packages, but because you're not prompted to set a password on purchase, you'll need to set your own WebDAV password using [ElfBot][elfbot], by running `elfbot env webdav WEBDAV_PASSWORD=yoursekritpassword`.

## Calibre / Calibre-Web fixes

Although not a hugely popular combination, [Calibre][calibre] / [Calibre-Web][calibre-web] is an excellent solution for managing your eBook collection. I've fixed some hardcoded paths pointing to ElfStorage (*which no longer exists*), and updated the [documentation][calibre-web] to indicate how to maintain the Calibre **Library** in `/config`, but to store actual **content** in a storage mount.

## Openbooks also fixed

Similar to Calibre above, [OpenBooks][openbooks] (*a tool for sourcing ebooks / audiobooks from IRC*) will now save downloads to an ephemeral `/tmp` folder by default (*you can then download them from the browser UI*), but this can be adjusted with use of an environment variable to save downloaded content to a storage mount.

## Elf-Disclosure for Jul 2024 released

Our [Elf-Disclosure report for Jul 2024](https://elfhosted.com/open/jul-2024/) was published, full of juicy stats, retrospectives, and ideas about upcoming plans.

## Reddit Rampages

I posted our Elf-Disclosure report to r/StremioAddons, as well as a 10% birthday coupon for our hosted Stremio addons. This caused a bit of a flurry of topics / posts, which the ElfVengers and I have tried to respond to as quickly and clearly as possible.

I include these below for context, and in case you're an active Reddit and you want to have your say :)

* [Plex Hosting Options // ElfHosted & Other Services ](https://www.reddit.com/r/RealDebrid/comments/1eirutv/plex_hosting_options_elfhosted_other_services/)
* [What's all the hype around elfhosted? ](https://www.reddit.com/r/StremioAddons/comments/1ei7dgq/whats_all_the_hype_around_elfhosted/)
* [The Jul 2024 Elf-Disclosure report](https://www.reddit.com/r/StremioAddons/comments/1ei1jg3/elfhosteds_elfdisclosure_report_for_july_2024_we/)
* [The 10% off offer on private hosted Stremio addons](https://www.reddit.com/r/StremioAddons/comments/1ei1ubz/get_10_off_all_elfhosted_private_stremio_addons/)

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 180 | -[^1]
👾 Zurg mounts: | 147 | +1
⛰ Riven pods: | 54 | +4
🐬 Tenant pods | 2365 | -313
🧑🏻‍🌾 [Hobbits](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/hobbit) | 49 | +16
🤠 [Rangers](https://store.elfhosted.com/product-category/consume-media/infinite-streaming/infinite-streaming-plus) | 19 | -
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 8 | -
🐛 Bugz squished | 2 | -
🕹️ New toyz | - | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"

[^1]: We lost about 50% of historical / legacy subscriptions during the transition to monthly subscriptions on the Aug 2024 pricing model.
