---
date: 2023-09-07
categories:
  - build-in-public
tags:
  - sso
title: Clarification on SSO protection
description: We've reviewed the SSO coverage of apps, and made some changes for consistency
---
# When is SSO provided?

I had feedback from a user today after a [recent post](/blog/2023/08/31/exposing-apis-without-sso/) about exposing various app APIs without SSO, pointing out that that SSO was applied a little inconsistently across our apps. For example, [Jellyseerr][jellyseerr] was exposed publically (*it has strong auth and is used to share media requests*), but [Overseerr][overseerr] (*of which Jellyseer is a fork*) was not! :facepalm:

This is now fixed :thumbsup:

To clarify, here's how SSO is applied, based on the intended audience / purpose of an app:

1. Apps that only you (*the user*) would use, are behind SSO without any native auth, where possible. This includes download clients, apps without auth ([openbooks][openbooks]), Arrs, etc (*although these can be [optionally exposed](/blog/2023/08/31/exposing-apis-without-sso/) to a limited degree*)
2. Apps which you might want to share ([Plex][plex], [Navidrome][navidrome], [Kavita][kavita], [Overseer][overseerr], etc) and which provide their own trusted auth, are exposed without SSO, since their entire purpose is to share media / content with a wider audience than just yourself!

<!-- more -->

### Summary

As always, thanks for building with us!

--8<-- "common-links.md"