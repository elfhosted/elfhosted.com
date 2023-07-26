---
title: How to design a scalable app hosting platform on Kubernetes
description: This section provides a high level design description of how ElfHosted works
---

This section TBD, but I wanted to put a placeholder in to keep me accountable. 

TL;DR, this is all that's required for a user setup:

```yaml
apiVersion: helm.toolkit.fluxcd.io/v2beta1
kind: HelmRelease
metadata:
  name: myprecious-goldilocks
  namespace: aa-goldilocks
spec:
  chart:
    spec:
      chart: myprecious
      version: ">= 1.0.0"
      sourceRef:
        kind: HelmRepository
        name: elfhosted
        namespace: flux-system
  rollback:
    disableWait: false
    disableWaitForJobs: true
  install:
    disableWait: false
    disableWaitForJobs: true
  upgrade:
    disableWait: false
    disableWaitForJobs: true
  interval: 24h
  timeout: 30m
  releaseName: goldilocks
  values:
    userId: 3
    plex:
      enabled:
        true
    global:
      plex:
        enabled: true
```