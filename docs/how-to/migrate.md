---
title: Migrating data/config in
description: Need to migrate your data or config into ElfHosted? Here's a detailed guide
---

# Migrating into ElfHosted

If you have data and config you'd like to migrate ElfHosted, this guide is for you!

## Into a StorageBox

The ideal migration strategy is to transfer files directly into your Storagebox, independently of ElfHosted infrastructure. This bypasses our 1Gbps node limits, and any rate-limits we apply on our migration tools to avoid customer impact. I.e., from a remote location, you can SFTP/SMB/WebDAV your data into your storagebox, before you're even an ElfHosted user!

### Drag & Drop (local machine)

The simplest way to transfer into a Storagebox is simply to mount it as a drive on your local computer via SMB, and drag/drop your content across.

You'll want to tell your file client (*i.e. Windows Explorer or MacOS Finder*) to open `\\u*****.your-storagebox.de\backup` (*customized for your own username*), and enter your credentials when prompted.

!!! note
    When using a Storagebox via SMB with a subaccount, the share name you're connecting to **must** be the same as the username of the subaccount

### Rclone (from another location)

If you'd prefer something automated for a more complex / unattended migration, here are some sample rclone configs you can use to transfer data in. In testing, we found best performance with Samba, followed by WebDAV, and finally SFTP:

=== "Samba (main account)"
    
    ```bash
    [hetzner]
    type = smb
    host = u*****.your-storagebox.de
    user = u*****
    pass = ************
    ```

=== "Samba (sub account)"
    
    ```bash
    [hetzner]
    type = smb
    host = u*****-sub**.your-storagebox.de
    user = sub**
    pass = ************
    ```

=== "WebDAV"

    ```bash
    [hetzner]
    type = webdav
    url = https://u*****.your-storagebox.de
    vendor = other
    user = u*****
    pass = ****************
    ```

=== "SFTP"
    
    ```bash
    [hetzner]
    type = sftp
    host = u****.your-storagebox.de
    user = u****
    pass = *************
    shell_type = unix
    ```

Here's a brief example re using rclone to transfer data from an existing seedbox into your Storagebox.

1. Configure rclone for your Storagebox settings, with `rclone config`. Create a new SMB remote named `storagebox`, and choose the defaults aside for hostname, username, and password.
2. Confirm your remote is correct, by running `rclone mkdir storagebox:backup/test`. Confirm that the test folder appears in your [elfhosted-mounted storagebox][store/storagebox]
3. Assuming your content is stored under `/home/harrypotter/secretfiles`, copy it to your storagebox by running `rclone copy -v /home/harrypotter/secretfiles storagebox:backup/` (*`backup` is the name of the default storagebox share*)

## Into ElfStorage

If you're using [ElfStorage][elfstorage], rather than a [Storagebox][storagebox], then you'll of necessity **have** to transfer via our migration tools.

!!! question "What's the difference?"
    The fundamental difference is that a storagebox belongs to you (*you pay Hetzner for it directly*), and if you stop using ElfHosted, you retain access to all of the content in the storagebox without having to do anything.

#### Pulling data into ElfStorage (preferred)

If your data is elsewhere, and you want to "pull" it into ElfStorage, use our [Rclone][rclone] UIs, configure the remote, and copy into `/storage/elfstorage`. Transfers are limited to 10Mbps.

!!! tip
    Using RCloneBrowser is preferable, since you can control the transfer parameters (*rate, etc, to avoid impacting other users*).

#### Pushing data into ElfStorage

Unlike Hetzner's Storageboxes, you can't transfer data into ElfStorage directly, so if you want to **push** data into ElfStorage, you'll need to add [WebDAV][webdav] to your apps, and then use rclone to transfer data **into** ElfStorage as a WebDAV remote. Transfers are limited to 10Mbps.

## Config

You may have app databases you'd like to migrated into ElfHosted. Usually, you'd stop an app, copy over its config, and then start it up. Because of our Kubernetes design, you can't actually **stop** your apps, but you can use ElfBot to trigger a restart-pause for an arbitrary period. 

Here's an example workflow re migrating an Ombi database..

1. Using [FileBrowser][filebrowser], navigate to `config/` and upload your new Ombi config to a folder named `ombi-new`
2. Now in the FileBrowser CLI, run `elfbot restart-pause ombi 10` to trigger a paused restart for 10 minutes
3. ElfBot will restart your Ombi pod, and wait for 10 minutes before continuing starting it up. Within 10 minutes, rename `/config/ombi` to `/config/ombi-old`, and rename `/config/ombi-new` to `/config/ombi`. 
4. After 10 minutes, Ombi will start normally, referencing your restored files!

--8<-- "common-links.md"