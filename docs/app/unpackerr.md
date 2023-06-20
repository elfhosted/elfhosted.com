# Unpackerr


## What is it?

Unpackerr extracts downloads for Torrents, [Radarr](/Apps/Radarr), [Sonarr](/Apps/Sonarr), [Lidarr](/Apps/Lidarr), [Readarr](/Apps/Readarr), and deletes extracted files after import . Use it to automatically unpack archives after download.

## How do I use it?

Simply enable Unpackerr it in [your account](https://elfhosted.com/tenant/apps/0). You won't see it appear on your dashboard, since it's just a daemon running in the background. 

### Troubleshooting

You can examine the Unpackerr logs using [File Browser](/Apps/File_Browser), at `/config/unpackerr/logs/`. Log files are auto-rotated, so there's no need to worry about truncation, etc.

### Advanced customization

Unpackerr should "just work", provided you use both the built-in API keys for the Arr apps, and download to `/media/downloads/completed`. For more advanced Unpackerr options, you may (using [File Browser](/Apps/File_Browser) edit `/conf/unpackerr/unpackerr.conf` and make further customizations.

## How do I get support?

1. For general use of the application itself, refer to the [upstream project](https://github.com/davidnewhall/unpackerr)
2. For specific support re your ElfHosted configuration / account, either consult the #[elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303) channel, or call for [#elf-care](https://discord.com/channels/396055506072109067/1119478614287712337).

## Useful links

* https://github.com/davidnewhall/unpackerr