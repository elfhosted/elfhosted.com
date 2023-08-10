# Get Started

Here's a TL;DR guide to getting started. We'll start simple, and then go through some more interesting options...

## First steps

### Choose your first app(s)

See the "elf-abetically sorted" list of [apps](/apps/), and subscribe to one or more apps from the [store][store].

### Choose a username

On checkout, you'll be asked to verify your email address, and create an account. The username that you use will define the URLs your apps will appear at, so user "johnwick" will end up with [Plex][plex] at `https://johnwick-plex.elfhosted.com`. 

!!! tip
    Choose a sensible username, it can't be changed later. (*`ilikebigbutts007.elfhosted.com` won't be so funny when you invite Grandma :older_woman: to your [Plex][plex] server!*)

### Explore your dashboard

After purchase, you'll receive email confirmation of your order, and your apps will be available at `https://<your username>.elfhosted.com`. Log in, look around. 

Take note of the built-in apps, including:

* Gatus (health tab)
* Tools tab
    * FileBrowser
    * RcloneBrowser
    * RcloneUI
    * RcloneFM

## Get mooar storage!

OK, so now you have some apps, but there's only 10Gi of storage available at `/storage/elfhosted`, what gives?

We're storage-flexible - you can buy from us, attach a Hetzner storagebox, or attach your existing rclone-compatible storage. See BYO Storage for more details.

!!! question "Are we there yet?"

    Depending on the storage you choose, provisioning can be instant, or can take several days. See the table below for indicative timing:

    | Storage     | How long does it take?                          |
    | ----------- | ------------------------------------ |
    | [ElfStorage][elfstorage]       | Instant  |
    | [StorageBox][storagebox]       | Depends on your relationship with Hetzner. It can be 1-2h, but users have reported multi-day delays waiting on Hetzner to approve their accounts|
    | [Rclone][rclone]    | Instant (*if it's an existing product*), else ~<24h to test and productize |

### Buy from us ($0.01/GB)

Just want it to work instantly? Want to grow your storage over time?

Buy some [ElfStorage][elfstorage] from the [store][store/elfstorage] - you can choose your size to the GB, and we'll instantly and transparently add it to your `/storage/elfhosted` mount. Done! :magic_wand:

!!! warning "Welcome to the Hotel Elf-ifornia"
    We can transparently **grow**, but we can't **shrink** an ElfStorage volume. 
    
    If you buy 10TB and later decide you'd prefer 5TB, we have to manually destroy and recreate the volume.

### Storagebox

Not willing to commit TBs of data? We get it. Buy a Storagebox [directly from Hetzner](https://www.hetzner.com/storage/storage-box), then [subscribe to a mount][store/storagebox], we'll make it appear in `/storage/storagebox-a` (*`-b and -c` are available too for multiple storageboxen!*)

!!! tip "What's so great about a StorageBox?"

    Great question! See [here][storagebox] to find out why it's awesome!

### Rclone-compatible

Already got rclone-compatible storage? We can **probably** mount it to your apps. When we've done it before, this process is automatic and provisioning is instant. 

If it's a new config we've not encountered, you'll need to get in touch so that we can test and add an automated product to the store!

!!! question "Do I **need** to mount my rclone storage?"
    No, if you just want to move data around, you can use the built-in rclone apps to migrate data to/from external storage via rclone.
    
    A mount permanently attaches the rclone-compatible storage to your apps, so if you want to play media from Droxbox via Plex, then you'll need a mount.

## Bring your own VPN

If you want to use bittorrent clients, you'll need to bring your existing VPN subscription. If you don't yet **have** a VPN subscription, we can recommend [Private Internet Access](https://www.privateinternetaccess.com/pages/buy-a-vpn/1218buyavpn?invite=U2FsdGVkX18CE8WQvq-yt5OJ9UFpALCzci2Oz_px1uA%2CGuAfcPbAeh-UmP4KJ2uroADgSdY) (*referral link*), who are currently running a big 3-year special, and whose port-forwarding implementation is known to work well. 

Choose your torrent app variant matching your VPN provider. If you don't see your provider listed, get in touch and we can try to add it.

!!! question "What VPN providers can you support?"
    Typically any providers which support WireGuard or OpenVPN.
    
    OpenVPN incurs higher subscription pricing due to its CPU usage compared to WireGuard.

## See you in Discord! :simple-discord:

That's it, we're done!

Where to now?

* [Discord][discord]: Support tickets, new app suggestions, and community support are all here - Jump in and say hi, we're friendly! :wave:
* FAQ: Got more questions? See the [FAQ](/faq/)

--8<-- "common-links.md"
