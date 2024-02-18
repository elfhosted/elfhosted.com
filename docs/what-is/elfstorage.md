---
title: ElfStorage. Elastic local storage.
description: ElfStorage is ElfHosted's native storage, available if you'd prefer not to BYO
---

# ElfStorage

While we encourage users to BYO storage (*especially Hetzner [StorageBoxes][storagebox]*), ElfStorage exists to provide quick and easy storage for cases where you might not want to bolt-on external storage.

Every user gets 100Gi ElfStorage free, mounted at `/storage/elfstorage`. This is done to ensure a smooth user experience when using our pre-provisioned apps, which would not otherwise be possible with the BYO mounts.

## How to get more ElfStorage

You can buy more ElfStorage [in the store][store/elfstorage].

!!! warning "You can't shrink an ElfStorage volume"
    Due to how Kubernetes PVC expansion works, you can **expand** but you can never **shrink** your ElfStorage volume. If you buy 10TB and later decide you'd rather only have 2TB, we'd have to manually **destroy** the volume and create a new one.

## Technical specs

ElfStorage is provided by a ceph cluster running within our Hetzner environment. It's designed with reliability in mind, not performance, and shouldn't be expected to handle heavy I/O loads well.

* Nodes are 1Gbps
* Disks are HDD, with no DB/WAL journals
* We keep 2 copies of each object, with the failure domain set to an individual host, so we can lose one Ceph host without impacting data availability.

--8<-- "common-links.md"