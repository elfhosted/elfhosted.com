---
title: Install ElfHosted MediaFusion Stremio Addon (torrentio alternative)
slug: AIOStreams
description: MediaFusion (an alternative to torrentio stremio addon), is the most comprehensive and powerful of the Stremio Addons in 2024, especially popular for watching Tamil, Hindi, Malayalam, Kannada, English, and dubbed movies & series
upstream: https://mediafusion.elfhosted.com
links:
- name: GitHub Repo
  uri: https://github.com/mhdzumair/MediaFusion
---

# {{ page.meta.slug }}

AIOStreams is an "addon of addons", which uses your provider credentials and preferences to combine the results from multiple addons, parse / filter, and present them in a consistent format, according to your preferences.

!!! tip "Proxy streaming support for torrentio"
    Notably, AIOStreams can serve these combined addons through your [MediaFlow Proxy][mediaflow-proxy] instance, so that you'll be able to use the results with your debrid provider from multiple locations at once, while not risking an account ban, since your provider only sees the IP of your MediaFlow Proxy instance.

ElfHosted provides a public, community version of MediaFusion at https://aiostreams.elfhosted.com (*with individual and global rate-limits*), and per-user, private, un-rate-limited instances.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### Set SECRET_KEY

AIOStreams uses a secret key to encrypt the data you provide, so that you're not exposing base64-encoded API keys in the manifest URLs held by Stremio. This also protects your keys if you share your addon, since a user would need your ElfHosted SSO credentials in order to use the /configure page to examine them.

AIOStreams won't work without a `SECRET_KEY`, but we've set a secret default so that the app will work without configuration. Users who prefer to, can change their `SECRET_KEY` (and re-install the addon), by generating a 32-character key (*`openssl rand -base64 32` for example*), and then applying it to AIOStreams using [ElfBot][elfbot]:

```
elfbot env aiostreams SECRET_KEY=whateveryousetmakesureits32chars
```

### Integrate with MediaFusion

If you've got an ElfHosted [MediaFusion][mediafusion] instance, you'll have set your own `api_password`. AIOStreams needs that same password for optimal integration into the /configure page, so set it using:

```
elfbot env aiostreams MEDIAFUSION_API_PASSWORD=sameapipasswordyousetformediafusion
```


{% include 'app_footer.md' %}