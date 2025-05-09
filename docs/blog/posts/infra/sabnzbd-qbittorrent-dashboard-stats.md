---
date: 2023-08-18
categories:
  - CHANGELOG
tags:
  - new-apps
title: SABnzbd / qBitorrent dashboard stats, Calibre upgrade, bugfixes
description: We've now got SABnzbd and qBitorrent stats on your dashboard, Calibre has a fresh coat of paint, and bugz are squashzed
---

# Downloader Dashboard stats

If you're an [SABnzbd][sabnzbd] user, you may have noticed a little error icon over your SABnzbd link on your dashboard. This is where your download stats are supposed to be displayed, but due to the trickery that our SSO plays with CORS, this wasn't happening.

The trickery is now fixed, so enjoy your beautiful dashboard!

Oh, and [qBittorrent][qbittorrent] users, there's a little surprise in there for you too: 
![qBitorrent stats in Homer](/images/blog/qbitorrent-homer-stats.png)

(*sorry [ruTorrent][rutorrent] users, no love for you yet, although the Homer dashboard does [support ruTorrent](https://github.com/bastienwirtz/homer/blob/main/docs/customservices.md#rtorrent), it doesn't send your credentials via cookies, so doesn't work with our SSO*)

<!-- more -->

### Calibre powered up!

[Calibre][calibre]'s got a face-lift - we're now[^1] using the [LinuxServer.io image](https://docs.linuxserver.io/images/docker-calibre), which includes the shiny "KasmVNC" UI. (*Yes, it's still a VNC session in a browser, the only way to effectively run the full Calibre*).

Now that we have full UI access to Calibre, you'll be able to point it's auto-add feature to your [openBooks][openbooks] download folder, and have downloaded books auto-appear in Calibre, as well as [Calibre-Web][calibre-web]! [Readarr][readarr] integration still works too.

### WebDAV export

Question: 

> What if you want to transfer your data to / from [ElfStorage][elfstorage]? You can't SFTP/FTP it, since our (*super-resilient and HA*) design only works with incoming HTTPS.

Answer:

> You expose your storage via a password-protected [WebDAV export](https://store.elfhosted.com/product/rclonewebdav/)! Behind the scenes, this is an `rclone serve` command, which is ideal for rcloning data in/out of ElfStorage.

!!! tip "Transferring data to/from storageboxes"
    You don't need any fancy WebDAV export to move data to/from your [storageboxes][storagebox], since they natively support SSH/SFTP, WebDAV, and SMB. Also, storagebox transfers go direct via Hetzner's infrastructure, bypassing an constraints / congestion on ElfHosted's infrastructure.

### jDownloader

We have rudimentary [jDownloader support](https://store.elfhosted.com/product/jdownloader/)! You'll need to enter your [myjdownloader](https://my.jdownloader.org) credentials on purchase, and then the app will "connect" your jDownloader to your account.

The config still needs some testing / tuning, so if you're a power-user who would actually **use** jDownloader, hit me up with your ideas / suggestions!

### Bugz squished

* :bug: If you've recently mounted some storage with rate-limits, like gDrive, and noticed that your storage stats on your dashboard disappeared, it may be because the script which generates the stats is taking too long to complete (due to rate-limits). The script will now time-out after 5 minute,s so troublesome storage targets won't appear in stats, but the rest of your storage targets will :thumbsup:
* :bug: Cancelled services actually cancel now!

### Summary

As always, thanks for building with us - feel free to share suggestions, ideas, and whatever you ate for breakfast today! :cooking:

[^1]: Normally I avoid images which run as root for security reasons, but an s6-based image like LSIO's one is the only way to run Calibre's UI, and I've recently added [kata-containers](https://github.com/geek-cookbook/elf-infra/blob/main/roles/kata-containers/tasks/main.yml) to our platform for better isolation of potentially-overprivileged pods.


--8<-- "common-links.md"