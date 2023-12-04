---
date: 2023-12-04
categories:
  - new-app
tags:
  - homepage
title: Introducing Homepage, a beautiful, integrated, alternate dashboard
description: Presenting Homepage, a deliciously beautiful alternate dashboard for your ElfHosted services, with deep integrations into applications
---
# Introducing Homepage

## Hello, Homepage :art:

Today's new app is an alternative dashboard, [Homepage][homepage]...

![Screenshot of Joplin](/images/screenshots/homepage.png)

Why do you need **another** dashboard, what's wrong with your default ElfHosted dashboard?

Probably nothing, but it's soooo pretty! Also, some of the app integrations are pretty sick! Unlike Homer, which hits the various APIs using your browser, Homepage runs a backend proxy, so it's much easier to configure it to talk to your other ElfHosted services, and much richer data can be retrieved.

For example, the Jellyfin integration will show you exactly what media is currently streaming, along with the expected summary of your library stats.

You can customize homepage by adding your own services (*like the weather in your location, or the price of your favorite crypto*), your own custom background, etc, and changes are effected instantly.

If there's popular demand, I'll add an option for Homepage to replace your default dashboard :thumbsup:

<!-- more -->

## What's new? ##

### New Toyz

#### Encrypted rclone mounts

Until today, if you wanted an encrypted rclone mount, you'd need to buy the "custom mount" product, and then create a support ticket for it to be provisioned, since the rclone encryption config is more complex than a simple remote - you effectively need one remote to reference the un-encrypted data, and another to represent the encrypted data on top of the first remote.

Further confounding the issue, rclone obfuscates credentials in its config file, which can make troubleshooting very difficult.

I've refactored how the various products are deployed via the store, and discovered the `rclone obscure` command, which means we can now allow users to input their **actual** credentials in the store (*which users were doing anyway, creating support issues*), and obfuscate them during provisioning, so that rclone will correctly mount their remotes.

As a result, we can now automatically provision encrypted BYO storage!

Currently in the store we have:

* Encrypted [storagebox mount](https://store.elfhosted.com/product/hetzner-storagebox-mount/)s (*don't want Hetzner to be able to read your data? Buy this!*)
* Encrypted [GDrive mounts](https://store.elfhosted.com/product/rclone-google-drive-mount/)

### Bugz squished

#### Races on new volumes being provisioned

Over the past few weeks, there have been a few occasions where a new user account would be created, but none of the volumes would be created - the CSI provisioner would error with messages about the volume operation already being in progress.

What I **think** was happening is this.. a new user gets 10+ volumes provisioned on startup (*more so, because we're still finishing off the HDD-SSD migrations*), and these pods get all RWX-attached to multiple pods, running on multiple nodes. A busy job for a provisioner, but I'd configured 2 replicas of the ceph CSI provisioners (*for redundancy's sake*), and I think, given the multiple-volume-multiple-pod attach requests, both provisioner pods were responding at the same time, creating a race / deadlock to provision the volumes.

I've reduced us to a single replica for the CSI provisioners, and **thus far**, there have been no more pending attachements (*but we'll only know after a few days of new user signups*).

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total subscribers | 87
:fontawesome-solid-hard-drive: Storageboxes mounted | 23
:material-sync: Rclone mounts | 10
:material-dolphin: Tenant pods | 819
:material-bug: Bugz squished | 1
:fontawesome-solid-gamepad: New toyz | 1

### Summary

As always, thanks for building with us - feel free to share suggestions, and your own ideas for new apps to add!

--8<-- "common-links.md"