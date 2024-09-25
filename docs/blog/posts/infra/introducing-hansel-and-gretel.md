---
date: 2024-09-23
categories:
  - infra
tags:
  - CHANGELOG
title: Introducing Hansel and Gretel
description: We've got new node types for contented / dedicated workloads
---

# Introducing Hansel and Gretel

The nodes in our first, primary datacenter (*in Germany*), have been classed as elves (*contended*), hobbits, and rangers (*dedicated*). We maintain enough hardware such that we can tolerate the loss of any one node type, and "fit" all the tenant workloads on the others. 

Until now, this has meant maintaining enough capacity for a spare elf, hobbit, and ranger. Since we're close to introducing halfling (*50% shared*) and nazgul (*100% dedicated*) nodes, and we don't want to have to maintain a whole 5 extra nodes for spare capacity, we're migrating the .com cluster to 2 new node classes...

<!-- more -->

![](/images/hansel-and-gretel.png)

Like the "yankee" nodes in the US cluster, our Germany-based node names will transition to "hansels" (*contended*) and "gretels" (*dedicated*). This will allow the "gretels" to be sliced up into hobbit-sized portions (*12.5% shared*), but to accommodate a mixture of hobbits, rangers, and halflings.

For example, you may have a hobbit, sharing a gretel node with 3 other hobbits and 2 rangers, or a ranger, sharing with another 2 rangers and 2 hobbits.

Resource allocations per-bundle remain the same, the advantage of the updated naming scheme (*for infrastructure geeks*), are:

1. Easier to identify which cluster a node belongs to, when examining pods across our growing collection of datacenters.
2. The only physical distinctions between our workload nodes is contention vs dedication, and hardware transcoding (*only on dedicated nodes*). Actual bandwidth / compute resource is handled at the bundle level, so there's no reason to have separate classes of node for each bundle type.

Also, the US cluster has been running on Ubuntu 24.04 LTS, and I'm taking this opportunity to upgrade our .com nodes from 22.04 to 24.04 at the same time (*longer lifespan!*)

The first few nodes went in during the most recent maintenance period, so if you look at your pods and discover they're running on a hansel / gretel node, this'll be why! There were a few hiccups (*maintenance took 37m longer than usual*), but all seems to be working as expected. If you encounter any issues post-maintenance, please create an [#elf-help][elf-help] ticket!

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 239 | -7
🐬 Tenant pods | 3481 | +295 [^1]
🐛 Bugz squished | - | -
🕹️ New toyz | - | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"

[^1]: We added a standalone "gatus" pod to make homer restarts more transparent, so 239 of these are just extra pods on existing subscriptions!
