---
title: Elf Hosted Joplin Server 🧝 from $0.05/day
slug: Joplin-server
description: Joplin is an open source note-taking app. Capture your thoughts and securely access them from any device
upstream: https://joplinapp.org/
links:
- name: GitHub
  uri: https://github.com/laurent22/joplin
sponsorship: 
- name: Buy me a coffee
  uri: https://www.buymeacoffee.com/etechonomy
---

# {{ page.meta.slug }}

[Joplin](https://joplinapp.org/) is a 100% open-source , markdown-driven note-taking app, similar to [Obsidian](https://obsidian.md/) or [Logseq](https://logseq.com/). There are [apps](https://joplinapp.org/) for Mac, Windows, and Linux, even a terminal app!

{% include 'app.md' %}

Joplin Server is the open-source version of the sync engine behind https://joplincloud.com, which takes you beyond simple apps, by enabling cross-device sync, sharing, publishing, etc.

Adding Joplin Server to your "Elf Stack" will let you utilize your ElfStorage (*pass go, collect 100GB*) for storing notes, attachments, etc.

The "publish note" feature is pretty - [here's an example](https://funkypenguin-joplin-server.elfhosted.com/shares/6m2JjKW5zUqtZrWNMj1lNI) of what a published note looks like - it's published by joplin-server (*so you can edit it with any client on any device*), and it's auto-updated whenever the note is updated.

If you don't trust a seedy seedbox host with your super secret notes (*and why should you?*), you can enable E2E encryption in the client apps, which (*like [Seafile][seafile]*) means that all that's stored in ElfStorage is the encrypted blobs, and some metadata in the postgresql database.

{% include 'app_access.md' %}

### What's my password?

The default username `admin@localhost`, and the password is `admin` (*change this after logging in, obviously!*).

If you change your email address (*and you should*), Joplin will try to send you an email to verify your address. Email doesn't work (*Joplin Server is a "at home" version of the paid JoplinCloud service*) so click on Admin -> Email, examine the email queue, find your confirmation email, and click on the link yourself :)

{% include 'app_footer.md' %}