---
title: Attach your existing VPN to your ElfHosted apps with gluetun
slug: Gluetun
description: ElfHosted provides simple Plex hosting - including hardware transcoding
works_with:
- Zurg
- RDTClient
upstream: https://github.com/qdm12/gluetun
sponsorship:
  - uri: https://github.com/sponsors/qdm12
    name: GitHub Sponsors
---

# {{ page.meta.slug }}

ElfHosted provides a "BYO VPN" to provide VPN connectivity to selected applications. Some apps (Zurg) require a VPN for external connectivity, and to facilitate this, we "bolt on" a gluetun instance, with the user's own VPN configuration.

[Add Gluetun to your ElfHosted stack! :magic_wand:](https://store.elfhosted.com/product/gluetun/){ .md-button .md-button--primary }

!!! tip "❤️ 30% of your subscription sponsors gluetun developer!"
    ElfHosted will contribute 30% of all revenue for Gluetun subscriptions to the [upstream developer](https://github.com/qdm12/gluetun), via [GitHub Sponsors](https://github.com/sponsors/qdm12).

## How do I use it?

1. Add a [gluetun subscription](https://store.elfhosted.com/product/gluetun/) to your account
2. Use [Kubernetes Dashboard][kubernetes-dashboard] to edit the ConfigMap named `gluetun-config`
3. Paste in the appropriate values for your VPN per the [gluetun wiki](https://github.com/qdm12/gluetun-wiki)
4. Watch your app pod restart in Kubernetes Dashboard, troubleshoot by examining the gluetun container logs in the pod
5. Make any required adjustments by re-editing the configmap. Go to step #4
6. All is working, success!

{% include 'app_footer.md' %}