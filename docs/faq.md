# FAQ

This page lists frequently asked questions about ElfHosted.

## Store

### Can I get a trial?

Sort of. Every new user gets $1 "[ElfBuckz][elfbuckz]" to spend on apps. Provided you have a positive ElfBuckz balance, you can trial apps, or subscribe daily. ElfBuckz can be topped up either manually or on a monthly subscription.

### Why are there two prices for each app?

Each app can be purchased either as a once-off, expiring after 24h, or on an ongoing, daily basis. This allows you to "trial" an app without the hassle of subscribing, and then cancelling.

### Why are some apps priced higher than others?

Apps are priced based on their resource consumption. "Heavier" apps consume more resources, and are priced accordingly.

### How do I swap an app?

View the bundled apps in [your subscription](https://store.elfhosted.com/my-account/subscriptions/). Remove any apps you don't want, and add new apps you **do** want. Changes are effected immediately.

## General

### Can I get SSH access?

* Short answer: No, but you can use [FileBrowser][filebrowser]'s console for limited CLI commands like moves and unpacks
* Long answer: Our services run within a Kubernetes microservices-based environment, every app is a separate container, so there's nothing to SSH **into**.

### Can I use rclone?

Yes! We use rclone extensively for our "BYOS" design. If you need long-term, permanent rclone mount, then buy a compatible storage mount from the store, and we'll can mount it to `/storage`. 

If you just need temporary / occasional rclone move data around, then see [how to use rclone][/how-to/use-rclone/].

## Apps

### Can I access my services without SSO?

Services with strong authentication or whose functionality requires access without SSO (*[Plex][plex], [Ombi][ombi], etc*) don't need to be protected by SSO. 

Services which can't be categorically secured are proteced by SSO to prevent abuse / accidental misconfiguration.

Due to the risk to all our customers if downloading apps are misconfigured and abused, these apps will are configured for SSO regardless of their own authentication layer. This may cause some 3rd-party mobile client apps to fail. We may one day be able to provide header-based authentication on a per-apps basis, get in touch!

### How do I restart my apps?

Use [ElfBot][elfbot]!

### How do I backup my app config?

Use [ElfBot][elfbot]!

## Streaming

### My playback is buffering

Check your speed at https://speed.elfhosted.com - you'll want at least 20Mbps for reliable playback at 1080p. Configure your streamer to "DirectPlay", rather than transcoding, for best results.

--8<-- "common-links.md"