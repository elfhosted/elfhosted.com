---
title: Elf Hosted GoToSocial
slug: GoToSocial
description: GoToSocial is a lightweight, secure, and private ActivityPub social network server, your gateway to the larger Fediverse
upstream: https://github.com/godver3/cli_debrid
links:
- name: GitHub
  uri: https://github.com/superseriousbusiness/gotosocial
- name: Docs
  uri: https://docs.gotosocial.org/en/latest/
sponsorship: 
- name: OpenCollective
  uri: https://opencollective.com/gotosocial
- name: LibrePay
  uri: https://liberapay.com/GoToSocial 
---

# {{ page.meta.slug }}

GoToSocial is a lightweight, secure, and private ActivityPub social network server, your gateway to the larger Fediverse.

With GoToSocial, you can keep in touch with your friends, post, read, and share images and articles. All without being tracked or advertised to!

{% include 'app.md' %}
{% include 'app_access.md' %}

## How to use GoToSocial

### Setup admin account

By default, GoToSocial includes no accounts. It's necessary to create an account for yourself, using the GoToSocial CLI shortcut on your ElfHosted apps dashboard.

#### Create account

Run a variation of the following to create your account:

```
gotosocial admin account create \
  --username=<your username> \
  --email=<your email address> \
  --password=<your password>
```

#### Promote account

Promote your account to an administrator:

```bash
gotosocial admin account promote --username <yourname>
```

#### Restart GoToSocial

Promotion of an account requires a restart of the GoToSocial binary to fully take effect, so from the GoToSocial CLI, run:

```bash
pkill gotosocial
```
### User Interface

Per the [official FAQ](https://docs.gotosocial.org/en/latest/faq/): 

> GoToSocial is just a bare server for the most part and is designed to be used thru external applications. [Pinafore](https://pinafore.social/) in the browser, [Tusky](https://tusky.app/) for Android and [Feditext](https://github.com/feditext/feditext) for iOS, iPadOS and macOS are the best-supported.
> 
> Anything that supports the Mastodon API should work, other than the features GoToSocial doesn't yet have. Permalinks and profile pages are served directly through GoToSocial as well as the settings panel, but most interaction goes through the apps.

### Configure profile / instance

Your profile and instance settings are available at `https://<your gotosocial url>/settings/`

### Backup / Export

Your GoToSocial data is stored in `config/gotosocial`, and can be backed up either by copying the `config.yaml` and the `*.db*` files manually, or running `elfbot backup gotosocial` using [ElfBot][elfbot].

Assuming you used a custom domain name, then migrating your instance to another, non-ElfHosted GoToSocial installation is as simple as dropping the config and databases into the new instance, redirecting your DNS, and starting it up.

### Use a custom domain

If you don't want to use the ElfHosted domain name, you can BYO domain and point it to your ElfHosted GoToSocial account.

Assuming your ElfHosted username is `batman`, and you have your own domain, `awesomeburger.com`, and you want `social.awesomburger.com` to point to your ElfHosted GoToSocial instance.

Create an A record on your domain, pointing `social.awesomeburger.com` to `batman-gotosocial.elfhosted.com`.

Purchase the [custom domain addon](https://store.elfhosted.com/product/gotosocial-custom-domain-addon/), and set the CNAME to `social.awesomeburger.com`.

Upon purchase, a LetsEncrypt certificate will be generated for your custom domain, and the necessary additional routes added to our loadbalancer.

It's now necessary to edit your GoToSocial `config.yaml`, and to update the `host` value to match your new domain. You'll also need to reinitialized GoToSocial after making a domain change, so delete any `*.db.*` files in `config/gotosocial`, and then restart GoToSocial with [ElfBot][elfbot], using `elfbot restart gotosocial`


{% include 'app_footer.md' %}