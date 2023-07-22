---
date: 2023-07-23
categories:
  - build-in-public
tags:
  - store
title: WebAuthn added for passwordless / biometric SSO
description: No longer do you have re-auth with your password for SSO - just use your fingerface!
---

# :material-fingerprint: Passwordless logins FTW

A few weeks ago, I started looking into integrating our store / SSO login with [OwnID](https://ownid.com/blog/why-you-should-adopt-passwordless-authentication-for-your-application/?domain_trace=ownid.com), to solve the fact that when your SSO session times out, you have to re-sign into the store (*also, in 2023, protecting all your services behind a simple password seems a little.. too little*)

The development got stuck behind decomissioning longhorn (*another long story, it didn't scale well!*), but after finally reproducing the prod store in dev for an accurate bug report to the OwnID team.. it worked perfectly :man_facepalming:

So... we now have passwordless / biometric logins for the store / SSO! :partying_face:

## How to go passwordless

Just log out and log in again. When you login, "[magic](https://en.wikipedia.org/wiki/WebAuthn)" will happen, and thereafter, you'll be able to login with your fingerprint / face / eyeballs etc.

## Should we enforce passwordless login?

Right now, the OwnID plugin just works **alongside** the default Wordpress login. We do have the option to remove the Wordpress login flow, and rely on OwnID only, which would make the solution overall more secure (*nobody can brute-force your account*). I'd like to gather some feedback over the next week on this idea, so jump into [Discord][discord] and let me know!

## Buy faster at the store

After some tinkering with the [Bitnami Wordpress helm chart](https://artifacthub.io/packages/helm/bitnami/wordpress) values, I was able to turn on the [W3 Total Cache plugin](https://wordpress.org/plugins/w3-total-cache/), which promises to improve page loads and responsiveness. I also turned on CloudFlare proxying for some extra speedz on those static assets.

TL;DR - the store should be faster to navigate, and stop 404ing under load! (*RAM usage has reduced by 50%, but that may just be a result of a restart*).

## Maintenance window worked

Our first maintenance window rolled by a few hours ago (*10h00 UTC to 11h00 UTC*), and it's likely that most of you pods were restarted, given there were lots of little changes queued up. Your health tab will show you whether any of your apps were restarted[^1], but it only checks every 5 min, so the restart may have been completely under-the-[radarr][radarr] (*haha*). 

We'll keep to a daily schedule for these updates - apps only restart if there's an upstream (*depends on the pace of upstream development*) or base image security update (*once or twice a month*), and they're typically back in < 1 min.

## Next Up

* [ ] Add a link on the store user account page to the app dashboard (*not done yet, but I've found out [how to do it](https://github.com/woocommerce/woocommerce/wiki/Customising-account-page-tabs)*)
* [ ] Send email to user with link to their dashboard (*enabled but needs testing*)
* [ ] Make checkout fields work better with browser auto-fill (*is this a Woocommerce/Wordpress issue?*)

Thanks for building with us - stay tuned!

[^1]: No emails were sent during the maintenance window though, which is what we wanted!

--8<-- "common-links.md"

