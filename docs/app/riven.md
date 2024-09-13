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

### Meet the frontend UI

A lot of progress has been made on the frontend UI! It can be used for the entire on-boarding process, with the exception of the quality/ranking settings. These settings are currently configuired in the `settings.json` file found in `config/riven via [FileBrowser][filebrowser]. All of the other settings can be directly modified with the frontend UI, in addition to a number of Riven functions.

### Meet the backend

The Riven backend is what's functionally complete. On the backend, you'll see the logs displayed as Riven searches for your content, adds it to your RealDebrid library, symlinks it to `/storage/symlinks`, and updates Plex accordingly

![](/images/riven-backend.png)

To restart the backend, hit `CTRL-C` once in the ttyd/browser UI to terminate the process, and then hit `Enter` to reconnect to the session and watch it restart.

### Minimum requirements

At a minimum, Riven requires:

* [x] Your RealDebrid API key
* [x] A [claimed][elfbot] [Plex][plex] server
* [x] A [Plex token][plex-token]

And optionally, Riven will work with:

* [ ] An [Overseerr][overseerr] instance, for managing media requests
* [ ] A [Jackett][jackett] instance, to provide additional content scraping targets
* [ ] A [Prowlarr][prowlarr] instance, to provide additional content scraping targets
  
### Basic setup

#### Zurg

First and formost, you **must** first setup Zurg before any setup can be completed with Riven itself. 

* :one: Retrive your Real-Debrid API token via (their website)[https://real-debrid.com/apitoken].
* :two: Navigate to Zurg's `confiig.yml` file found in `config/riven` via [FileBrowser][filebrowser].
* :three: Add your Real-Debrid token Zurg's `confiig.yml` file and save your changes.
* :four: Restart Zurg, either by using the Elfbot command `elfbot restart realdebird-zurg` or by deleting the pod for Zurg via [Kubernetes][kubernetes].

#### Plex

**Claim your Plex server:**

* :one: Generate your token! Use this nifty (Plex Token Generator)[https://plex-token-generator.elfhosted.com] tool to generate a Plex token. Enter an any product name you'd like (it doesn't matter what it is), an any client ID you'd like (it doesn't matter what it is). Click on `Generate PIN` and then the link to https://www.plex.tv/link/. Input your PIN on the "Link Account" screen. Your token will now be displayed in the Plex Token Generator for you to use.
* :two: Navigate to [FileBrowser][filebrowser] from your Dashboard and issue the following command:
  ```elfbot claim plex YourTokenGoesHere```
* :three: Restart your Plex Server:
  ```elfbot restart plex```

**Create your Plex libraries:**

Using the Plex button on your Dashboard, go to your newly claimed Plex server.

* :one: Create a library for you Movies and set the path to `/storage/symlinks/movies/`.
* :two: Create a library for you TV Shows and set the path to `/storage/symlinks/shows/`.
#### ***NOTE:*** *Make certain you are not enabling any of the features to generate thumbnails or intro/credit detection.*

#### Overseerr

#### ***NOTE:*** *Some of the Overseerr setup is already done by default for new installations or following a reset of the Overseerr app.*

To integrate Overseerr with Riven, first setup Overseerr to integrate with Plex, and then...

* :one: Configure a webhook pointing to `http://riven:8080/webhook/overseerr`:

![](/images/riven-overseerr-2.png)

* :two: Enable your webhook for `Request Automatically Approved` and `Request Approved`:

![](/images/riven-overseerr-3.png)

* :one: Retrieve your Overseerr API key, which will be used in Riven:

![](/images/riven-overseerr-1.png)

#### Riven Frontend UI

To perform a basic Riven setup, use the frontend, and navigate to Settings:

![](/images/riven-settings-1.png)

* :one: General Settings
  - Enable your chosen option in the `Downloaders` section.
  - Input your API key for that downloader.
  - Save your changes.
  
![](/images/riven-settings-2.png) 

* :two: Media Server Settings
  - Enable `Plex Updater` in the `Updaters` section.
  - Authenticate your Plex server within the `Plex Token` section.
  - Save your changes.

![](/images/riven-settings-3.png)

* :three: Content
  - Enable your preferred options (you must choose at least one) in the `Content Providers` section.
    - Please see the `Content Request Providers` sections found below.
  - Apply the relevant settings.
  - Save your changes.

