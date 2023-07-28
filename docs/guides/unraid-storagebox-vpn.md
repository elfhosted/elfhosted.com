---
title: Outsource your media management/aquisition, consume it on your unRAID
description: Running unRAID but want to offload media management/aquisition? Here's how to use ElfHosted, a Hetzner Storagebox, and UnRAID plugins to achieve this!
---
# "Outsource" your unRAID media management/aquisition to ElfHosted

unRAID is an incredibly popular platform for home media management, providing storage, apps, and virtualization. Many happy geeks are running a local unRAID platform, maintaining their own "data hoard", and using platform to run media streaming apps (*[Plex][plex], [Jellyfin][jellyfin], [Emby][emby], etc*) locally at home.

## Why ElfHosted?

ElfHosted plus a [Hetzner StorageBox]( https://www.hetzner.com/storage/storage-box) compliments the unRAID setup perfectly, providing:

* [x] Cost-effective remote storage when you need more capacity for media you don't care to store at home
* [x] Transparent mounting of this storage into the local unRAID for local consumption
* [x] "outsourcing" of media management/aquisition apps ([Radarr][radarr], [Sonarr][sonarr], [qBittorrent][qbittorrent], etc)
* [x] Possibility of sharing media without exposing your home unRAID instance to the internet

!!! tip "Torrent to unRAID without requiring a VPN"
    Importantly, with ElfHosted's BYO VPN design, you can run [qBittorrent][qbittorrent], [Deluge][deluge], or [ruTorrent][rutorrent], saving data directly to your Storagebox, and consume it locally at home on unRAID, without having to secure and manage the torrent client / VPN components at home!

## Step-by-step

### What you'll need:

* [x] A VPN (*either a [supported provider](https://github.com/qdm12/gluetun-wiki/tree/main/setup/providers), or your own custom Wireguard / OpenVPN config*)
* [x] A Hetzner Storagebox in the Germany location

### Aquire a Hetzner Storagebox

Pick your [preferred size storagebox](https://www.hetzner.com/storage/storage-box), ensuring it's located in the Germany / FSN1 / Falkenstein location. This is **your storage**, to keep or expand as you please.

Enable **Samba Support**, and **External Reachability**:

![Screenshot of Storagebox config](/images/guides/unraid-storagebox-1.png)

Reset your password (*you're not given one initially*) and store it securely.

!!! question "What do we have now?"
    You have a storagebox which you can access remotely

### Grab some ElfHosted apps

* Get a FREE [$10 ElfBuckz starter pack](https://store.elfhosted.com/product/elfbuckz-10-starter-pack/) with coupon code `ELFELFBABY`, check out and create your account. Now you have an ElfBuckz balance!
* Subscribe to a [Storagebox mount](https://store.elfhosted.com/product/hetzner-storagebox-mount/), enter your storagebox details (*you can optionally use a subaccount*)
* Subscribe to [qBittorrent](https://store.elfhosted.com/product/qbittorrent/) / [Deluge](https://store.elfhosted.com/product/deluge/) / [ruTorrent](https://store.elfhosted.com/product/rutorrent/) - plug in your VPN details (*if your VPN provider isn't listed yet, get in touch via [#elf-help][elfhelp], and we'll add it!*)
* Optionally, add other media management apps you need such as [Radarr][radarr], [Sonarr][sonarr], [Prowlarr][prowlarr], etc.
* Pay with your ElfBuckz balance! 🧝💰 (*when it runs out, you can top it up at from [my account](https://store.elfhosted.com/my-account/account-funds/)*)

Configure your apps to save your media to `/storage/storagebox-a`.

!!! question "What do we have now?"
    Now you're able to download media to your StorageBox

### Connect to unRAID

Ensure your unRAID has "[Unassigned Devices](https://github.com/dlandon/unassigned.devices)" app installed:

![Screenshot of Unassigned Devices unRAID app](/images/guides/unraid-storagebox-2.png)

Navigate to the plugin and select "**Add Remote SMB/NFS Share**":

![Screenshot of adding remote SMB/NFS share to unRAID](/images/guides/unraid-storagebox-3.png)

When prompted to choose a protocol, click on the "Windows icon" to choose SMB:

![Screenshot of adding remote SMB/NFS share to unRAID, step 2](/images/guides/unraid-storagebox-4.png)

Enter the servername of your storagebox 

![Screenshot of adding remote SMB/NFS share to unRAID, step 2](/images/guides/unraid-storagebox-5.png)

Enter your username

![Screenshot of adding remote SMB/NFS share to unRAID, step 3](/images/guides/unraid-storagebox-6.png)

Enter your password (*scored securely earlier*)

![Screenshot of adding remote SMB/NFS share to unRAID, step 4](/images/guides/unraid-storagebox-7.png)

When prompted for a domain, leave the value blank and just click Next:

![Screenshot of adding remote SMB/NFS share to unRAID, step 6](/images/guides/unraid-storagebox-8.png)

Finally, when prompted for a share, enter `backup` (*or the name of your subaccount, if you're using one*), and click `Done`:

![Screenshot of adding remote SMB/NFS share to unRAID, step 7](/images/guides/unraid-storagebox-9.png)

!!! warning "A subaccount can only see a share with the same name"
    You won't be able to see the `backup` share with a subaccount. You'll have to use a share with the same name as the subaccount.

Now, you can mount your share, and happily consume the media on your remote storagebox, locally! :thumbsup!

![Screenshot of adding remote SMB/NFS share to unRAID, step 8](/images/guides/unraid-storagebox-10.png)

!!! question "What do we have now?"
    You're able to view the media on your storagebox alongside the exitsing media on your unRAID, and transfer files to/from Storagoebox

### Optional extras

Want to share your media with friends and family without exposing your unRAID? Install [Plex][plex], [Jellyfin][jellyfin], or [Emby][emby], and point your libraries at your storagebox, at `/storage/storagebox-a`

## Questions

### Storagebox location

Question:

> What if my storagebox is in Finland, and not Germany?

Answer:

> The torrent-client->storagebox performance will likely be much worse, and Hetzner will ultimately charge me for egress traffic (not currently an issue at our scale), so I'd strongly suggest sticking with Germany

### Integrating local apps

Question: 

> Can my apps (Arrs) running locally on unRAID talk to the torrent clients?

Answer:

> No, because the torrent clients are all protected with a layer of SSO which is applied at the ingress (Traefik) level. While we can **technically** enable/disable SSO per-app (*some apps like Plex are obviously not SSO'd*), the torrent apps will always remain behind SSO due to the risk of an accidental misconfiguration exposing all our customers to suspension / shutdown.

> Any ElfHosted apps can connect with the torrent clients though, so while it's not a **perfect** solution, you may be able to configure [Sonarr][sonarr] / [Radarr][radarr] to import from your home Arr instances.

## Now what?

That's it, you're done. Hope into our [friendly Discord server][discord] if you have questions or suggestions!

--8<-- "common-links.md"