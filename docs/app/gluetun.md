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

### Summary 

1. Add a [gluetun subscription](https://store.elfhosted.com/product/gluetun/) to your account
2. Use [Kubernetes Dashboard][kubernetes-dashboard] to create a ConfigMap named `gluetun-config`
3. Paste in the appropriate values for your VPN per the [gluetun wiki](https://github.com/qdm12/gluetun-wiki)
4. Watch your app pod restart in Kubernetes Dashboard, troubleshoot by examining the gluetun container logs in the pod
5. Make any required adjustments by re-editing the configmap. Go to step #4
6. All is working, success!

### Detail 

#### Creating the ConfigMap

From Kubernetes Dashboard, click the `+` icon to create a new resource:

![](/images/gluetun-configmap-1.png)

Copy the example YAML below, edit it to include only the values you need for your config, and paste it in:

!!! warning "No DNS names"
    gluetun doesn't support DNS names, so you can't use `myawesomevpn.gobblerof.pizza` as your custom VPN endpoint. You **must** use IP addresses (*not an issue unless you're doing a custom config*)

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: gluetun-config
data:
  VPN_SERVICE_PROVIDER: 'private internet access'
  VPN_TYPE: 
  VPN_ENDPOINT_IP: 
  VPN_ENDPOINT_PORT: 
  OPENVPN_USER: 'my pia username'
  OPENVPN_PASSWORD: 'my pia password'
  WIREGUARD_PUBLIC_KEY:
  WIREGUARD_PRIVATE_KEY:
  WIREGUARD_PRESHARED_KEY:
  WIREGUARD_ADDRESSES:
  SERVER_COUNTRIES:
  SERVER_CITIES:
  OPENVPN_CUSTOM_CONFIG:
  SERVER_REGIONS:
```

![](/images/gluetun-configmap-2.png)

#### Check logs

It's likely that things won't work perfectly, the first time. To debug, navigate to pods, find your Zurg pod, click the 3 dots, and pick `Logs`:

![](/images/gluetun-logs-1.png)

Click the `Logs from` dropdown...

![](/images/gluetun-logs-2.png)

.. and pick `gluetun`:

![](/images/gluetun-logs-3.png)

#### Editing ConfigMap

If you need to edit your ConfigMap once it's created, you can do so by finding it by navigating to `ConfigMaps`, clicking the 3 dots, and picking `Edit`:

![](/images/gluetun-configmap-3.png)

{% include 'app_footer.md' %}