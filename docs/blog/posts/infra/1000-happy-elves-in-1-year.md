---
date: 2024-06-20
categories:
  - infra
title: Discord is 1 year old, 1,000 Elves strong!
description: One year in, we welcomed our 1,000th Elf into Discord today (and taught ElfBot how to backup symlinks!)
---

# 1 year, 1000 Elves 🎂

Today the Discord stats widget (*the "elf-o-meter"*) ticked past 1,000 elves! 🥳

Totally coincidentally, it's also 365 days since our oldest elves joined the [Discord server][discord]! (*we had a 6-week "dev" period, and went into "prod" on 1 Aug*)

For a glimpse of how far we've come, and where it all started, check out [this Reddit post](https://www.reddit.com/r/seedboxes/comments/143qegl/comment/jnpfb2n/?utm_source=reddit&utm_medium=web2x&context=3) from a year ago!

<!-- more -->

It took a few iterations to get our initial cluster built, but here's a snapshot showing our oldest original node (*which hasn't been subsequently re-installed*):

```
NAME       STATUS                     ROLES                       AGE    VERSION
dwarf01    Ready                      <none>                      183d   v1.28.4+k3s2
dwarf02    Ready                      <none>                      364d   v1.28.4+k3s2
dwarf03    Ready                      <none>                      183d   v1.28.4+k3s2
```

## ElfBot backs up symlinks

In what we're informally code-naming the "*check-your-rd-key*" update, :rofl: [ElfBot][elfbot] can now backup all your symlinks! (*A precursor to a potential Hetzner-less, multi-region design for infinite streaming bundles*)

To perform this onerous task, run `elfbot backup symlinks`, sit back and wait for about 0.003s, and then rest easy in the knowledge that your massive collection of links to another massive collection of links, is now safely backed up to `/storage/elfstorage/backup/`! :muscle:

## Riven rocks on!

Tonight's update (*v0.7.3*) from the [Riven][riven] devs is a big one - it includes:

* changes for debugging of memory use
* significant speed improvements (*2-4x faster*)
* improved results from scrapers
* internal refactoring and improvements

Riven Discord discussion has moved to its own permanent channel, at [#elf-riven](https://discord.com/channels/396055506072109067/1253110932062601276), and remember that you can sponsor / tip your Riven dev [here](https://github.com/sponsors/dreulavelle) :heart: !

## Get involved!

Our [Discord community][discord] is growing, and we're investing in tools and processes to keep things running smoothly. You'll soon see improved [#elf-support](https://discord.com/channels/396055506072109067/1245513340176961606) processes (*thanks \@mxrcy!*), and hopefully a replacement AI (*Glime is unfortunately shutting down in July*).

If you'd like to get involved as an [ElfVenger](/team/#elf-vengers), and you have a set of skills (*or just a ready smile*) to contribute, we'd love to meet you! There's an ever-growing list of projects, not all of which require high levels of technical skillz, so if you're keen to get "on the inside", drop into [#elf-venger-plz](https://discord.com/channels/396055506072109067/1198400497632153630), and follow your nose!

## Today's scoreboard

Metric | Numberz | Delta
---------|----------|----------
🧝 Total subscribers | 359 | +6
👾 Zurg mounts: | 145 | +1
⛰ Riven pods: | 25 | +1
💾 [ElfStorage](https://elfhosted.com/what-is/elfstorage/) in TBs | 111 | -
🐬 Tenant pods[^1] | 3321 | +119
🦸 [Elf-vengers](https://elfhosted.com/team/#elf-vengers) | 8 | -
🧑‍🎓 Trainees | 23 | -
🐛 Bugz squished | - | -
🕹️ New toyz | 1 | -

## Summary

Thanks for geeking out with us, and please share these posts with related geeks! Type `/review` into any Discord channel to share your experience - this helps us to attract mooar elves!

--8<-- "common-links.md"
