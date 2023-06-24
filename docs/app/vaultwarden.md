---
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

No. You can back it up yourself from `/config/vaultwarden` using [FileBrowser](/Apps/FileBrowser)

### Can you see my passwords?

No, your data is encrypted client-side. All we do is host the database. You can confirm this, by backing up your data, and examining it (see above).

{% include 'app_footer.md' %}