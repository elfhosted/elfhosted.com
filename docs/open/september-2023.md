---
title: Elf-Disclosure / September 2023
description: Recent changes, stats, and plans for ElfHosted from September 2023
---

# "Elf-Disclosure" for September 2023

We've been in prod for 2 months now, and September was mostly spent on bugfixes and strategic improvements,  which I'll detail below, although we did bring [Miniflux][miniflux], [Joplin][joplin-server] :simple-joplin:, and [Tdarr][tdarr] into the fold!

Here are some shiny stats for September 2023, followed by a summary of some of the bigger changes announced this month in the [blog](/blog/)...

<!-- more -->

## Resources

=== ":material-cpu-64-bit: CPU"

    Most apps consume almost no CPU while idle - the larger consumers are streamers doing transcoding, and download clients doing download/unpack operations. 
    
    Average CPU utilization (*although increased from 2% to 3%*) is largely unchanged from last month. Much of this is likely due to removal of deprovisioned / abandoned accounts.

    ![CPU stats for September 2023](/images/reports/2023-09/cluster-cpu-utilization.png)

    Last month (Aug 2023)'s for comparison:

    ![CPU stats for Aug 2023](/images/reports/2023-08/cluster-cpu-utilization.png)


=== ":material-memory: RAM"

    This graph represents memory usage across the entire cluster. By far the largest consumers of RAM is rook-ceph. Like CPU utilization, there appears to be no month-on-month growth this month, but this data was recorded **after** deprovisioned accounts were pruned, so it's likely that actual **used** RAM has increased.

    ![Memory stats for September 2023](/images/reports/2023-09/cluster-memory-utilization.png)

    Last month (Aug 2023)'s for comparison:

    ![Memory stats for Aug 2023](/images/reports/2023-08/cluster-memory-utilization.png)

=== ":material-server-network: Network"

    I'm not sure these stats are accurate, they've likely overly high because pods on the host network (*like metallb, ceph, etc*) will end up counting **all** traffic on each host, rather than the pod itself. This is an outstanding issue to fix!

    Combined with the ingress/egress graphs on the next page, and the almost doubling of Ceph storage usage, the graphs below indicate more regular network usage compared to the previous month.

    ![Memory stats for September 2023](/images/reports/2023-09/cluster-network-utilization.png)

    Last month (Aug 2023)'s for comparison:

    ![Memory stats for Aug 2023](/images/reports/2023-08/cluster-network-utilization.png)

=== ":octicons-graph-16: Ingress/Egress"

    These are the traffic stats for egress from Hetzner. They exclude any traffic to/from Hetzner Storageboxes.

    Network traffic increased ~50% from the previous period, and notably egress traffic increased 100%.

    ![Hetzner traffic stats for September 2023](/images/reports/2023-09/monthly_traffic_graph.png)

    Last month (Aug 2023)'s for comparison:

    ![Hetzner traffic stats for Aug 2023](/images/reports/2023-08/monthly_traffic_graph.png)

=== ":simple-ceph: Ceph"

    Ceph provides our own storage ("[ElfStorage][elfstorage]"), typically used for long-term slow storage and seeding. The warning status for this month is due to `1 clients failing to respond to cache pressure`, which may be due to torrent clients running directly against ElfStorage (*more investigation required, but note the increase in point-in-time IOPS and client throughput*)

    ![Ceph stats for September 2023](/images/reports/2023-09/ceph-cluster-stats.png)

    Last month (Aug 2023)'s for comparison:

    ![Ceph stats for Aug 2023](/images/reports/2023-08/ceph-cluster-stats.png)


## What's new?

### Custom domains

We can now offer custom domains for your ElfHosted services, so that instead of (*for example*) https://funkypenguin-uptime-kuma.elfhosted.com, you might prefer something like https://status.funkypenguin.co.nz (*see how it works?*)

More details in [this blog post](/blog/2023/09/29/custom-domain-support/).

### Plex over VPN

Plex recently sent [notices](https://torrentfreak.com/plex-will-block-media-servers-at-prevalent-hosting-company-230915/) to users hosted on Hetzner IP ranges, indicating that from 12 Oct 2023, their hosting provider will be blocked. 

We don't know exactly what'll happen from 12 Oct, but to mitigate this risk, we now offer [Plex with BYOVPN support](https://store.elfhosted.com/product/plex/), so you can plug your existing VPN provider credentials into Plex (*like we do with torrent clients*), and have Plex "phone home" over the VPN, hopefully avoiding the Hetzner IP block.

More details in [this blog post](/blog/2023/09/15/adding-byo-vpn-to-plex/).

### Tdarr

[Tdarr][tdarr] is a new app introduced this month, which will allow you to batch-transcode your media library for better compatibility with your devices, or for more efficient storage.

More details in [this blog post](/blog/2023/09/27/introducing-tdarr/).

### Joplin

A user-requested app, [Joplin Server][joplin-server] is the open-source version of the sync engine behind https://joplincloud.com, which takes you beyond simple apps, by enabling cross-device sync, sharing, publishing, etc.

![Screenshot of Joplin](/images/screenshots/joplin-server.png)

More details in [this blog post](/blog/2023/09/13/introducing-joplin-server/).

### Miniflux

Finally, my [favorite minimal RSS client][miniflux] is now an ElfHosted app (*and a good candidate for a custom domain*).

![Screenshot of Miniflux](/images/screenshots/miniflux.png)

More details in [this blog post](/blog/2023/09/06/introducing-miniflux/).

## Join us!

!!! tip "Want to get involved?"

    Want to get involved? Join us in [Discord][discord] and come and test-in-production!

--8<-- "common-links.md"