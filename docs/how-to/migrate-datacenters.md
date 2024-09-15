---
title: Migrating between ElfHosted datacenters
description: Prefer a datacenter "closer to home", for improved latency / throughput? Here's a quick guide
---

# Migrating between ElfHosted datacenters

ElfHosted's default datacenter is located in the EU, which may not result in the best performance for users in other parts of the world.

We're expanding to other regions, and this guide will show you how to migrate your ElfHosted services between regions.

!!! warning "elfhosted.cc is in BETA"

    The elfhosted.cc datacenter is considered “beta”. It’s been thoroughly tested by a small subset of users, who are currently using it without issue, but it’s possible that further issues will manifest with greater load.

    If you’re tolerant of a little downtime, and wanting to join in the fun on the “cutting edge”, then proceed, but come with a realistic expectation of availability and downtime. If in doubt, see the related [Discord thread](https://discord.com/channels/396055506072109067/1269247618983268382).


## What you need to know

1. Our hosting costs vary per-region. In order to maintain pricing parity across regions, resources may differ per-region (*for example, the US cluster has lower CPU limits but higher bandwith allocations*)
2. Data migration is based on daily 24h offsite backups, so if you migrate 23h after your last backup, you'll loose the most recent 23h of changes. To make a manual backup, run `elfbot backup offsite` from [ElfTerm][elfterm].
3. Your data persists on each individual cluster for 7 days. So if you migrate **back** to our default datacenter after 6 days, you'll "pick up where you left off" 6d ago, but if you migrate back after 8 days, you'll get your data restored as of the most recent daily backup.
What you should know

There are some discrepancies between the datacenters which you should be aware of, listed below.

### elfhosted.cc

Due to hardware constraints, in this environment, users get 50% of the CPU/RAM resources they'd get at elfhosted.com, but 200% of the bandwidth.

There is no ceph cluster, so your apps' data is stored on local volumes, with no redundancy. As is the case across all our datacenters though, data is backed up to offsite cloud storage daily (so in the event of a hardware failure, you risk loosing the last 24h changes). It's also possible to trigger a manual backup by running "elfbot backup offsite" from ElfTerm/FileBrowser.

## Process

1. (*optionally*) Force a manual backup, by running `elfbot backup offsite` from [ElfTerm][elfterm], and investigate any failures (*if you care about that particular app's data*)
1. Use https://speed.elfhosted.com to identify your ideal datacenter
2. Add the "[Elf-spedition](https://store.elfhosted.com/product/regional-relocation)" subscription to your account, picking the appropriate datacenter
3. Your apps will be turned off on the primary cluster, and created on the target cluster - this may take 10-15 minutes, depending on the volume of data restored from offsite backup
4. Your apps will run from the new cluster, with a new domain suffix! (*i.e., instead of `https://batman.elfhosted.com`, you might be `https://batman.elfhosted.cc`*)

## FAQ

### Can I un-migrate?

Yes, cancel your subscription within 7 days to roll back to the original datacenter, where your volumes persist for 7 days. If it’s been more than 7 days, your volumes will have been cleaned up, and you’ll either get the latest cloud backup, or a fresh installation.

--8<-- "common-links.md"