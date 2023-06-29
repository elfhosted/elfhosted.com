---
title: Migrating data/config in
description: Need to migrate your data or config into ElfHosted? Here's a detailed guide
---

# Migrating into ElfHosted

If you have data and config you'd like to migrate ElfHosted, this guide is for you!

## Data

### Into Storagebox

There are 2 ways to import data into a Storagebox, listed below in preferential order

#### Direct Transfer

!!! tip
    The ideal method is to transfer files directly into Storagebox independently of ElfHosted

The advantage to Hetzner's Storageboxes is that you can add content to them independently of ElfHosted's infrastructure entirely. I.e., from a remote location, you can SFTP/SMB/WebDAV your data into your storagebox, before you're even an ElfHosted user!

The simplest way to transfer into a Storagebox is simply to mount it as a drive on your desktop via Samba, and drag/drop your content across.

!!! note
    When using a Storagebox via SMB with a subaccount, the share name you're connecting to **must** be the same as the username of the subaccount

If you'd prefer something automated for a more complex migration, here are some sample rclone configs you can use to transfer data in. In testing, we found best performance with Samba, followed by WebDAV, and finally SFTP:

=== "Samba (main account)"
    
    ```bash
    [hetzner]
    type = smb
    host = //u*****.your-storagebox.de/backup
    user = u*****
    pass = ************
    ```

=== "Samba (sub account)"
    
    ```bash
    [hetzner]
    type = smb
    host = //u*****-sub**.your-storagebox.de/sub-**
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

#### Using Rclone

!!! tip
    In this case, we use [Rclone][rclone] / [RcloneBrowser][rclonebrowser] on ElfHosted to suck data **into** Storagebox

If you don't **have** a remote location from which transfer data into StorageBox, use [Rclone][rclone] / [RcloneBrowser][rclonebrowser] within ElfHosted, to connect to your remote storage, and start a transfer to `/storage/storagebox-a` (*you need to have purchased a [StorageBox mount][store/storagebox]*). You might use this, for example, if you wanted to bring content from a Dropbox folder into Storagebox.

### Into ElfStorage

#### Pulling data into ElfStorage (preferred)

If your data is elsewhere, and you want to "pull" it into ElfStorage, use [Rclone][rclone] / [RcloneBrowser][rclonebrowser], configure the remote, and copy into `/storage/elfstorage`.

!!! tip
    Using RCloneBrowser is preferable, since you can control the transfer parameters (*rate, etc, to avoid impacting other users*).

#### Pushing data into ElfStorage

Unlike Hetzner's Storageboxes, you can't transfer data into ElfStorage directly, so if you want to **push** data into ElfStorage, you'll need to add [Minio][minio] to your apps, and then use Minio as an S3-compatible endpoint transfer data **into** ElfStorage.

!!! warning
    You'll need to throttle down your requests/sec to below 5, to avoid 429 errors

## Config

You may have app databases you'd like to migrated into ElfHosted. Usually, you'd stop an app, copy over its config, and then start it up. Because of our Kubernetes design, you can't actually **stop** your apps, but you can use ElfBot to trigger a restart-pause for an arbitrary period. 

Here's an example workflow re migrating an Ombi database..

1. Using [FileBrowser][filebrowser], navigate to `config/` and upload your new Ombi config to a folder named `ombi-new`
2. Now in the FileBrowser CLI, run `elfbot restart-pause ombi 10` to trigger a paused restart for 10 minutes
3. ElfBot will restart your Ombi pod, and wait for 10 minutes before continuing starting it up. Within 10 minutes, rename `/config/ombi` to `/config/ombi-old`, and rename `/config/ombi-new` to `/config/ombi`. 
4. After 10 minutes, Ombi will start normally, referencing your restored files!


--8<-- "common-links.md"