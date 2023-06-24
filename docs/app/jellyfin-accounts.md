---
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

* Send invite links to your users, let them sign up themselves
* Create setting profiles to restrict permissions of new users
* Handles password resets without your intervention
* Enforce sign-up requirements:
  * Password strength
  * Contact method verification
  * CAPTCHA
* Send messages & notifications to your users (email, discord, telegram, matrix available)
* Set accounts to expire after a specified time
* Manage your users in bulk
* More

{% include 'app_access.md' %}
{% include 'app_footer.md' %}