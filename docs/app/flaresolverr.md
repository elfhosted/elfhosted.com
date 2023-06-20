# Flaresolverr


## What is it?

FlareSolverr is a proxy server to bypass Cloudflare protection commonly applied to indexers / trackers, so that they can be auto-queried by [Prowlarr](/Apps/Prowlarr).

## How do I use it?

Once you've enabled it in [your account](https://elfhosted.com/tenant/apps/0), configure it as a proxy in [Prowlarr](/Apps/Prowlarr) under `Settings --> Indexers` as follows:

* name: `flaresolverr`
* tags: `flaresolverr`
* host: `http://flaresolverr:8191/`

Then add the `flaresolverr` tag to any indexers requiring it.

## How do I get support?

1. For general use of the application itself, refer to the [upstream project](https://github.com/FlareSolverr/FlareSolverr)
2. For specific support re your ElfHosted configuration / account, either consult the #[elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303) channel, or call for [#elf-care](https://discord.com/channels/396055506072109067/1119478614287712337).

## Useful links

* https://github.com/FlareSolverr/FlareSolverr