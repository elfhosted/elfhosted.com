---
title: Data Retention
description: Here's how we automatically delete unused / inactive user data
---

# Data Retention

This page describes how data is automatically deleted when you terminate your account, unsubscribe from an app, or abandon your account without active subscriptions.

## Definitions

* "Account data" means your account (*username, email, password, purchase history*) in the ElfHosted store, to which all of your subscriptions are tied.
* "Application data" refers to the config for a specific application, usually found in `/config/<app>` in [File Browser][filebrowser]. Examples would be your [Plex][plex] metadata, or your [Prowlarr][prowlarr] DB.
* "[ElfStorage][elfstorage] data" refers to your data stored in `/storage/elfstorage`. This **includes** the free 100Gb data assigned with your account, and any further ElfStorage data purchased from the store.

## When do we automatically purge data?

Action | Data affected | Retention
---------|----------|---------
 :no_entry_sign: Unsubscribe an app | :material-trash-can-outline: Application data | 7 days
 :sleeping: Have no active subscriptions | :material-trash-can-outline: ElfStorage data | 31 days
 :material-nuke: Delete your account | :material-trash-can-outline: Account data<br/>:material-trash-can-outline: Application data<br/>:material-trash-can-outline: ElfStorage data | Immediately

## Examples

If you...

* ... decide to switch from [Plex][plex] to [Jellyfin][jellyfin], after ==7 days== your previous Plex data will be ^^deleted^^.
* ... run out of [ElfBuckz][elfbuckz] and all your subscriptions stop, after ==7 days==, ^^all^^ your application data will be ^^deleted^^, and after ==31 days== ^^all^^ your ElfStorage data will be ^^deleted^^ (*you'll get a fresh 100GB if you start a new subscription*)
* ... delete your account from the store, all your data (*including your store account, ElfStorage, app data*) will be ==^^immediately deleted^^==.

## Questions

!!! question "Can you recover deleted data?"
    No :cry:

!!! question "Do you backup my data?"
    We use ceph snaphots to make daily snapshots of user data to give us **some** protection in the event of an internal failure. However, once we delete the volume, the related snapshots are also deleted, so you should treat the data as if we don't back it up.

!!! question "How can I backup my data?"
    Use [ElfBot][elfbot] to perform backups of your app data to ElfStorage, and then copy the data from ElfStorage offsite.

!!! question "I'm no longer subscribed to my app, how can I get my app data?"
    Re-subscribe to the app, backup the data using [ElfBot][elfbot], then copy your backup using [FileBrowser][filebrowser], and then unsubscribe again.

--8<-- "common-links.md"