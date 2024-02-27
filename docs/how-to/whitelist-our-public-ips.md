---
title: Whitelisting ElfHosted's public IPs
description: Because we run apps in a Kubernetes cluster, each app (pod) may end up on a different node each time it runs, and thus have a different "public" IP from the perspective of egress traffic. Here's a list of possible IPs.
---
# How to whitelist ElfHosted's IPs

Because we run apps in a Kubernetes cluster, each app (pod) may end up on a different node each time it runs, and thus have a different "public" IP from the perspective of egress traffic.
 
If you are using external services which work on a per-IP whitelist, you may need a list of all possible IPs your ElfHosted apps may send requests from. The following is an list of the possible public IPs of your pods:

```
188.40.106.252
46.4.250.117
94.130.70.123
94.130.70.123
116.202.157.219
144.76.155.221
78.46.108.106
157.90.176.210
167.235.11.46
116.202.158.52
88.99.242.236
116.202.236.238
168.119.32.195
88.198.4.19
188.40.58.42
5.9.14.190
167.235.11.31
162.55.122.12
94.130.11.45
88.99.249.213
168.119.65.154
178.63.241.78
178.63.241.78
```

--8<-- "common-links.md"