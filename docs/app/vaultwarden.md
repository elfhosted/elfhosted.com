---
title: sElfHosted VaultWarden 🪄 from $0.05/day
slug: VaultWarden
description: Alternative implementation of the Bitwarden server API written in Rust and compatible with upstream Bitwarden clients
upstream: https://github.com/dani-garcia/vaultwarden
---

# {{ page.meta.slug }}

Alternative implementation of the Bitwarden server API written in Rust and compatible with upstream Bitwarden clients.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

### Is it backed up?

No. You can back it up yourself using [ElfBot][elfbot].

### Can you see my passwords?

No, your data is encrypted client-side. All we do is host the database. You can confirm this, by backing up your data, and examining it (see above).

### How do I enable the admin page?

Per the [upstream docs](https://github.com/dani-garcia/vaultwarden/wiki/Enabling-admin-page), you need to supply an `ADMIN_TOKEN` environment variable to VaultWarden.

It's an advanced / beta operation, but you can achieve this with [ElfBot][elfbot]! :robot:

{% include 'app_footer.md' %}