![](/images/riven-settings-4.png)

* :four: Scrapers
  - Enable `Torrentio`, `Knightcrawler`, `Annatar`, `Mediafusion`, and `Zilean`. (up to you if you want use the others)
  - Enable `Ratelimit` for all of them, except for `Zilean`.
  - Save your changes.
  
![](/images/riven-settings-4.png)

* :five: Ranking
***Note:*** *These settings are currently being reworked and dramatically improved. They will soon appear in the Riven frontend UI. Currently, these settings are configuired in the `settings.json` file found in `config/riven` via [FileBrowser][filebrowser].*

Pick a quality profile. Riven, in it's current form, has some built-in quality profiles and these profiles have their own rankings for specific attributes:

- `default` *(DefaultRanking): The default ranking model.*
- `remux` *(BestRemuxRanking): The ranking model for the best remux.*
- `web` *(BestWebRanking): The ranking model for the best web release.*
- `resolution` *(BestResolutionRanking): The ranking model for the best resolution.*
- `overall` *(BestOverallRanking): The ranking model for the best overall quality.*
- `anime` *(AnimeRanking): The ranking model for anime releases.*
- `all` *(AllRanking): The ranking model for all releases.*

Most will pick `overall`, `resolution`, or `remux`.

- Replace `"default"` with your chosen profile:
```
    "ranking": {
        "profile": "overall",
```
- For `"require"`, `"exclude"`, and `"preferred"` please refer to (#🗻┆elf-riven)[https://discord.com/channels/396055506072109067/1253110932062601276] and/or its pinned posts.
- The items below are the various attributes Riven will rank. If you are going to follow the rankings set by your chosen profile, ignore the `"enable"` and `"rank"` fields.
- The `"fetch"` settings are essentially your on/off switch for each of these attributes. Set the ones you want to `true` and set the ones you do not want to `false`.
- The `"enable"` and `"rank"` fields are **only** used if you wish to override the rankings established in the pre-configured quality profile you have chosen.
  - The `"enable"` setting, with a `true` or `false` value, enables or disables your custom rank for any individual attribute.
  - The `"rank"` setting, with a numerical value, establishes your custom rank for any individual attribute.
  ***Note:*** *Rankings for individual attributes accumulate. If a file matches three attributes with individual rankings of `100`, the overall rank of that file will be `300`. Files are then ranked by their overall score.
- Save your changes.
- Restart Riven, either by using the Elfbot command `elfbot restart realdebird-zurg` or by deleting the pod for Zurg via [Kubernetes][kubernetes].

### Content Request Providers *(you must choose at least one)*

#### Plex Watchlist

* :one: Navigate to the Watchlist section of your Plex Media Server settings.
  ```
  https://<username>-plex.elfhosted.cc/web/index.html#!/settings/watchlist
  ```
* :two: Copy the appropriate washlist RSS feed link(s)
* :three: Enable `Plex Watchlist` within the Riven frontend UI `Content` section of its settings.
* :three: Add the RSS feed link(s) to the `Plex Watchlist Rss` setting.
* :four: Save your changes.

#### Overseerr

* :one: Retrieve your Overseerr API key:

![](/images/riven-overseerr-1.png)

* :two: Enable `Overseerr` within the Riven frontend UI `Content` section of its settings.
* :three: Apply the relevant settings:
  - The Overseerr URL is `http://overseerr:5055`
  - Add your Overseerr API key.
  - Enable the `Use Webhook` setting.
* :four: Save your changes.
  
#### Trakt

* :one: Visit the (Create a Trakt API app)[https://trakt.tv/oauth/applications/new] page.
* :two: Name it whatever you like.
* :three: For `Redirect uri:` use the default value of `urn:ietf:wg:oauth:2.0:oob`.
* :four: `Description:`, `Javascript (cors) origins:`, and `Permissions:`can be left blank/default.
* :five: Click on `SAVE APP`.
* :six: Enable `Trakt` within the Riven frontend UI `Content` section of its settings.
* :seven: Apply the relevant settings:
  - Use the `Client ID:` provided is your `Trakt Api Key`.
  - The various Trakt functions are optional, but you should enable one or more of them if you wish to use Trakt with Riven.
* :eight: Save your changes.

That's it, a minimal configuration! :partying_face: Now load the backend, and watch the magic! :magic_wand:

{% include 'app_footer.md' %}
