---
slug: Flaresolverr
upstream: https://github.com/FlareSolverr/FlareSolverr
works_with:
- Prowlarr
---

# {{ page.meta.slug }}

FlareSolverr is a proxy server to bypass Cloudflare protection commonly applied to indexers / trackers, so that they can be auto-queried by [Prowlarr][prowlarr].

{% include 'app.md' %}

## How do I use it?

Configure Flaresolverr as a proxy in [Prowlarr][prowlarr] under `Settings --> Indexers` as follows:

* name: `flaresolverr`
* tags: `flaresolverr`
* host: `http://flaresolverr:8191`

Then add the `flaresolverr` tag to any indexers requiring it.

{% include 'app_footer.md' %}
