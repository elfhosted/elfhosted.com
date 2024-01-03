---
title: 🧝 Hosted Wallabag 🦘 from $0.05/day
slug: Wallabag
description: Wallabag is an popular, open-source read-it-later app, like Instapaper or Pocket, but yours to control!
upstream: https://wallabag.org
links:
- name: subreddit
  uri: https://www.reddit.com/r/wallabag/
- name: GitHub Repo
  uri: https://github.com/wallabag/wallabag
price: 0.5
sponsorship:
- name: Liberapay
  uri: https://liberapay.com/wallabag
---

# {{ page.meta.slug }}

Wallabag is an popular, open-source read-it-later app, like Instapaper or Pocket, but yours to control!

{% include 'app.md' %}

wallabag extracts the article's content (*and only its content!*) and displays it in a comfortable view. Moreover, wallabag is responsive: you can read your articles on your smartphone or your tablet.

If you already have data on Pocket©, Readability©, Instapaper©, Pinboard©, Firefox or Chrome, you can import your data into wallabag: add easily thousands of articles in your account.

{% include 'app_access.md' %}

## How to get started

To log into Wallabag, use the default credentials (*username `wallabag`, password `wallabag`*). Once you've logged in, change your password

!!! warning "Change your password, there's no SSO"
    Because many of Wallabag's features require external access (*mobile apps, public sharing*), we don't secure it behind SSO, so take care to change your password ASAP, and ideally enable 2FA

## How to setup email

The docs describe [how to setup a mailer configuration](https://doc.wallabag.org/en/admin/mailer). In our case, you'll need to pass this `mailer_dsn` value as an environment variable, so you'll use `SYMFONY__ENV__MAILER_DSN`. 

Use [ElfBot][elfbot] to set this env var, by running (*for example*) `elfbot env wallabag SYMFONY__ENV__DOMAIN_NAME=smtp://user:pass@host:465`. This will trigger a restart of Wallabag, and upon the next start, the environment variable will be available.

{% include 'app_footer.md' %}