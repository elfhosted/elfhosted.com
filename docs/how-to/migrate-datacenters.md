---
title: Migrating between ElfHosted datacenters
description: Prefer a datacenter "closer to home", for improved latency / throughput? Here's a quick guide
---

# Migrating between ElfHosted datacenters

ElfHosted's default datacenter is located in the EU, which may not result in the best performance for users in other parts of the world.

We're expanding to other regions, and this guide will show you how to migrate your ElfHosted services between regions.

## What you need to know

1. Our hosting costs vary per-region, so there will be a variable charge based on which region you migrate to
2. Data migration is based on daily 24h offsite backups, so if you migrate 23h after your last backup, you'll loose the most recent 23h of changes
3. Your data persists on each individual cluster for 7 days. So if you migrate **back** to our default datacenter after 6 days, you'll "pick up where you left off" 6d ago, but if you migrate back after 8 days, you'll get your data restored  as of the last nightly backup.

## Process

1. Use https://speed.elfhosted.com to identify the ideal datacenter
2. Add the "[Elf-spedition](https://store.elfhosted.com/product/regional-relocation)" subscription to your account, picking the appropriate datacenter
3. Your apps will be turned off on the primary cluster, and created on the target cluster - this may take 10-15 minutes, depending on the volume of data restored from offsite backup
4. Your apps will run from the new cluster, with a new domain suffix! (*i.e., instead of `https://batman.elfhosted.com`, you might be `https://batman.elfhosted.us`*)

## FAQ

### Can I un-migrate?

Yes, cancel your subscription within 7 days to roll back to the original datacenter, where your volumes persist for 7 days. If it’s been more than 7 days, your volumes will have been cleaned up, and you’ll either get the latest cloud backup, or a fresh installation.

--8<-- "common-links.md"