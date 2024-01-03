---
title: Go backstage with Kubernetes Dashboard on ElfHosted! 🧝
slug: Kubernetes-Dashboard
description: Get a glimpse into the infrastructure running your ElfHosted apps, using own own private Kubernetes Dashboard!
upstream: https://github.com/kubernetes/dashboard
---

# Peek inside your ElfHosted with Kubernetes Dashboard

Behind the scenes, Elfhosted is run on Kubernetes, using a [GitOps design from Funky Penguin's Geek Cookbook](https://geek-cookbook.funkypenguin.co.nz/kubernetes/deployment/flux/design/).

Your ElfHosted account includes a limited instance of the Kubernetes Dashboard, which you can use to geek out over the technical details, check your apps' CPU / memory, or restart apps if you don't want to use [ElfBot][elfbot].

![Screenshot of {{ page.meta.slug }}](/images/screenshots/{{ page.meta.slug | lower }}.png){ loading=lazy }

{% include 'app_access.md' %}

## How do I use it?

### Logging in

The first time you open Kubernetes Dashboard, you'll be prompted for authentication details. Click "Skip" to continue with the pre-provisioned access which has been setup for you:

![Screenshot illustrating skipping authentication on first login](/images/kubernetes-dashboard-skip-auth.png){ loading=lazy }

### Searching

The amount of information presented can be overwhelming. If you're looking at a particular app, use the "search" field to narrow down the amount of data presented:

![Screenshot illustrating searching](/images/kubernetes-dashboard-search.png){ loading=lazy }

### Restarting apps

To restart an app, navigate to its current pod, and simply **delete** the pod. Kubernetes will recreate it, and the app will "restart" (*this is what ElfBot does*):

![Screenshot illustrating deleting a pod](/images/kubernetes-dashboard-delete-pod.png){ loading=lazy }

### Examining logs 

While apps **sometimes** create logs in `/config/<app name>` which are then visible in [FileBrowser][filebrowser], in some cases they don't, and in other cases there are multiple containers responsible for the running of a single app (*like a VPN attached to [Plex][plex]*).

You can examine the logs for a pod by clicking "Logs" on the "3 dots" icon:

![Screenshot illustrating deleting a pod](/images/kubernetes-dashboard-pod-logs.png){ loading=lazy }

Once viewing the logs, you can adjust which **container** in the **pod** you want to see the logs for:

![Screenshot illustrating deleting a pod](/images/kubernetes-dashboard-app-logs-per-container.png){ loading=lazy }

### Can I break stuff?

No, the dashboard only provides necessary read access to your own namespace, plus the permission to delete pods (*which will always be recreated*).

### This is awesome!

Isn't it? If you want to learn more about Kubernetes, here's a [good place to start](https://geek-cookbook.funkypenguin.co.nz)!