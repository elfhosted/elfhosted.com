---
title: Elf Hosted Iceberg 🧝 from $0.05/day
slug: Iceberg
description: Iceberg is a WIP rewrite of plex_debrid, supporting Plex torrent streaming through Real Debrid and 3rd party services like Overseerr, Mdblist, etc.
upstream: https://github.com/dreulavelle/iceberg
links:
- name: Discord
  uri: https://discord.gg/wDgVdH8vNM
- name: project board
  uri: https://github.com/users/dreulavelle/projects/2
---

# {{ page.meta.slug }}

Iceberg is a rewrite of [plex-debrid][plex-debrid], enabling Plex torrent streaming through Real Debrid and 3rd party services like Overseerr, Mdblist, etc.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How to use it

### Onboarding

#### General Settings

When prompted, set 

* **Host Path**: `/storage/elfstorage/downloads`
* **Container Path**: `/storage/realdebrid-zurg`

and paste in your [Real-Debrid][real-debrid] API key (*get it [here](https://real-debrid.com/apitoken)*)

![](/images/iceberg-setup-step-1.png)

#### Step 2 / 4

Set your Plex URL to `http://plex:32400`, and authenticate

![](/images/iceberg-setup-step-2.png)

#### Step 3 / 4

When prompted for content services, use either `http://jellyseerr:5055` or `http://overseerr:5055`, depending which app you use. Navigate to Overseerr / Jellyseerr, retrieve your API key from **Settings** -> **General** --> **API Key**, and paste it in.

![](/images/iceberg-setup-step-3.png)

#### Step 4 / 4

![](/images/iceberg-setup-step-4.png)


##### Torrentio

To use ElfHosted's internal, unrestricted torrentio instance, set **Torrentio URL** to `http://elfhosted.torrentio`[^1]

##### Jackett

To use your own ElfHosted [Jackett][jackett] instance, set the URL to `http://jackett:9117`, and paste in your API key (*retrieved from the Jackett UI*)

{% include 'app_footer.md' %}

[^1]: No, that's not a typo, it's a [Kubernetes service](https://github.com/funkypenguin/elf-infra/blob/ci/torrentio/service-elfhosted.yaml) called `elfhosted` in the namespace `torrentio`, on port `80`!