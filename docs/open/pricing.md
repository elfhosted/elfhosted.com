---
title: ElfHosted Open Pricing - calculation and costs
description: Here's how our costs and pricing is calculated
---
# Pricing

This page describes both how our prices are calculated, and what the underlying costs are that we need to recover through our pricing.

At the highest level, our goal is to **recover hardware costs equivalent to resources consumed, and to realize 20% profit on costs** (*see how we're going on this goal by examining our [monthly reports](/open)!*)

This page is intended to be referenced when making pricing adjustments in line with the stated goal above, and to provide clarity and transparency on how prices are calculated.

## How is pricing calculated

We use [kubecost](https://www.kubecost.com/), an open-source analysis tool for managing cloud/on-prem infrastructure costs, to monitor tenant pods in the cluster, and generate reports like this:

![](/images/kubecost-example-stats.png)

The data above represents Plex instances, sorted by 'efficiency'. The CPU and RAM prices are based on actual hardware costs, and the 'shared' cost represents a proportionate percentage of our overheads allocated to each pod (*so a pod with more resources contributes more towards shared resources than a very lightweight pod*).

The efficiency score indicates how much of the requested CPU/RAM was actually used during the period - on an well-tuned app like Plex, most instances are using on average less than what they're requested.

Per-app pricing is calculated roughly as follows (*based on the example above*):

1. Calculate average efficiency of the top 10% of pods over a sampling period (65%), and apply that to the calculated total cost ($0.62), to determine a "fair" rate, rounded up to the nearest 5 to make the math easy (\$0.40)
2. Where app-specific overheads apply (*10Gbit nodes used for Real-Debrid/Zurg streaming, for example*), add a proportionate cost (*$0.10 in the case of high-bandwith apps*)
3. Add 20% markup (*$0.50 + 20% = $0.60*)

So on the basis of the analysis and pricing above, Plex instances are priced at **$0.60/day**.

## What does it cost to run ElfHosted?

### Compute

Here's a month's summary of Hetzner hardware costs (the full invoice can be viewed [here](/assets/hetzner_example_invoice_elfhosted_redacted.pdf)):

![](/images/pricing-hetzner-example-total.png)

Here's a breakdown of the various hardware components / roles:

#### Fairies

!!! note "Hardware Specs"
    Hetzner Auction server (i9-9900K 128GB nodes, 2 x 1TB NVMEs)

The fairies are our HA Kubernetes control plane. We need 3 of them to provide HA and redundancy.

#### Elves

!!! note "Hardware Specs"
    Hetzner Auction server (i9-9900K 128GB nodes, 2 x 1TB NVMEs)

The elves are the workers - they run most tenant workloads, and we take advantage of the i9-9900K's QuickSync for Video (QSV) support for hardware transcoding from [Plex][plex], [Jellyfin][jellyfin], [Emby][emby], and Stremio. Typically the most contended resource on the elves is RAM (*you can't overprovision it!*), so we generally run out of usable RAM before we run out of CPU.

#### Gnomes

!!! note "Hardware Specs"
    Hetzner Auction server (i7-7700 64GB nodes, 2 x 500GB NVMEs)

Gnomes are lightweight nodes (*compared to fairies and elves*) which run observability workloads *(graphing, metric collection, and status health checks*). Since the elves can be heavily loaded at times, running observability on dedicated nodes makes their data more accurate.
  
#### Dwarves 

!!! note "Hardware Specs"
     Hetzner Auction servers (Xeon E3-1271 32GB nodes, 4 x 10TB HDDs)

Dwarves provide our HDD-based [ElfStorage][elfstorage] ceph volumes. We require a minimum of 10 nodes for our chosen [erasure coding](https://docs.ceph.com/en/latest/rados/operations/erasure-code/) profile (8+2). Their primary resource for exhaustion is available storage space (*RAM and CPU are fairly constant regardless of I/O load, since the HDDs themselves are the I/O bottleneck*).

#### Goblins

!!! note "Hardware Specs"
    [Hetzner AX41-NVMe](https://www.hetzner.com/dedicated-rootserver/ax41-nvme/) w/ 10Gbps, 128GB RAM, AMD Ryzen 5 3600 6-Core Processor, 2 x 500GB NVMe, 2 x 2TB NVMe

The goblins are the most expensive hardware whose resources we don't sell on a per-unit basis. They provide a 10Gbps, NVMe-backed ceph block/fs store which supports the config / data / database volumes of our our apps. 

The database / metadata for all apps are supplied by the goblins, and costs are apportioned per-app using the "shared" calculation provided by kubecost.

#### Giants 

!!! note "Hardware Specs"
    Hetzner AX41 w/ 10Gbps, 64GB RAM

Giants' defining trait are their 10Gbps NICs. Hetzner allow us unlimited 10Gbps ingress on these nodes, but meter egress after 20TB/month. The Giants run workloads which primarily **receive** data ([Zurg][zurg], [NZBGet][nzbget], [SABNZbd][sabnzbd]), and serve it to apps running on the elves (*1Gbps, unlimited*), which transcode / store / stream it as necessary. 

The giants were introduced to the design to prevent network i/o starvation as users stream content from remote sources like Real-Debrid, Google Drive, etc.

### Other

Aside from compute hardware, ElfHosted has the following monthly overheads:

Project | Why | Monthly Cost
---------|----------| ------
Store | Our store is hosted with Wordpress/Woocommerce-specialized hosts, Rocket.net | $30
Analytics | Plausible.io provides privacy-respecting metrics, for [elfhosted.com](/open/traffic/elfhosted.com/) and [store.elfhosted.com](/open/traffic/store.elfhosted.com/) | $20 
CI | A dedicated CI cluster is established to provide CI validation before significant changes are made in production | $100
Web Hosting | This website (https://elfhosted.com) is hosted on a paid Netlify plan | $10
Open Source Sponsorships | We [support the open-source devs](/open/sponsorship/) whose work underpins our platform | $35

--8<-- "common-links.md"