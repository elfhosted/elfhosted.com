# Seafile


## What is it?

Seafile is an open-source, cross-platform file-hosting software system. 

Files are stored on a central server and can be synchronized with personal computers and mobile devices through apps. 

Files on the Seafile server can also be accessed directly via the server's web interface.

Files on the server can be encrypted with client-side encryption, so that only authorized clients can view them.

## How do I use it?

Once you've enabled it in [your account](https://elfhosted.com/tenant/apps/0), launch the app via your dashboard.

Upon first login, you'll be prompted for credentials. Your credentials have been pre-setup as follows:

* User: `<username>@elfhosted.com`
* Password: `changeme`

You should immediately navigate to settings, and change your password. Ideally, let the `<username>@elfhosted.com` user remain unused as a backup admin user, and add your own independent admin user.

**Once** you have changed the password, **then** disable SSO to permit access from desktop/mobile clients for syncing (*See [Dangers_of_disabling_SSO](/Reference/Dangers_of_disabling_SSO) for context*)

## Can I access synced data from my other apps?

**No**. Seafile uses git-like commits to track the sync state of files, which is why it's so fast, but consequently the files are unreadable in any other app. If you want to transfer files for the purposes of accessing with other apps (*i.e. streaming with [Jellyfin](/Apps/Jellyfin)*), then use [File Browser](/Apps/File_Browser) or [Minio](/Apps/Minio).

## Can you see my files?

**No**. All we can see are blobs. And if you enable encryption on your libraries, all we'll see are encrypted blobs!

## How do I get support?

1. For general use of the application itself, refer to the [upstream project](https://www.seafile.com/en/support/) or the [subreddit](https://www.reddit.com/r/seafile/).
2. For specific support re your ElfHosted configuration / account, either consult the #[elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303) channel, or call for [#elf-care](https://discord.com/channels/396055506072109067/1119478614287712337).

## Useful links

* https://www.seafile.com/en/support/
* https://www.reddit.com/r/seafile/