---
date: 2023-07-31
categories:
  - build-in-public
tags:
  - infra
title: SSH rclone mounts, ElfBuckz balances, and bugfixes
description: Keep an eye on your ElfBuckz balance, we can now offer SSH-based rclone mounts, and user dashboards should be easier to find!
---

# Beware exhausted ElfBuckz

Some users noticed today that their ElfBuckz balaces were exhausted, or near-to-exhausted. Currently, the system won't tell you if your ElfBuckz are running close to empty, it'll just tell you that your renewals failed, and leave you to figure out why!

I have a plan to send out notification emails re low balances, but for now, [check in on your ElfBuckz balance](https://store.elfhosted.com/my-account/account-funds/) occasionally to make sure you've got enough! You can also [subscribe to a monthly ElfBuckz topup](https://store.elfhosted.com/product/elfbuckz-topup/) once you've got a handle on your expected usage requirements.

## Added SSH Rclone mounts

We had our first request from a user wanting to mount data from a seedbox provider, in order to run an app not supported by that provider ([Pyload][pyload]). Consequently, we now have an [SSH rclone mount product group](https://store.elfhosted.com/product/rclone-ssh-mount/) for such a configuration. One interesting discovery was that the password submitted when you place the order needs to be an `rclone obscured` password (*which is not really secure, since rclone can decode it again, but it prevents casual "shouldersurfing"*).

<!-- more -->

## Apps dashboard link

A longstanding issue has been that users haven't been immediately aware of **where** to find their newly subscribed apps (*the `https://<username>.elfhosted.com` links*). I've learned a little bit of Wordpress-fu today, and managed to create an "Apps" link on the store dashboard, which should direct you to your personal apps collection!

## Welcome emails dashboard link

Similarly, I found that the workflow which sends the "welcome to ElfHosted" email (*including a dashboard link*) wasn't triggering because of an incompatiblity with DigitalOcean's managed MySQL product (*which requires primary keys on all tables, even temporary ones!*). I've applied potential workaround, and updated [MailPoet](https://wordpress.org/plugins/mailpoet/) (*the plugin author*) about the issue. Hopefully we'll see a fix soon, they seem to have a rapid dev pace.

## Today's scoreboard

:material-target: Metric | Numberz
---------|----------
:fontawesome-regular-circle-user: Total users | 47
:material-bug: Bugz squished | 2
:fontawesome-solid-gamepad: New toyz | 3

### Bugz squished

* :bug: You [no longer](https://plugins.trac.wordpress.org/changeset?sfp_email=&sfph_mail=&reponame=&new=2945391%40ownid-passwordless-login%2Ftrunk&old=2922905%40ownid-passwordless-login%2Ftrunk&sfp_email=&sfph_mail=) get redirected to an unparsable URL when you first login
* :bug: Filebrowser issued a new version 2 days ago, which [broke our](https://github.com/filebrowser/filebrowser/issues/2576) implementation (*invisible to users thanks to Kubernetes rollingUpdate rollout strategy*). I've rolled us back to the previous, working version.

### Upcoming

* [ ] July 2023 "Elf-Disclosure" report, and official "production" status!
* [ ] Revisit the "refer-a-friend" workflow

Thanks for building with us - stay tuned!

--8<-- "common-links.md"