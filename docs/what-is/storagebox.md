---
title: Attaching a Hetzner Storage Box
description: Hetzner Storage Boxes are ideal for BYO storage for your ElfHosted apps
---

# Hetzner Storage Box

Hetzner offer affordable storage in "[Storage Boxes](https://www.hetzner.com/storage/storage-box)", in 1TB, 5TB, 10TB, and 20TB sizes. Here's why these are ideal for a BYO storage solution:

## Advantages

### Proximity

If your Storage Box is in the Hetzner Falkenstein datacenter, you'll get the best possibly latency and throughput from your ElfHosted apps.

### Externally accessible

You can transfer data in/out of your Storage Box without touching any ElfHosted infrastructure. This means that:

1. You are not subject to our rate-limits, resource constraints, etc when transferring data in / out
2. You can transfer data in / out of your Storage Box using rclone from other providers (*a migration strategy*)
3. You own your data. If ElfHosted's infrastructure or business fails, your access to your data is unaffected

### Exposed via SMB

Technically, Storage boxes can be accessed via SMB, making them an efficient and reliable way to attach storage to your apps, using [csi-driver-smb](https://github.com/kubernetes-csi/csi-driver-smb) in kernel-space, rather than rclone mounting, which runs (*less efficiently*) in user-space.

## How to attach a Storage Box

Use the [self-service rclone setup][rclone] to attach your storagebox using WebDAV, just like any other rclone-compatible storage provider.

--8<-- "common-links.md"