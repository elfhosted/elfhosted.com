# FAQ

This page lists frequently asked questions about ElfHosted.

## General

### Can I get SSH access?

Our services run within a Kubernetes microservices-based environment, running on ephemeral containers, and there's no external access to the applications.

### Can I install more apps?

You can subscribe to any app at https://dev.elfhosted.com, and you can exchange apps for others (cross-grade/upgrade)

### Can I use rclone?

Yes! We use rclone extensively for our "BYOS" design. If you need long-term, permanent rclone mount, then buy a compatible storage mount from the store, and we'll can mount it to `/storage`. 

If you just need temporary / occasional rclone, then purchase [RcloneBrowser][rclonebrowser].

### Can I access my services without SSO?

Currently not. We're working on making this optional.

> It's **your** responsibility to ensure that you've configured the app with appropriate credentials to be publically exposed to the internet.
{.is-warning}

### How do I restart my apps?

Use [ElfBot][elfbot]

## Usenet

### I can't connect my Arr apps to Deluge

Deluge requires the "Label" plugin for compatibilty with Arr, which is already enabled on our default Deluge config.

## Streaming

### My playback is buffering

Check your speed at https://speed.elfhosted.com - you'll want at least 20Mbps for reliable playback at 1080p. Configure your streamer to "DirectPlay", rather than transcoding, for best results.





