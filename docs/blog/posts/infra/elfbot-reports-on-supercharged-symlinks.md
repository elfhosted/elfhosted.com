---
date: 2024-02-27
categories:
  - CHANGELOG
tags:
  - infrastructure
title: Symlinks get SSD supercharged, and ElfBot can report and delete broken symlinks
description: Symlinks are now "stored" on SSDs (less overall I/O load), and ElfBot can now report on your broken symlinks
---
# Symlinks get Supercharged

When we started using symlinks for real-debrid content, the natural place to store them was in `/storage/elfstorage`, since all users get 100GB free, so it's a consistent location. As we've increased in users, and users have increased their libraries sizes, I realized that this may be an inefficient way of "storing" the symlinks.

ElfStorage is backed by HDDs, and is using Ceph's [erasure coding](https://docs.ceph.com/en/latest/rados/operations/erasure-code/) at a profile of 8:2, meaning every object gets split into 8 checks, and distributed across our 10 ElfStorage "dwarf" nodes (*2 coding chunks*). This is great for 80GB movies (*10GB per node!*), but probably **not** great for tiny little symlinks, since it represents a lot of extra work for the ceph cluster!

To this end, I've added a `/storage/symlinks` folder for each user. Unlike `/storage/elfstorage`, this is backed by NVMes on our 10Gbit nodes, in a simple 2-replica configuration, so the actual load on the cluster resulting from storage to `/storage/symlinks` should be negligible.

Your old symlinks in `/storage/elfstorage` will continue to work, but ElfBot will new create all new symlinks into `/storage/symlinks`. Apps default configs will be updated for fresh installs, but you'll want to update your [Radarr][radarr] / [Sonarr][sonarr] root folders if you use them as part of your symlink setup.

# ElfBot reports on broken symlinks

Many users with large Real-Debrid collections have been noticing that their content occasionally "goes away". The symlinks remain, but the original sources in `/storage/realdebrid-zurg/__all__` (*for example*) are removed. We're not sure exactly **why** this happens to some content and not others, but to make it easier to manage, [ElfBot][elfbot] can now generate you a report of all broken symlinks.

To get your report, run `elfbot symlink report-broken`, and find the resulting report in `/storage/symlinks/report-broken.txt`.

!!! tip "Deleting broken symlinks"
    It's not implemented yet (*some apps legitimately use symlinks which appear to be broken upon scanning*), but we **could** also allow ElfBot to automatically delete broken symlinks. Watch this space!

### Summary

Thanks for geeking out with us, and please share these posts with related geeks!

--8<-- "common-links.md"