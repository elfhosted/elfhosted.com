---
title: Add requests to Overseerr from Plex
slug: Plex-Requests
description: Use this clever workaround to "trick" Plex into adding wanted content to your Overseerr library
upstream: https://github.com/westsurname/scripts/
works_with:
- Plex
- OverSeerr
---

# {{ page.meta.slug }}

Plex Requests in a collection of several clever "microservices" which "abuse" the Plex API to make it possible to add requests to Overseerr, directly from Plex apps.

![Screenshot of {{ page.meta.slug }}](/images/screenshots/{{ page.meta.slug | lower }}.gif){ loading=lazy }

## How do I use {{ page.meta.slug }}?

There's no UI, but you can watch the logs of the various containers using [Kubernetes Dashboard][kubernetes-dashboard]

## Setup

You'll need to supply several values to plex-requests as environment variables, using [ElfBot][elfbot] commands in [ElfTerm][elfterm].

### Machine ID

Visit `https://<your plex url>/identity`, and note the `machineIdentifier` value. 

Provide this to plex-requests using:

```
elfbot env plexrequests PLEX_SERVER_MACHINE_ID=machineidentifiergoeshere
```

### Server Token

Visit https://plex.tv/devices.xml (*you must be signed in*), and search the resulting XML for the machine identifier identified above. A token will be related to this identifier. Provide the token to plex-requests using:

```
elfbot env plexrequests PLEX_SERVER_API_KEY=machinetokengoeshere
```

### Overseerr API Key

Grab your Overseerr API key (General -> Settings), and feed it to plex-requests using:

```
elfbot env plexrequests OVERSEERR_API_KEY=yourkeygoeshere
```

### Setup auth

Visit `https://<your plex url>/auth`, and process the authentication once. You should receive a JSON result indicating the token was successfully processed.

!!! tip "Do this once per-user"
    If you want to identify **which** of your users requested a particular item, you'll need each user to perform the auth step once. This is also required for the addition of content via user's watchlist.

## Usage

When you search Plex, you'll find Plex usually returns items you **don't** already have in your library. 

![](/images/plex-requests-search-1.png)

(*Disable any shared libraries or sources you don't want to search*)

Plex-requests "augments" these search results with a link to your server, labeled `(server name) REQUEST:`:

![](/images/plex-requests-search-2.png)

### Overseerr

After you're requested something via Plex Requests, you should be able to verify it's been requested in your Overseerr, and fulfilled downstream by the Aars, [Riven][riven], [SeerrBridge][seerrbridge], [plex_debrid][plex-debrid], etc.


### Logs

To watch the Plex Requests logs, use [Kubernetes Dashboard][kubernetes-dashboard], as illustrated below:

![](/images/plex-requests-logs-1.png)

![](/images/plex-requests-logs-2.png)


{% include 'app_footer.md' %}