---
title: Using ElfTerm
description: Need to flex your geek-fu? Use the ElfTerm
---

# Enter the ElfTerm

!!! tip "ElfTerm is still growing"
    Did you find a new icon on your dashboard, and click to check it out? We're still building this, but this page will document available features as they roll out...

## Pod management

Your ElfTerm is integrated into your Kubernetes namespace. Try running `kubectl get pods` to see your running pods!

Here's a quick list of fun things you can do with `kubectl`

* `kubectl delete <pod>` (*restart your app*)
* `kubectl logs -f <pod>` (*watch the pod logs*)
* `kubectl top pods` (*see pod resource usage*)

## PlexTraktSync

Need to sync your [Plex][plex] library with Trakt? Use PlexTraktSync!

Run `plextraktsync sync`, plug in your Plex library details, and sync away!

--8<-- "common-links.md"