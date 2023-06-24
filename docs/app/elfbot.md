---
description: ElfBot is a CLI tool for ElfHosted users providing self-service functions such as restarts, backups, and Plex claims
---
# ElfBot

ElfBot is not a standalone app, it's a command-line script written for ElfHosters, which provides self-service functions:

1. Restart apps
2. Reset apps (*wipe config and restore original pre-setup where applicable*)
3. Backup apps (*restart and create offline backup to storage*)
4. Claim plex server

## Activating ElfBot

ElfBot lives in your [FileBrowser][filebrowser] console. Run him like this:

```bash
elfbot <command> <arguments>
```

For example, to restart plex...

```
elfbot restart plex
```

## Restarting apps

## Resetting apps

## Backing up apps

## Claiming Plex server

After you install [Plex][plex], you'll need to "claim" it against your Plex account, by grabbing a claim ID from plex.tv/claim/. Claim your plex server using ElfBot by running:

```bash
elfbot claim plex <token>
```

After the claim is made, you'll need to restart plex. To restart Plex, and access your freshly-claimed instance, run:

```bash
elfbot restart plex
```


--8<-- "common-links.md"