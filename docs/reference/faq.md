# FAQ

This page lists frequently asked questions about ElfHosted..

## General

### Can I get SSH access?

Our services run within a Kubernetes microservices-based environment, running on ephemeral containers, and there's no external access to the applications.

### Can I install more apps?

The currently available apps are listed at https://elfhosted.com (once you login). You can create a ticket / suggestion for additional apps in our Discord server.

### Can I use rclone?

[Minio](/Apps/Minio) exposes an S3 endpoint, which you can use with rclone from outside of our platform. We don't support running rclone from within your environment.

### Can I access my services without SSO?

If you need to access your services via apps / tooling externally, without Auth0 authentication, you can disable this on a per-app basis in your user portal, at https://elfhosted.com

> It's **your** responsibility to ensure that you've configured the app with appropriate credentials to be publically exposed to the internet.
{.is-warning}

### How do I restart my apps?

Use the same add/remove interface to trigger one-time restarts of your apps at https://elfhosted.com

## Torrents

### I can't connect to my tracker

It's possible that your tracker needs to be whitelisted to connect. Please open a ticket at our Discord (https://discord.elfhosted.com) for further processing. You also might be using a public tracker (eg, Kickasstorrents, RarBG, The Pirate Bay etc) in which you'll need to install the Deluge/Qbittorrent app that's for public trackers. 

### My torrents pause

In the event of Deluge crashing, the resuming torrents will be paused when the restart is completed. You can resolve this by defaulting the caching parameters by going to `ltconfig > (drop down) libtorrent default > load preset > then clicking apply. `

![deluge.png](/deluge.png)

## Usenet

### I can't connect my Arr apps to Deluge

Deluge requires the "Label" plugin for compatibilty with Arr. Enable this:

![deluge_webui_2.0.5_—_(private_browsing)_2022-05-14_20-07-16.png](/deluge_webui_2.0.5_—_(private_browsing)_2022-05-14_20-07-16.png)


## Streaming

### My playback is buffering

Check your speed at https://speed.elfhosted.com - you'll want at least 20Mbps for reliable playback at 1080p. Configure your streamer to "DirectPlay", rather than transcoding, for best results.





