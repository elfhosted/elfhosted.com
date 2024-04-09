---
title: Get your ElfHosted Stremio Server
slug: Stremio-Server
description: Stremio Server handles downloading and transcoding your remote streams, supporting various Stremio clients and debrid provider implementations
upstream: https://github.com/Stremio/server-docker/
links:
- name: Subreddit (Official)
  uri: https://www.reddit.com/r/Stremio/
- name: r/StremioAddons
  uri: https://www.reddit.com/r/StremioAddons
---

# {{ page.meta.slug }}

Stremio Server is a standalone instance of the component of the official Stremio client app which does the downloading (*torrenting or HTTP streaming*) and transcoding of your remote media.

Usually bundled with the desktop apps, Stremio Server can be useful to host remotely for improved transcoding performance (*i.e., if your client can't transcode your media*), or to consolidate all your Debrid downloads behind a VPN (*providing a single source IP to the debrid provider*).

!!! question "What's the relationship to Official Stremio?"
    The ElfHosted Stremio Server subscription is simply the hosting of an [un-modified](https://github.com/geek-cookbook/containers/blob/main/apps/stremio-server/Dockerfile)[^1] instance of the [publically available](https://github.com/Stremio/server-docker/) docker image, exactly as distributed by Stremio, and subject to the same [terms and conditions](https://www.stremio.com/tos) as any other Stremio installations.

    There's nothing proprietary to the solution, and the subscription price is for the **hosting** components of the service (*CPU, RAM, bandwidth, etc*), and not the Stremio app itself, nor the content consumed by the user.

Possible use-cases for Stremio-Server are:

1. Ensuring all torrenting activity is routed over a VPN.
2. Ensuring all Debrid activity comes from a single source IP, even if multiple clients at multiple locations are streaming simultaneously (*only works in the web UI*)
3. Transcoding media which a client can't natively play (*like an under-powered Android TV*).

!!! warning "Not all Stremio clients support proxying/transcoding HTTP streams!"
    Your Stremio client may not support transcoding of HTTP / Debrid streams. See [Client Compatibility](#client-compatibility) for a list of known client support.

{% include 'app.md' %}

### How to access Stremio-Server

Your ElfHosted app dashboard will link you to either the Stremio web player (`https://web.strem.io`), or your own, ElfHosted instance of [Stremio Web][stremio-web], with a URL path to pre-configure the client for your Stremio Server instance.

You can also manually add your Stremio Server to an existing Stremio client using the URL  `https://<username>-stremio-server-<secret-string>.elfhosted.com`.

!!! question "Why the secret string in the URL?"

    There's no way to authenticate a stremio client against a server - if you know the URL for a server instance, you can use it to download/transcode your media. This allows for the possibility of abuse if users' instances are on predictable URLs like `https://<user>-stremio-server.elfhosted.com`. To mitigate this risk, upon purchasing Stremio Server from the store, you'll be asked to enter a secret string. This string is appended to your URL, and should be kept private. 

## How to use Stremio Server

Navigate to **Stremio Server** from your app dashboard (`https://<your username>.elfhosted.com`) - the Stremio Web UI will automatically configure your streaming server.

Confirm the setup by navigating to **Settings** --> **Streaming**, and configure per the screenshot below - set your transcoding profile to `vaapi-renderD128`.

![](/images/stremio-server-setup-1.png)

Now play your media as normal - you may see a longer-than-usual delay when a stream starts - this is due to the server caching the content before streaming starts.

{% include 'stremio_server_faq.md' %}
{% include 'app_footer.md' %}

[^1]: Other than an entrypoint change to enforce waiting for a VPN to be established before running the server!
