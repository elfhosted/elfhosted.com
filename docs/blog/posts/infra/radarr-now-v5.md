---
date: 2023-10-26
categories:
  - CHANGELOG
tags:
  - radarr
title: Radarr bumped to v5
description: Radarr's at v5 now, and we have headroom for temp space!
---
# Radarr's at v5 now!

It turned out that due to changes in Radarr v4 compared to v5, our image wasn't passing testing, and so we didn't get the juicy new [v5.0.3.8127 release](https://github.com/Radarr/Radarr/releases/tag/v5.0.3.8127) a few weeks ago.

I was under the impression that v5 would support multiple resolutions for content, meaning a separate Radarr4K wouldn't be required anymore, but in the brief testing I've done so far, I've not been able to work out how to do this!

Anybody know how this works?

<!-- more -->

## Temp space headroom expanded

Our NZB download clients (*[NZBGet][nzbget] and [SABnzbd][sabnzbd]*) are configured for 200GB of NVMe-backed ephemeral `/tmp` space, to perform unpacking and repairs, before the content is moved to permanent storage. 

Since this `/tmp` directory is provided as a Kubernetes emptyDir, it appears to the download client as if it has all the available space on the base node available, but in reality, if a single pod consumes more than 200GB, it'll be restarted and the contents of `/tmp` will be lost (*the clients are configured to pause downloading while unpacking/moving to prevent this happening*).

Recently on one node, we've started seeing some clients pausing themselves because too little temp space was available on the base node, in cases where a lot of the active NZB clients ended up on the same node.

I've just finished reinstalling the worker nodes using a RAID0 for the pod's temp data, rather than a RAID1 (*who cares about redundancy for ephemeral data?*), which should put to bed any issues re low temp space in the NZB clients.

### Summary

As always, thanks for building with us!

--8<-- "common-links.md"