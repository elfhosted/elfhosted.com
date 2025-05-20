---
title: Data Retention
description: Here's how we automatically delete unused / inactive user data
---

# Data Retention

This page describes how data is automatically deleted when you terminate your account, unsubscribe from an app, or abandon your account without active subscriptions.

## Definitions

* "Account data" means your account (*username, email, password, purchase history*) in the ElfHosted store, to which all of your subscriptions are tied.
* "Application data" refers to the config for a specific application, usually found in `/config/<app>` in [File Browser][filebrowser]. Examples would be your [Plex][plex] metadata, or your [Prowlarr][prowlarr] DB.

## When do we automatically purge data?

Action | Data affected | Retention
---------|----------|---------
 :no_entry_sign: Unsubscribe all subscriptions | :material-trash-can-outline: Application data<br/>:material-trash-can-outline: Account data<br/>:material-trash-can-outline: Offsite backups | 7 days<br/>1 month<br/>1 month
 :material-nuke: Delete your account | :material-trash-can-outline: Account data<br/>:material-trash-can-outline: Application data<br/>:material-trash-can-outline: Offsite backups | Immediately<br/>Immediately<br/>Immediately

## Examples

If you...

* ... decide to switch from [Plex][plex] to [Jellyfin][jellyfin], nothing changes. Your Plex data persists at `/config/plex/`, consuming space, until you manually remove it.
* ... cancel / lapse all your subscriptions, after ==7 days==, ^^all^^ your application data will be ^^deleted^^. (*if you create a new subscription ==within 1 month==, your data will be automatically restored from backup*), and after ==1 month== your account itself, and ^^all^^ your offsite backups will be ^^deleted^^ (*you'll get a fresh 100GB if you start a new subscription*)
* ... [delete your account from the store](https://store.elfhosted.com/delete-my-account/), ^^all^^ your data (*including your store account, app data, and offsite backups*) will be ==^^immediately deleted^^==.

## Questions

!!! question "Can you recover deleted data?"
    No :cry:

!!! question "Do you backup my data?"
    Yes, we take daily backups of your `/config`, your `/storage/symlinks`, and your `/backups` volumes, and we store these offsite for a month. These backups are intended for datacenter migrations and disaster recovery, and can't be **selectively** restored. In other words, you can request us to restore the **entire** `/config` folder, but not just the `/config/plex` folder.

!!! question "How can I backup my data?"
    Use [ElfBot][elfbot] to perform backups of your app data to `/backups`, and then copy the data offsite using filebrowser.

!!! question "I'm no longer subscribed to my app, how can I get my app data?"
    The data will persist in `/config/<app>` for as long as you have an active subscription.

!!! question "How can I immediately delete my account and data?"
    Go to the [Delete My Account](https://store.elfhosted.com/delete-my-account/) page on the store, enter your account password, and confirm deletion.

--8<-- "common-links.md"