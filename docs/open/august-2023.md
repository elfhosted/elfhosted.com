---
title: Elf-Disclosure / Aug 2023
description: Recent changes, stats, and plans for ElfHosted from Aug 2023
---

# "Elf-Disclosure" for Aug 2023

We've been in "prod" for a month now, August was spent focusing on stability and efficiency, as well as slow maturation of some of our features.

Here are some shiny stats for Aug 2023, followed by a summary of some of the bigger changes announced this month in the [blog](/blog/)...

<!-- more -->

## Stats

=== ":moneybag: Spent"

    :material-target: Focus | :material-calendar: June 2023 | :material-calendar: July 2023 | :material-calendar: Aug 2023 
    ---------|----------|----------|---------- 
    :material-cow: Cluster | $428 | $428 | $428 
    :material-cart: Store | $632 [^1] | $223 | $100
    :material-test-tube: CI | $208 | $200 | $600
    :material-cloud-cog: Cloud | $30 | $20  | $20
    :material-clock: Development | 146h / $21,900 | 124h / $18,600 | 60h / $12,000 [^2] 
    :material-trending-down: Total Expenses | $23,198 | $19,471 | $13,148
    :material-trending-up: Income | $0 | $43 | $215
    :material-calculator: % of expenses | 0% | 0.2% | 1.63%
        

=== ":nerd: Tech stats"

    :material-target: Focus | :material-calendar: June 2023 | :material-calendar: July 2023 | :material-calendar: Aug 2023 
    ---------|----------|----------|---------- 
    :fontawesome-regular-circle-user: Subscribers | 14 | 48 | 53
    :octicons-sign-in-16: Ingress | 24TB | 19.5TB | 23TB
    :octicons-sign-out-16: Egress | 1TB | 3.3TB | 7TB
    :material-dolphin: Pods | 478 | 619 | 792

=== ":bar_chart: Summary"

    :material-target: Focus | :material-calendar: June 2023 | :material-calendar: June 2023 | :material-calendar: Aug 2023 
    ---------|----------|----------|---------- 
    :material-trending-down: Total invested thus far | $23,200 | $42,669 | $53,118 [^4]
    :material-trending-up: Total revenue | $0 | $43 | $258
    :material-calculator: Income % of total invested | 0% | 0.1% | 0.5%

## Resources

=== ":material-cpu-64-bit: CPU"

    Most apps consume almost no CPU while idle - the larger consumers are streamers doing transcoding, and download clients doing download/unpack operations:

    ![CPU stats for Aug 2023](/images/reports/2023-08/cluster-cpu-utilization.png)

    Last month (July 2023)'s for comparison:

    ![CPU stats for July 2023](/images/reports/2023-07/cluster-cpu-utilization.png)


=== ":material-memory: RAM"

    This graph represents memory usage across the entire cluster. By far the largest consumers of RAM is rook-ceph:

    ![Memory stats for Aug 2023](/images/reports/2023-08/cluster-memory-utilization.png)

    Last month (July 2023)'s for comparison:

    ![Memory stats for July 2023](/images/reports/2023-07/cluster-memory-utilization.png)

=== ":material-server-network: Network"

    I'm not sure these stats are accurate, they've likely overly high because pods on the host network (like metallb, ceph, etc) will end up counting **all** traffic on each host, rather than the pod itself. This is an outstanding issue to fix!

    ![Memory stats for Aug 2023](/images/reports/2023-08/cluster-network-utilization.png)

    Last month (July 2023)'s for comparison:

    ![Memory stats for July 2023](/images/reports/2023-07/cluster-network-utilization.png)

=== ":octicons-graph-16: Ingress/Egress"

    These are the traffic stats for egress from Hetzner. They exclude any traffic to/from Hetzner Storageboxes:

    ![Hetzner traffic stats for Aug 2023](/images/reports/2023-08/monthly_traffic_graph.png)

    Last month (July 2023)'s for comparison:

    ![Hetzner traffic stats for July 2023](/images/reports/2023-07/monthly_traffic_graph.png)

