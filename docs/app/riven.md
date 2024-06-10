---
title: Seamless Plex / Debrid automation with Riven
slug: Riven
description: Riven is a WIP rewrite of plex_debrid, supporting Plex torrent streaming through Real Debrid and 3rd party services like Overseerr, Mdblist, etc.
upstream: https://github.com/rivenmedia/riven
sponsorship:
- uri: https://github.com/dreulavelle
  name: GitHub Sponsors
links:
- name: Discord
  uri: https://discord.gg/wDgVdH8vNM
- name: project board
  uri: https://github.com/users/dreulavelle/projects/2
- name: GitHub repo
  uri: https://github.com/rivenmedia/riven
---

# {{ page.meta.slug }}

Riven (*previously Iceberg*) is a rewrite of [plex-debrid][plex-debrid], enabling Plex-based torrent streaming through Real Debrid and 3rd party services like Overseerr, Mdblist, etc.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How to use it

!!! warning "UI is non-functional pending dev updates"
    The screenshots below represent the old Iceberg code, whose UI is not yet working with Riven.
    
    To use Riven, you'll need to use [FileBrowser][filebrowser] to edit `config/riven/settings.json`, and [Kubernetes Dashboard][kubernetes-dashboard] to watch the pod logs for success.

## UI details for future (not currently working)

### Onboarding

#### General Settings

When prompted, set 

* **Rclone Path**: `/storage/realdebrid-zurg/__all__ `
* **Library Path**: `/storage/symlinks`

and paste in your [Real-Debrid][real-debrid] API key (*get it [here](https://real-debrid.com/apitoken)*)

![](/images/iceberg-setup-step-1.png)

#### Step 2 / 4

Set your Plex URL to `http://plex:32400`, and authenticate

![](/images/iceberg-setup-step-2.png)

#### Step 3 / 4

When prompted for content services, select your Plex watchlist - if you're a [Overseer][overseerr] / [Jellyseer][jellyseerr] user, use either `http://jellyseerr:5055` or `http://overseerr:5055`, depending which app you use. Navigate to Overseerr / Jellyseerr, retrieve your API key from **Settings** -> **General** --> **API Key**, and paste it in.

![](/images/iceberg-setup-step-3.png)

#### Step 4 / 4

![](/images/iceberg-setup-step-4.png)

##### Torrentio

To use ElfHosted's internal, unrestricted torrentio instance, set **Torrentio URL** to `http://elfhosted.torrentio`[^1]

##### Jackett

To use your own ElfHosted [Jackett][jackett] instance, set the URL to `http://jackett:9117`, and paste in your API key (*retrieved from the Jackett UI*)

#### Now what?

You'll see a summary of your setup displayed. Click "Status" to look at your requests / queue / library:

![](/images/iceberg-setup-step-5.png)

### Where do I find my files?

Iceberg will put symlinks in `/storage/symlinks/movies` and `/stories/symlinks/tv`

### Where do I find logs?

To see what Iceberg is up to, use [Filebrowser] to inspect the logs in `config/iceberg/`


{% include 'app_footer.md' %}

[^1]: No, that's not a typo, it's a [Kubernetes service](https://github.com/funkypenguin/elf-infra/blob/ci/torrentio/service-elfhosted.yaml) called `elfhosted` in the namespace `torrentio`, on port `80`!
