---
title: sElfHosted Jellyfin Accounts 🪄 from $0.05/day
slug: jellyfin-accounts
description: jellyfin-accounts (JFA) is a better way to manage your Jellyfin users
upstream: https://jfa-go.com/
links:
- name: Discord
  uri: https://discord.com/invite/MrtvuQmyhP
- name: wiki
  uri: https://wiki.jfa-go.com/
---

# {{ page.meta.slug }}

jellyfin-accounts (JFA) is a better way to manage your Jellyfin users.

{% include 'app.md' %}

Features include:

* [x] Send invite links to your users, let them sign up themselves
* [x] Create setting profiles to restrict permissions of new users
* [x] Handles password resets without your intervention
* [x] Enforce sign-up requirements:
    * [x] Password strength
    * [x] Contact method verification
    * [x] CAPTCHA
* [x] Send messages & notifications to your users (email, discord, telegram, matrix available)
* [x] Set accounts to expire after a specified time
* [x] Manage your users in bulk
* [x] More

{% include 'app_access.md' %}

## How do I set it up?

Here's a series of screenshots to illustrate, but TL;DR, use the following settings:

### TL;DR 

* [x] **Disable** updates (*we roll these out for you anyway*)
* [x] When setting up connection to Jellyfin, use these settings:
    * [x] Server Address (Internal): `http://jellyfin:8096`
    * [x] Server Address (External): `https://<your username>.jfa.elfhosted.com`
* [x] If connecting to Ombi, use `http://ombi:5000` for connection

### Step-by-step 

Initial setup:

![Jellyfin Accounts - Starting Setup](/images/jfa-setup-1.png){ loading=lazy }

Pick language:

![Jellyfin Accounts - Starting Setup](/images/jfa-setup-2.png){ loading=lazy }

General setup:

![Jellyfin Accounts - General Setup](/images/jfa-setup-3.png){ loading=lazy }

Configure login:

![Jellyfin Accounts - Starting Setup](/images/jfa-setup-4.png){ loading=lazy }

Configure Jellyfin Integration.

* [x] When setting up connection to Jellyfin, use these settings:
    * [x] Server Address (Internal): `http://jellyfin:8096`
    * [x] Server Address (External): `https://<your username>.jfa.elfhosted.com`

It's recommended to create a dedicated Jellyfin user for JFA to use:

![Jellyfin Accounts - Jellyfin Setup](/images/jfa-setup-5.png){ loading=lazy }

Here's what the Jellyfin user setup looks like:

![Jellyfin - setup jfa-admin user](/images/jfa-setup-6.png){ loading=lazy }

If using [Ombi][ombi] integration, set Ombi to `ombi:5000`:

![Jellyfin Accounts - Ombi Setup](/images/jfa-setup-7.png){ loading=lazy }

Setup (optional) messaging support

![Jellyfin Accounts - Messaging Setup](/images/jfa-setup-8.png){ loading=lazy }

Setup password validation requirements:

![Jellyfin Accounts - Password Validation Setup](/images/jfa-setup-9.png){ loading=lazy }

Setup contact info

![Jellyfin Accounts - Contact Setup](/images/jfa-setup-10.png){ loading=lazy }

Done! :thumbsup:

![Jellyfin Accounts - Done!](/images/jfa-setup-11.png){ loading=lazy }

{% include 'app_footer.md' %}