# FAQ

This page lists frequently asked questions about ElfHosted.

## Store

### Can I get a trial?

No, but within 14 days, if you're legitimately unsatisfied with your purchase, and we haven't been able to resolve it for you, we'll refund you the balance of your subscription.

### How do you justify the cost?

Our pricing is explained in detail [here](/open/pricing/). 

Store purchases start at $9/month, which (*in New Zealand, anyway*) will get you 2 fancy coffees :coffee: or 1 fancy beer :beer:

Any store purchase carries with it the potential overhead of a support request, which costs our staff / volunteers their personal time and attention, and the base price reflects not only the infrastructure cost, but also product development / maintenance, and support overheads.

## General

### Can I get SSH access?

* Short answer: No, but you can use [ElfTerm][elfterm] for limited CLI commands like moves and unpacks
* Long answer: Our services run within a Kubernetes microservices-based environment, every app is a separate container, so there's nothing to SSH **into**.

### Can I use rclone?

Yes! We use rclone extensively for our "BYOS" design. If you need long-term, permanent rclone mount, then buy a compatible storage mount from the store, and we'll mount it to `/storage`. 

If you just need temporary / occasional rclone move data around, then see [how to use rclone](/how-to/use-rclone/).

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

Some apps create logs in their `config/<app>/` folder, which you can examine using [FileBrowser][filebrowser]. Alternately, you can watch each app's logs in realtime using [Kubernetes Dashboard][kubernetes-dashboard].

## Streaming

### My playback is buffering

Check your speed at https://speed.elfhosted.com - you'll want at least 20Mbps for reliable playback at 1080p. Configure your streamer to "DirectPlay", rather than transcoding, for best results.

## Debrid

### Aren't you misusing RealDebrid?

RealDebrid has a "fair use" policy of ~2TB/day for residential users, and ~500GB/day for datacenters. [Zurg][zurg] supports multiple user-provided "backup tokens", allowing users to purchase multiple RD accounts in order to remain within RealDebrid's fair-use limits.

An ElfHosted user therefore gets 25% of the daily bandwidth allocation that a residential user gets, and consequently pays 400% more than a residential user for the same level of service.

--8<-- "common-links.md"