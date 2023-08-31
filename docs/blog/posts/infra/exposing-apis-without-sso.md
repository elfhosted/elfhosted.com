---
date: 2023-08-31
categories:
  - CHANGELOG
tags:
  - radarr
  - sonarr
  - lidarr
  - readarr
  - nzbget
  - sabnzbd
  - qbittorrent
title: Safely exposing app APIs without SSO
description: If you're an NZB360 / LunaSea users, huzzah, we can now expose app APIs without SSO!
---

# Exposing Arr/Downloader apps without SSO

Until now, when a user has asked 

> "how can I access my media apps with [NZB360](https://www.nzb360.com/) or [Lunasea](https://www.lunasea.app/)?"

The answer has been:

> "sorry, the SSO which protects the apps relies on a browser cookie, which won't work in a separate app".

From today though, the answer is:

> Change your API key / password, subscribe to an "[Exposed](https://store.elfhosted.com/product-category/advanced/)!" service, and enjoy your exposed access!

Read further for details about how it works, and why..

<!-- more -->

It's possible to selectively avoid SSO, so we could have simply exposed `/api` on the apps, but given that we default users to a common API key (*for a better out-of-box experience, with integration and dashboard support*), this would result in an easy avenue for abuse.

Thanks to a particularly helpful elf (*who was in trouble with his wife since his migration to ElfHosted broke NZB360!*), we now have an elegant solution to allow users to selectively "opt in" to exposing their APIs / apps with minimal risk. Here's how it works..

Say you're a [Radarr][radarr] user, and you want to access Radarr's API without SSO. You'd change your Radarr API key (*breaking your dashboard integration*), then you'd subscribe (*in addition to Radarr*), to [Radarr Exposed!](https://store.elfhosted.com/product/radarr-exposed/), which will require your new API key. This additional product will then update the dashboard for your new API key (*fixing your integration*), and expose the minimum necessary paths without SSO (*normally `/api/`*).

We currently have [exposed services](https://store.elfhosted.com/product-category/advanced/) for the Arr apps, and for the downloaders which support their own auth (*[ruTorrent][rutorrent] does not, AFAIK*). Radarr and Sonarr are known to work with NZB360, the others may require testing. If you're interested in bypassing normal SSO for other apps, let's discuss in [#elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303)!

## Custom DNS / SSL support coming soon

I've recently migrated some of my other public projects into the ElfHosted cluster, the better to control my (*slightly-out-of-control*) cloud resource spending.. the following public services are now ElfHosted:

* [Mastodon](https://so.fnky.nz) - my teeny-weeny geek-friendly instance, more geeks welcome
* [Invidious](https://in.fnky.nz) - alternate YouTube frontend to browse trending / Taylor Swift videos without feeding Google's profile on you
* [Searxng](https://searxng.fnky.nz) - Privacy-respecting meta search engine, whose killer feature (*for me*) is "subscribing" to search results via RSS (*like your own Google alerts*)

Cool apps aside, the takeaway here is that none of these app URLs end in `elfhosted.com` (*because they pre-dated it*)...

Using CNAMEs and LetsEncrypt HTTP01 validation, we can request certificates for any authorized domain name, which means.. we'll be able to offer custom domain names for your apps!

This may be unnecessary for secure, isolated little apps like the Arrs, but I can imagine a user who'd want to subscribe to a NextCloud stack might prefer to use their own domain, like `https://mycloud.batman.pizza`, rather than `https://nextcloud-harold123.elfhosted.com`!

There are no apps supporting custom domains yet, but if you've got a use case, hit me up and we can work out if/how it can work!

## OneDrive support

We now have the option to [rclone-mount your Microsoft OneDrive](https://store.elfhosted.com/product/rclone-onedrive-mount-a/) into your apps! It turns out if you have a Microsoft account, you get a small amount of OneDrive storage bundled in already. If you have weird requirements that don't work with the default product (*like Sharepoint integration*), then let me know and we can test!

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers[^1] | 36
:fontawesome-solid-hard-drive: Storageboxes mounted | 16
:material-sync: Rclone mounts | 12
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 3

### Bugz squished

#### Blog works again!

It's been quiet during the past week because the latest release of mkdocs-material was [broken on Python 3.8](https://github.com/squidfunk/mkdocs-material/issues/5916), which is what Netlify uses when it builds this site. Now that the fix is merged, I can publish blog updates again![^2] :partying_face: 

### Summary

As always, thanks for building with us - feel free to share suggestions, ideas, and whatever you ate for breakfast today! :cooking:

[^1]: I changed this metric to count subscribers as reported by Wordpress, rather than provisioned users (*72 currently*), because (a) I have some un-provisioning scripts to fix, and (b) I think subscribers is a more accurate measure of current growth.
[^2]: Just in time for the Aug 2023 elf-disclosure report this weekend!

--8<-- "common-links.md"