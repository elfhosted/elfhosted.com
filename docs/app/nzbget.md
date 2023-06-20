# NZBGet

## What is it?

NZBGet is an efficient usenet downloader.

## How do I use it?

Once you've enabled it in [your account](https://elfhosted.com/tenant/apps/0), launch the app via your dashboard.

Most of the configuration is already fine-tuned for our enviornment (so take care making changes!), but you'll want to configure your own news servers before NZBGet will download anything.

## How do I restart it?

!!! warning
    Because `/tmp` is on a tmpfs (*to make it uber-fast to download and unpack, before transferring to storage*), if you restart the pod, you'll lose everything currently in `/tmp`. If you're going to restart NZBGet, you'll want to pause downloads, ensure that any pending downloads have been moved to `/storage`, and **then** perform the restart.

## How do I get support?

1. For general use of the application itself, refer to the [upstream project](https://nzbget.net) or the [subreddit](https://www.reddit.com/r/nzbget).
2. For specific support re your ElfHosted configuration / account, either consult the #[elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303) channel, or call for [#elf-care](https://discord.com/channels/396055506072109067/1119478614287712337).

## Useful links

* https://nzbget.net
* https://www.reddit.com/r/nzbget