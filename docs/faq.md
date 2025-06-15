# FAQ

This page lists frequently asked questions about ElfHosted.

## Store

### Can I get a trial?

Yes, almost all of our packages come with a $1, 7-day trial. Larger streaming bundles (Rangers+) do not, but users are able to trial a normal-sized bundle (*Hobbits, etc*), and upgrade to a larger bundle as required.

## General

### Can I get SSH access?

* Short answer: No, but you can use [ElfTerm][elfterm] for limited CLI commands like moves and unpacks
* Long answer: Our services run within a Kubernetes microservices-based environment, every app is a separate container, so there's nothing to SSH **into**.

### Can I use rclone?

Yes! See [how to use rclone](/how-to/use-rclone/).

## Apps

### Can I access my services without SSO?

Services with strong authentication or whose functionality requires access without SSO (*[Plex][plex], [Ombi][ombi], etc*) don't need to be protected by SSO.

Services which can't be categorically secured are protected by SSO to prevent abuse / accidental misconfiguration.

Due to the risk to all our customers if downloading apps are misconfigured and abused, these apps will are configured for SSO regardless of their own authentication layer. This may cause some 3rd-party mobile client apps to fail. In some cases, if API keys are rotate and recorded, we are able to "expose" individual apps using a separate purchase - see the "[Advanced](https://store.elfhosted.com/product-category/advanced/)" category in the store for details.

### How do I restart my apps?

Use [ElfBot][elfbot], or just delete the pod with [Kubernetes Dashboard][kubernetes-dashboard]!

### How do I backup my app config?

Use [ElfBot][elfbot]!

### How do I see app logs?

Some apps create logs in their `config/<app>/` folder, or `logs/<app>/`, which you can examine using [FileBrowser][filebrowser]. Alternately, you can watch each app's logs in realtime using [Kubernetes Dashboard][kubernetes-dashboard].

## Streaming

### My playback is buffering

Check your speed at https://speed.elfhosted.com - you'll want at least 20Mbps for reliable playback at 1080p. Configure your streamer to "DirectPlay", rather than transcoding, for best results.

Depending on the results of the speed test, you may want to [migrate your stack to a closer datacenter](/how-to/migrate-datacenters).

## Debrid

### Aren't you misusing RealDebrid?

RealDebrid has a "fair use" policy of ~2TB/day for residential users, and ~500GB/day for datacenters. [Zurg][zurg] supports multiple user-provided "backup tokens", allowing users to purchase multiple RD accounts in order to remain within RealDebrid's fair-use limits.

An ElfHosted user therefore gets 25% of the daily bandwidth allocation that a residential user gets, and consequently pays 400% more than a residential user for the same level of service.

--8<-- "common-links.md"