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

Riven (*previously Iceberg*) is a re-imagining of original functions of [plex-debrid][plex-debrid], enabling Plex-based torrent streaming through Real Debrid and 3rd party services like Overseerr, Mdblist, etc.

!!! tip "Riven gets revenue! :heart:"
    Riven is an "Elf-illiated" app - the devs are actively supporting users in our [Discord][discord] community, the app itself is tuned to work perfectly with ElfHosted "out-of-the-box", and 100% of your subscriptions are contributed to the Riven devs to further development!

## How to use it

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZHZAEhLuJqk?si=t5HJ5RT8UOfDDuXs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Unlike most ElfHosted apps, Riven is (currently) split into two - the frontend, and the backend:

### Meet the backend

The Riven backend is what's functionally complete. On the backend, you'll see the logs displayed as Riven searches for your content, adds it to your RealDebrid library, symlinks it to `/storage/symlinks`, and updates Plex accordingly

![](/images/riven-backend.png)

To restart the backend, hit `CTRL-C` once in the ttyd/browser UI to terminate the process, and then hit `Enter` to reconnect to the session and watch it restart.

### Meet the frontend

The frontend UI is a work-in-progress, but there are enough pieces in place to enable a basic onboarding. The frontend is also critical for setting up Plex authentication.

### Making configuration changes

Until the frontend UI is completed, configuration changes are effected by updating `settings.json` in `config/riven`, via [FileBrowser][filebrowser].

### Minimum requirements

At a minimum, Riven requires:

* [x] Your RealDebrid API key
* [x] A [claimed][elfbot] [Plex][plex] server
* [x] A [Plex token][plex-token]

And optionally, Riven will work with:

* [ ] An [Overseerr][overseerr] instance, for managing media requests
* [ ] A [Jackett][jackett] instance, to provide additional content scraping targets
  
### Basic setup

#### Overseerr

To integrate Overseerr with Riven, setup Overseerr to integrate with Plex, and then..

* :one: Get your API key:

![](/images/riven-overseerr-1.png)

* :two: Configure a webhook pointing to `http://riven:8080/webhook/overseerr`:

![](/images/riven-overseerr-2.png)

* :three: Enable your webhook for `Request Automatically Approved` and `Request Approved`:

![](/images/riven-overseerr-3.png)

#### Frontend 

To perform a basic Riven setup, use the frontend, and navigate to Settings:

![](/images/riven-settings-1.png)

Under **General**, ensure your RealDebrid API token is applied and correct (get it [here](https://real-debrid.com/apitoken)):

![](/images/riven-settings-2.png)

!!! warning "Plex auth broken in v0.7.5"
    At present, it's not possible to perform Plex authentication via the UI. Use [this guide][plex-token] to get your Plex token, and paste it into your `config/riven/settings.json` directly.
    
Under **Media Server**, click `Authenticate with Plex` to retrieve the token necessary for Riven to interact with Plex:

![](/images/riven-settings-3.png)

Under **Content**, paste in your Overseerr API key, and enable `Overseerr Use Webhook`:

![](/images/riven-settings-4.png)

That's it, a minimal configuration! :partying_face: Now load the backend, and watch the magic! :magic_wand:

{% include 'app_footer.md' %}