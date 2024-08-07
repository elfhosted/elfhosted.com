---
title: Elf Hosted Sonarr 🧝
slug: Sonarr
description: Sonarr is a PVR for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them
upstream: https://sonarr.tv/
links:
- name: wiki
  uri: https://wiki.servarr.com/sonarr
- name: subreddit
  uri: https://www.reddit.com/r/Sonarr
sponsorship: 
- name: Open Collective
  uri: https://opencollective.com/sonarr
- name: Bitcoin
  uri: https://sonarr.tv/donate
---

# {{ page.meta.slug }}

Sonarr is a PVR for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them. 

It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available. 

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

Sonarr will be pre-configured for the other supported apps. By default, Sonarr HD is configured to seek out only 1080P content which can reliably be direct-played / transcoded on a range of equipment and bandwidth constraints. If you have the hardware / bandwidth to direct-play 4K content, you'll need to update the profiles yourself.

### Import existing remote media

If you have existing remote media mounted at `/storage/<something>` (*like Real-Debrid*), you can [use ElfBot to create symlinks](/app/elfbot#how-to-import-symlinks) to bring this into your Sonarr library, without consuming any more space.

Here's how the process works. The end result is that Plex only sees `[3]: /storage/symlinks/series`:

```mermaid
flowchart TD
    E["DMM/Torrentio"] --> |creates files in..|A
    A["[1]: /storage/realdebrid-zurg/shows"] -->|elfbot creates symlinks to...| B("[2]: /storage/symlinks/import/shows/")
    D[Plex] --> |Library points to...|C
    B --> |Sonarr manual imports to..|C["[3]: /storage/symlinks/series"]

```

To perform a symlink import using [ElfBot][elfbot], run `elfbot symlink /storage/realdebrid-zurg/shows`. ElfBot will symlink any **new**  content at `/storage/realdebrid-zurg/shows` to `/storage/symlinks/import/shows`. After this, use Sonarr to perform an automatic / interactive manual import from `/storage/symlinks/import/shows/`.

In Sonarr, use `Wanted` -> `Manual Import`, and point the import at `/storage/symlinks/import/shows/`, as illustrated below:

![](/images/sonarr-wanted-manual-import.png)

!!! warning "Not Library Import"
    We're not importing an organized library here, we're importing a messy bunch of files created by DMM / Stremio. Use `Wanted` -> `Manual Import` instead, since this will rename and upgrade your content, and move it to existing libraries

### Add TRaSH Guides

The [TRaSH guides](https://trash-guides.info/) utilize custom formats and quality profiles to fine-tune the media that Sonarr downloads.

There are 3 ways to configure Radarr for the TRaSH guides:

1. Run `elfbot recyclarr sync` from [FileBrowser][filebrowser]'s console (*manual, super-easy*)
2. Subscribe to the [Recyclarr][recyclarr] service, and have Recyclarr sync with Sonarr on a daily basis (*automatic, fire-and-forget*)
3. [Manually apply the TRaSH guides settings](/guides/media/optimize-series-quality-with-trash-custom-formats/) to Sonarr (*manual, complex*)

{% include 'app_footer.md' %}