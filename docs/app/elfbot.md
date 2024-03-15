---
title: ElfBot, your helpful ElfHosted CLI tool
description: ElfBot is a CLI tool for ElfHosted users providing self-service functions such as restarts, backups, and Plex claims
---
# ElfBot

ElfBot is not a standalone app, it's a command-line script written for ElfHosters, which provides self-service functions, including:

1. Pause apps
2. Restart apps
3. Reset apps (*wipe config and restore original pre-setup where applicable*)
4. Backup apps (*restart and create an offline backup*)
5. Claim a plex server
6. Set an arbitrary ENV var for an app (*advanced, beta feature*)

## Using ElfBot

ElfBot lives in your [FileBrowser][filebrowser] console. 

![ElfBot in FileBrowser console](/images/elfbot-filebrowser-console.png)

Run ElfBot like this:

```bash
elfbot <command> <arguments>
```

For example, to restart plex...

```
elfbot restart plex
```

### How to stop / suspend an app

You may need to turn an app off temporaily to adjust its config, or to perform a restore from backup. Run `elfbot pause <app>` (*`<app>` should match the name of a folder under `/config`*), and ElfBot will shutdown the app, and wait for 5 min, before starting the app again.

### How to restart an app

ElfBot can restart your app. Run `elfbot restart <app>` (*`<app>` should match the name of a folder under `/config`*), and ElfBot will instantly trigger an app restart.

Occasionally circumstances will prevent a graceful restart of an app (*node failure, kernel bug, etc*). In such cases, a regular `elfbot restart` won't work on the app, its pod will stay in a terminating state.

In this event, the only recourse is to "force restart" the app - if the app hasn't properly saved its data, you may loose data as a result, but in the case of a stuck pod, you have no other recourse.

To "force restart" an app, run `elfbot restart <app> --force --yesiamsure` - ElfBot will instantly remove the pod (*rather than waiting for it to terminate*), and a replacement pod will be scheduled.

!!! tip "Restarting all at once"
    You can use `elfbot restart all` to restart **all** your apps at the same time (*although it's hard to imagine a situation where this would be required*)

### How to reset an app

Need to reset an app to defaults? Run `elfbot reset <app> --yesiamsure` to perform the reset. ElfBot will restart your app, and remove its config from `/config`, resulting in a fresh bootstrap or a clean install.

!!! warning
    This command will result in data loss. There are no further confirmations beyond `--yesiamsure`. If you're uncertain, perform a backup of your app before resetting (*below*).

!!! danger
    You can also use `all` here, as in `elfbot reset all` - but be aware that it'll do exactly what it says, and wipe **ALL** of your app data! (*not your ElfStorage though!*). There's no going back from this!

### How to backup an app

In order to safely backup an app, the app can't be running. ElfBot can trigger a restart of your app, and before the app actually starts, make a backup of its config folder to `/storage/elfstorage/backup/<app name>-<timestamp>`.

Run:

```bash
elfbot backup <app>
```

To perform the backup!

Here's an example:

![ElfBot backup result](/images/elfbot-backup-1.png)

And here's the resulting backup:

![ElfBot backup result](/images/elfbot-backup-2.png)

### How to Claiming a Plex server

After you install [Plex][plex], if you find that you're just presented with a "web player", you'll need to "claim" it against your Plex account, by grabbing a claim ID from plex.tv/claim/. Claim your plex server using ElfBot by running:

```bash
elfbot claim plex <token>
```

After the claim is made, you'll need to restart plex. To restart Plex, and access your freshly-claimed instance, run:

```bash
elfbot restart plex
```

### How to set an ENV var for an app

If you need to set a custom ENV var for an app (*for [VaultWarden][vaultwarden]'s `ADMIN_TOKEN`, for example*), you can use ElfBot to apply it to the app, by running:

```bash
elfbot env <app> <key>=<value>
```

For example:

```bash
elfbot env vaultwarden ADMIN_TOKEN=thisisnotasecuretoken
```

Be aware that this process has some limitations, namely:

1. You can't see the ENV vars you've already set
2. You can't delete an ENV var, but you can set its value to nothing ('')
3. Only the apps below are supported (*Seek [#elf-help][elf-help] if you need an app added*):

#### Apps supporting custom ENV vars

* [VaultWarden][vaultwarden]
* [Plex Meta Manager][plex-meta-manager]

### How to manage symlinks

If you've attached read-only external storage, which is managed outside of your ElfHosted tools (*[Real-Debrid][real-debrid] with [Debrid Media Manager](https://debridmediamanager.com/), for example*), then you may find that you have content in `/storage/<provider>` which you can't change (*rename, move, organize, etc*).

This read-only content can be cumbersome to manage via [Radarr][radarr] / [Sonarr][sonarr] for example, which require read/write access to rename files, delete old files on quality upgrade etc.

ElfBot can help with this by creating a symlink to the remote content, in `/storage/symlinks/import/`. You can then manipulate this symlink as if it's a regular file (*rename, move into subfolders, etc*), but when accessed, it'll point to the original (*read-only*) content.

#### Manually Importing symlinks

To perform a symlink import, run `elfbot symlink <path to read-only storage>`, or navigate using FileBrowser to a specific folder, and run `elfbot symlink here` to import from the current directory specifically. 

ElfBot will symlink any **new**  content in the target directory to `/storage/symlinks/import/<directory>`. After this, you point the Aars at the `/storage/symlinks/import/` path, and tell them to perform an interactive import.

For app-specific details, see:

* [Radarr](/app/radarr/#import-existing-remote-media)
* [Sonarr](/app/sonarr/#import-existing-remote-media)

ElfBot keeps track of the content it's already symlinked - it won't re-create a symlink which you've already created, and then moved/renamed elsewhere. If you'd like to wipe ElfBot's memory, and recreate **all** symlinks, then delete the `/storage/symlinks/.symlinks_cache` folder!

#### Automatically Importing symlinks (blackhole)

Another way to manage the importing of symlinks is to create a "Usenet Blackhole" downloader in Radarr/Sonarr, and then have ElfBot import your downloads directly into that folder, for the Aars to srape. "Blackholed" imports work a little differently to symlink imports, in that the parent folder is not recreated within the blackhole target, but the contents of the current path in filebrowser are symlinked directly into the target.

For example, navigating to `storage/realdebrid-zurg/shows/My Favorite Show - Season 1`, and running `elfbot blackhole sonarr`, will result in all files **under** `storage/realdebrid-zurg/shows/My Favorite Show - Season 1` being symlinked into `/storage/symlinks/blackhole/sonarr/` (*and subsequently "sucked up" by Sonarr, if it's configured*)

See Aar-specific details here:

* [Radarr](/app/radarr/#import-existing-remote-media)
* [Sonarr](/app/sonarr/#import-existing-remote-media)

#### Finding broken symlinks

If the source of your symlinks become unavailable (*is removed from your storage provider for any reason*), the symlink will remain, but you'll be unable to access the content, and the arrs won't notice that it's missing.

To find these "broken symlinks", run `elfbot symlink report-broken` - you'll find a report generated at `/storage/symlinks/report.txt `

#### Delete broken symlinks

To bulk-delete all broken symlinks (*so the aars can re-search for them*), run `elfbot symlink delete-broken`. Only valid symlinks will survive!


--8<-- "common-links.md"