# FAQ

This page lists frequently asked questions about ElfHosted.

## General

### Can I get SSH access?

* Short answer: No, but you can use [FileBrowser][filebrowser]'s console for limited CLI commands like moves and unpacks
* Long answer: Our services run within a Kubernetes microservices-based environment, every app is a separate container, so there's nothing to SSH **into**.

### Can I install more apps?

You can subscribe to any app in the [bundle][store/bundle], and you can exchange apps for others (*cross-grade/upgrade*).

### Can I use rclone?

Yes! We use rclone extensively for our "BYOS" design. If you need long-term, permanent rclone mount, then buy a compatible storage mount from the store, and we'll can mount it to `/storage`. 

If you just need temporary / occasional rclone move data around, then see [how to use rclone][/how-to/use-rclone/].

### Can I access my services without SSO?

Services with strong authentication or whose functionality requires access without SSO (*[Plex][plex], [Ombi][ombi], etc*) don't need to be protected by SSO. 

Services which can't be categorically secured are proteced by SSO to prevent abuse / accidental misconfiguration.

Due to the risk to all our customers if downloading apps are misconfigured and abused, these apps will are configured for SSO regardless of their own authentication layer. This may cause some 3rd-party mobile client apps to fail. We may one day be able to provide header-based authentication on a per-apps basis, get in touch!

### How do I restart my apps?

Use [ElfBot][elfbot]

## Usenet

### I can't connect my Arr apps to Deluge

Deluge requires the "Label" plugin for compatibilty with Arr, which is already enabled on our default Deluge config.

## Streaming

### My playback is buffering

Check your speed at https://speed.elfhosted.com - you'll want at least 20Mbps for reliable playback at 1080p. Configure your streamer to "DirectPlay", rather than transcoding, for best results.




