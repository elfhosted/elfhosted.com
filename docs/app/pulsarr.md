---
title: Elf Hosted Pulsarr 🧝
slug: Pulsarr
description: Instantly sync Plex watchlists with Radarr / Sonarr
upstream: https://github.com/jamcalli/Pulsarr
links:
- name: GitHub
  uri: https://github.com/jamcalli/Pulsarr
sponsorship:
- name: Ko-Fi
  uri: https://ko-fi.com/jamcalli
works_with:
- Plex
- Radarr
- Sonarr
---

# {{ page.meta.slug }}

Pulsarr is an integration tool that bridges Plex watchlists with Sonarr and Radarr, enabling real-time media monitoring and automated content acquisition all from within the Plex App itself.

!!! tip "Pulsarr gets revenue sharing! :heart:"
    Pulsarr is an "[Elf-illiated](https://store.elfhosted.com/affiliate/)" app - the developer is active in our [Discord][discord] community (*in the [#elf-pulsarr](https://discord.com/channels/396055506072109067/1352022384722575420) channel*), the app itself is tuned to work perfectly with ElfHosted "out-of-the-box", and 33% of your subscriptions are contributed to the developer!

{% include 'app.md' %}

Enjoy all the benefits of other content discovery systems without requiring users to use additional services. All the magic happens from the pimary users Plex Token.

It provides user-based watchlist synchronization for yourself and for friends, smart content routing based on genre, and notification capabilities (Discord and Email).

{% include 'app_access.md' %}

## How do I use Pulsarr

### Initial setup

#### Setup account

When you first log into Pulsarr, you're prompted to setup your account. This protects your instance from public tampering, and as such, there's no further SSO required to access Pulsarr.

![](/images/pulsarr-1.png)

#### Add Plex Token

You'll need a Plex token for Pulsarr to use to interact with Plex. Re-use an existing one, or (better) create a 
new one using our [token generator][plex-token].

![](/images/pulsarr-2.png)

### Setup Aars

Your 4K Radarr and Sonarr URLs and API keys are pre-configured, but you'll need to manually set your quality profiles, and save the changes.

![](/images/pulsarr-3.png)

#### Multiple Aars

By default, ElfHosted HD Aars are configured to import from the 4K Aars, but this process is not immediate, it relies on a scheduled job within the Aarr.

Pulsarr is able to send watchlisted items to multiple Aars simultaneously, bypassing Aar-to-Arr import delay.

If you want to populate multiple Radarrs / Sonarrs, you'll need to enter the **HD** Aars' details as follows:

* Radarr: `http://radarr:7878`
* Sonarr: `http://sonarr:8989`

Get your API keys from the respective Aar, under `Settings` -> `General`

Nominate one of the Aars to be the primary, and then configure it to sync with the other one.

![](/images/pulsarr-5.png)

### Start workflow

Pulsarr doesn't **start** doing anything by default. From the main dashboard, enable the option to auto-start, and then start the workflow.

![](/images/pulsarr-4.png)

### Troubleshooting

To watch what Pulsarr is doing, use [Kubernetes Dashboard][kubernetes-dashboard] to watch the logs of the Pulsarr pod.

{% include 'app_footer.md' %}