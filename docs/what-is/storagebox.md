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

You can subscribe to a slot (A, B, or C) [in the store][store/storagebox]. Enter your storagebox credentials (*subaccounts also work*), and purchase. The storage will appear in `/storage/storagebox-<a/b/c>` within your apps.

Use the username provided with your storagebox, and reset the password if you don't already have one:

![](/images/storagebox-reset-password.png)

### Video guide

Here's an instructional video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/TJoOR140IJw?si=UK_E91kIozxBCqU9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Encryption (optional)

And here's how to add optional encryption to the storagebox mount:

<iframe width="560" height="315" src="https://www.youtube.com/embed/llPjWdHmF_k?si=yuZyMmmUJ8vbrC69" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

--8<-- "common-links.md"