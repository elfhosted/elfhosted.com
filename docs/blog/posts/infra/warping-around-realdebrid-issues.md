---
date: 2024-06-17
categories:
  - infra
tags:
  - zurg
  - gluetun
title: WARPing around RealDebrid datacenter blocks, BYO VPN for security
description: Yesterday RealDebrid blocked Hetzner's IPv6 ranges from being able to download, and once again we were cut off. Necessity being the mother of invention, we now have a CloudFlare WARP VPN attached to all Zurg pods, as well as an option to BYO VPN for security / resilience.
---

# WARPing around RealDebrid blocks with VPNs

About 24h ago (*just as we ran a big [Riven][riven] rollout*), RealDebrid finally [closed the IPv6 loophole](https://www.reddit.com/r/debridmediamanager/comments/1dhe6u1/psa_file_is_not_available_error_in_zurg/) which was allowing us to Zurg with RealDebrid from datacenter IPv6 range.

We added a new product / process to allow us to connect your pods (*[Zurg][zurg], in this case*) to your own, existing VPN. On the plus side, it's extremely flexible, since gluetun supports a [huge range](https://github.com/qdm12/gluetun-wiki/tree/main/setup/providers) of VPN providers. On the downside, it requires some user geeky interaction, which I explain in this video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/Pa_jf9oy_SI?si=dlgnuTaX6KxlxtJa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

The solution works great, and several our of geekier elves validated it with Mullvad, Nord, ProtonVPN, and PIA. This was only a small subset of the affected users, and the process of VPN-ifying 100+ Zurg pods was looming unpleasantly...

And then our newest Elf-Venger, \@Mxrcy, pointed me a [container image for CloudFlare WARP](https://github.com/cmj2002/warp-docker), which can be used as a SOCKS5 proxy in Zurg 0.10, with zero manual config! After a bit more refactoring, we were able to reunite all users with their beloved  RD libraries via CloudFlare WARP! :couple_with_heart:

However...

<!-- more -->

Many users have opted to **remain** on the [gluetun][gluetun] solution, preferring the peace of mind it provides, over the unknown factors in the WARP design (*speed limits, potential congestion, etc*).

In the end, there are 2 paths forward:

1. Do nothing, and your Zurg will connect to RealDebrid via CloudFlare WARP, YMMV
2. Add your own VPN (*I like [PIA][pia]*) using [gluetun], getting your hands a little dirty creating a Kubernetes ConfigMap, and rest easy in the knowledge that your Zurg is routed through a platform for which you have some control!

## Riven has a UI (sort of)

We've all been enjoying geeking out on the [Riven][riven] backend logs, but now we also have a bare-bones frontend, which makes the process of managing your Riven config **soooo** much easier! It even uses Plex OAuth to retrieve your token, so that you don't have to go hunting in XML files anymore!

## Summary

Thanks for geeking out with us, and please share these posts with related geeks!

[^1]: I worked out why the numbers were so weird. Under some circumstances, when a subscription expires, the provisioning script wasn't properly removing deployments, and we ended up with "orphaned" pods still running in the cluster. I've applied a temporary, manual workaround, but will perma-fix this soon.

--8<-- "common-links.md"
