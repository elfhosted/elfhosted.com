---
title: Elf Hosted Tdarr 🧝 from $0.15/day
slug: Tdarr
description: Tdarr will batch-transcode your media, for efficient storage and maximum-compatibility streaming
price: 0.15
upstream: https://docs.tdarr.io
links:
- name: GitHub
  uri: https://github.com/HaveAGitGat/Tdarr
- name: subreddit
  uri: https://www.reddit.com/r/tdarr/
- name: Discord
  uri: https://discord.gg/waKdfJR
---
# {{ page.meta.slug }}

Tdarr will batch-transcode your media, for efficient storage and maximum-compatibility streaming. Tdarr utilizes unused CPU / GPU capacity across our platform to perform batch transcodes, keeping your library lean and mean!

{% include 'app.md' %}
{% include 'app_access.md' %}

## How to use Tdarr

Tdarr is powerful and flexible, and can be intimidating to configure. Our instance is pre-configured to work as best as possible with our hardware / resources, but this section will detail some of the important configurations necessary.

### Worker setup

The following is required for the worker component of Tdarr:

#### Configure node

From the main Tdarr window, select the node, set 1 GPU transcode and 1 CPU healthcheck, and then click `Options` to add node-specific config:

![](/images/tdarr-node-setup-0.png)

#### Node options

Set the hardware encoding type to `vaapi`, allow the GPU worker to do CPU tasks, and set a low priority for FFMpeg/handbreak tasks:

![](/images/tdarr-node-setup-1.png)

#### Staging section 

Back on the main Tdarr page, under `Staging Section`, ensure that `Auto accept successful transcodes` is checked (*without this, the transcoded file will sit in `/transcodes` waiting manual approval, eventually filling up the `/transcodes` volume and crashing the pod*):

![](/images/tdarr-node-setup-2.png)

### Library setup

Each library which you want Tdarr to process needs to be setup as follows:

#### Source

For each source folder, ensure that the following options are checked for optimum performance:

![](/images/tdarr-node-source-1.png)

#### Transcode cache

The `Transcode cache` section **must** be set to `/transcode`:

![](/images/tdarr-node-source-2.png)

### Transcode options

Your may require a custom combination of plugins, but the transcoding plugin which works best with our QSV hardware is the one highlighted below:

![](/images/tdarr-node-source-3.png)


{% include 'app_footer.md' %}