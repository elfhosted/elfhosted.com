---
slug: autobrr
---

# Autobrr

## What is it?

 Buy now

[Add to Cart :fontawesome-solid-hat-wizard:](#){ .md-button .md-button--primary }


Autobrr monitors IRC announce channels to get releases as soon as they are available, with good filtering.

![Screenshot of {{ page.meta.slug }}](/images/screenshots/{{ page.meta.slug }}.png){ loading=lazy }

Features include:

- Single binary + config for easy setup
- Support for 30 trackers
- Easy to use UI
- Available torrent actions:
  - qBittorrent
  - Deluge
  - Radarr
  - Sonarr
  - Lidarr
  - Save to watch folder
  - Run custom commands

## How do I use it?

Once you've enabled it in [your account](https://elfhosted.com/tenant/apps/0), launch the app via your dashboard. 

Upon launch, you'll be prompted to create a username/password. Once this is completed, you'll be able to access the app, and configure your indexers, groups, etc.

To connect to other apps, refer to [Interconnecting-Apps](/Reference/Interconnecting-Apps)
  
## Common connection to Torrent Clients

### Deluge 

* Type: `Deluge 2`
* Host: `deluge`
* Port: `58846`
* Username - `autobrr` 
* Password - `c7RJKKt#KBcM5Z?a`

### qBitorrent

* Type: `qBittorrent`
* Host: `http://qbittorrent:8080` 
* Username/Password: `<leave blank>`

### ruTorrent

* Type: `rTorrent`
* Host: `http://rutorrent:8080/plugins/rpc/rpc.php`

## How do I get support?

1. For general use of the application itself, refer to the [upstream project](https://autobrr.com/)
2. For specific support re your ElfHosted configuration / account, either consult the #[elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303) channel, or call for [#elf-care](https://discord.com/channels/396055506072109067/1119478614287712337).

## Useful links

* https://autobrr.com/
* https://www.reddit.com/r/seedboxes/comments/t7kpkz/a_comprehensive_guide_on_how_to_automate_your/