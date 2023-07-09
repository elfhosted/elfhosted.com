---
date: 2023-07-10
categories:
  - note
tags:
  - stripe
title: Business summary for Stripe
description: ElfHosted business model summed up in an email response to Stripe
---

# ElfHosted Business model

Shortly after receiving our first actual payment for services, Stripe got in touch and asked me to clarify how the business works, to ensure we're supportable under their [Restricted Businesses list](https://stripe.com/en-nz/legal/restricted-businesses)

I responded as below, and thought that this would be useful to blog, since it succintly summarizes my thoughts about how ElfHosted operates.

<!-- more -->

## Products / Services

Stripe:

> What products or services do you plan to sell through Stripe?

I'm selling app hosting services. Somewhere between IAAS and SAAS, I provide compute / orchestration / storage for popular opensource applications that a user would normally self-host. Examples of supported applications are [Mattermost][mattermost], [VaultWarden][vaultwarden], [Plex][plex], associated tooling, etc.


I differentiate myself from other hosting providers by offering users the chance to "BYO" storage - so they can attach their existing cloud storage (*S3, dropbox, etc*) to their hosted apps, or they can buy storage from me directly.

## Target audience

Stripe: 

> We'd like to learn about your typical customers. Who is your target audience?


My target user would be technically-savvy users who, while capable of running self-hosted apps at home, want to offload the infrastructure / maintenance to me, and just enjoy the other benefits of self-hosting. Which is why I called it "elfhosted" :)


Further, I'm building the platform "in public", open-sourcing much of the design and build process at https://geek-cookbook.funkypenguin.co.nz, with the intention of providing a reference build / training example to augment my existing published material.


## Details

Stripe:

> Specifically, could you provide details around products/inventory, pricing, shipping details, and customer-vetting processes, if applicable?

Not sure how to answer this, tell me if you need more information...

### Products 

I create helm charts per app, and products for these apps in a wordpress-powered store which fires a webhook when a user buys an app. The webhook produces a commit to a github repo which alters a user's helm deployment, resulting in a new pod deploying in their kubernetes namespace, and giving them access to the app via a SSO-protected ingress. At that point, the user configures and uses the app as they need.

### Inventory

The application containers are open-source and [publicly available](https://github.com/geek-cookbook/containers), my inventory constraint is the compute resources in the underlying Kubernetes cluster. When running "short" on resources, I horizontally scale the cluster by adding more compute / storage nodes to the cluster.

### Pricing

Pricing is primarily based on the resources consumed by the app. My floor price is $1 USD (*smaller amounts tend to fail due to transaction fees*), so most apps (*[VaultWarden][vaultwarden], for example*) are priced at $1/month. Apps which consume significantly more CPU are priced accordingly, the highest currently being $5/month.

### Shipping details

Since all the products are provided online, there is no shipping involved.

### Customer vetting

While I'm currently providing $0 services during a trial period in June 2023 using a coupon code, in order to use my services beyond an initial trial period, customers must (a) provide a verified email address, (b) a valid credit card, \(c), and pass the woocommerce anti-fraud checks.

Further, the design of the service (*bring your own storage, bring your own VPN*) dis-incentivizes bad actors who would just abuse a free trial period and then move on, since while the trial period may be free, the BYO resources necessary to make use of it are not, and must already have been purchased elsewhere. Further, customers cannot purchase services (*trial or otherwise*) before agreeing to our [TOS](/legal/terms-of-service/) and [AUP](/legal/acceptable-use/), and I'm quick to shut down any abusers.

### Summary

Hope this provides the necessary reassurance, happy to provide more details if necessary :)

--8<-- "common-links.md"

