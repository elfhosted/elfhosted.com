---
date: 2023-09-28
categories:
  - CHANGELOG
tags:
  - notifiarr
title: Notifiarr client now actually works!
description: Our notifiarr client suffered from an authentication misconfiguration, this is now fixed, so you can enjoy gloriously geeky notifications!
---
# Notifiarr notifies again!

Today we found a bug which has existed since our code was originally Seedplicity, which prevented the Notifiarr client UI from properly authenticating you, a necessary step towards configuring notifications for local services such as [Radarr][radarr], [Jellyfin][jellyfin], etc.

If you're unfamiliar with [Notifiarr][notifiarr], it's worth a look - check this out:

![](/images/notifiarr-sept-2023.png)

<!-- more -->

## How does Notifiarr work? 🙋‍♂️

[Notifiarr](https://notifiarr.wiki/) itself is a free(mium) service which consolidates notifications from a multitude of services, both online and self-hosted. For example, you can receive notifications to new subreddit posts matching a particular string, or notifications when your Radarr instance has downloaded a new movie. 

For integration with local services, we offer the [Notifiarr client][notifiarr], which runs locally, and interrogates your ElfHosted services in order to provide rich notifications.

## How do I get notified? 🤷‍♂️

That's the thing.. as far as I can tell, notifications can only be sent to a Discord channel. This means you need your own Discord server, and you'll need to setup some webhooks. Maybe there are other ways to receive notifications, but I'm unaware of them.

## Is your StorageBox slow? 🐢

On another topic, if you've noticed your ElfHosted apps being slow to access your mounted [Hetzner storagebox][storagebox], ensure that your storagebox is in the Falkenstein datacenter, where our infrastructure is located. You'll still be able to access storageboxes in other regions (*just like you can mount any cloud storage supportetd by rclone*), but the added latency will make disk operations (*like Plex library scanning*) **much** slower than if your storagebox was in Falkenstien.

Out of interest, here's what [Hetzner's datacenters](https://www.hetzner.com/unternehmen/360-tour) look like. You have to appreciate that they picked the cafeteria as one of the highlights for their virtual tour!

### Summary

As always, thanks for building with us!

--8<-- "common-links.md"