=== ":simple-ceph: Ceph"

    Ceph provides optional storage ("ElfStorage"), typically used for long-term slow storage and seeding. The following is a "moment-in-time" view of the ceph stats, future improvements will be providing dashboard with historical graphing.

    ![Ceph stats for Aug 2023](/images/reports/2023-08/ceph-cluster-stats.png)

## What's new?

### Implemented daily maintenance window

We re-established our 1h daily maintenance window, between 10h00-11h00 UTC. During this window, automated (*pre-tested*) app images updates are applied - if any of your apps are due an update, they'll be briefly unavailable as they restart. We avoid mass-restarts by relying on Flux's helmrelease controller default concurrency of 2, meaning we only reconcile updates for 2 users at-a-time.

The maintenance window doesn't mean that there will **always** be an impact during that period, simply that if an update **is** required, it'll be performed during this 1h window. A routine, predictable window means we can suppress Gatus (*your health tab*) email notifications during this period, as well as any internal alarming which would otherwise indicate issues.

### 10x more free ElfStorage, price reduced by 40%

Initial feedback was very helpful, indicating that (a) 10Gb free ElfStorage was effectively useless, and just confused users, and (b) $0.01/GB ($10/TB) was too expensive. After juggling some numbers and evaluating initial uptake rates and committed infrastructure, we increased the initial free ElfStorage allocation from 10Gb to 100Gb, and dropped the rate of ElfStorage to $6/TB (*minimum "chunk" to buy is 1TB*)

Selling ElfStorage by the TB instead of by the GB means it can now be included in a daily subscription alongside the rest of your apps, at $0.20/TB/day.

More details in [this blog post](/blog/2023/08/21/elfstorage-refactored/)

### Added "Elf-erral" program

We introduced a referral program, to promote organic growth. You'll get 10% for life of any ElfBuckz top-ups purchased your referees. See the "[Refer a friend](https://store.elfhosted.com/my-account/myreferrals/)" tab in your account in the store for your unique referral link.

More details in [this blog post](/blog/2023/08/09/elferral-program-is-a-go/)

### Dashboard stats for qbit, sabnzbd

If you're using [qBittorrent][qbittorrent] or [SABnzbd][sabnzbd], you'll now get more info appearing on your dashboard, indicating downloads in progress, speed, etc. Unfortunately these are not yet available for [Deluge][deluge], [ruTorrent][rutorrent], or [NZBGet][nzbget].

More details in [this blog post](/blog/2023/08/18/sabnzbd-qbittorrent-dashboard-stats/)

### Added bundles

To make it easier to compare ElfHosted's basic features with other Seedbox providers, we've added [discounted bundles](https://store.elfhosted.com/product-category/bundles/) to the store. A bundle gets you a combination of apps and storage, for slightly less than it would cost to assemble each component manually. The idea is that this give us a good starting position for comparative shoppers, and also makes possible future promotions, discounts, (*i.e., Black Friday specials*), etc.

!!! question "Why are there NZB bundles but not torrent bundles?"
    The torrent apps require you to BYO VPN, by entering credentials at checkout, and as such can't be bundled (*a platform limitation*)

### Expose your Arrs without SSO

NZB360 / Lunasea users have been asking how to access their apps **without** SSO, so that they can use their external, 3rd-party tools to manage them. This is now possible - we've implemented optional "[exposed](https://store.elfhosted.com/product-category/advanced/)" products which disables SSO for the respective app APIs, but keeps the existing dashboard integrations working nicely.

More details in [this blog post](/blog/2023/08/31/exposing-apis-without-sso/)
  


## Join us!

!!! tip "Want to get involved?"

    Want to get involved? Join us in [Discord][discord] and come and test-in-production!

[^1]: Much of this is yearly fees for Wordpress plugins
[^2]: Yes, that's a **lot**! This is the opportunity cost, over a month, of focusing on ElfHosted rather than billable consulting work!
[^3]: Total spend includes yearly payments for Wordpress plugins, etc
[^4]: All moneyz are in US dollarz!

--8<-- "common-links.md"