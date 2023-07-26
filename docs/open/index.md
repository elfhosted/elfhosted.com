# ElfHosted is an Open (Source) Startup

This means that our business metrics, as well as our technical resources, are open for public inspection and input.

!!! question "Isn't it risky to give away your sekrit sauce?"
    Meh. Maybe. There's nothing we do that's especially proprietary or competitive.
    
    Part of the reason ElfHosted exists is to provide a "reference design" for similar platforms. If you want help doing something like this, [hit me up](https://www.funkypenguin.co.nz/work-with-me/) - it's my DayJob(tm)!

## Metrics

Each month's metrics are summarized in the left-hand navigation column

## Traffic

#### elfhosted.com

<iframe plausible-embed src="https://plausible.io/share/elfhosted.com?auth=gxX1I4vjUN50asSjGE8nU&embed=true&theme=system&background=transparent" scrolling="no" frameborder="0" loading="lazy" style="width: 1px; min-width: 100%; height: 1600px;"></iframe>
<div style="font-size: 14px; padding-bottom: 14px;">Stats powered by <a target="_blank" style="color: #4F46E5; text-decoration: underline;" href="https://plausible.io">Plausible Analytics</a></div>
<script async src="https://plausible.io/js/embed.host.js"></script>

#### store.elfhosted.com

<iframe plausible-embed src="https://plausible.io/share/store.elfhosted.com?auth=X8cOGY9-_ltHXzC9NJebb&embed=true&theme=system&background=transparent" scrolling="no" frameborder="0" loading="lazy" style="width: 1px; min-width: 100%; height: 1600px;"></iframe>
<div style="font-size: 14px; padding-bottom: 14px;">Stats powered by <a target="_blank" style="color: #4F46E5; text-decoration: underline;" href="https://plausible.io">Plausible Analytics</a></div>
<script async src="https://plausible.io/js/embed.host.js"></script>

## Technical

### Performance

(one day, I'll get live graphing working here!)

### Repositories

#### :simple-github: [geek-cookbook/containers](https://github.com/geek-cookbook/containers) 

Contains the containers we run ([available at ghcr.io](https://github.com/orgs/geek-cookbook/packages)), with a build process inspired by https://github.com/onedr0p/containers/

[![GitHub commit activity (branch)](https://img.shields.io/github/commit-activity/w/geek-cookbook/containers/main)
![Lines of code](https://img.shields.io/tokei/lines/github/geek-cookbook/containers)
![GitHub Repo stars](https://img.shields.io/github/stars/geek-cookbook/containers)](https://github.com/geek-cookbook/containers)
 
#### :simple-github: [geek-cookbook/elf-infra](https://github.com/geek-cookbook/elf-infra)

Contains the flux GitOps manifests used to run various services on the cluster, as well as the ansible playbooks / roles to maintain these.

[![GitHub commit activity (branch)](https://img.shields.io/github/commit-activity/w/geek-cookbook/elf-infra/main)
![Lines of code](https://img.shields.io/tokei/lines/github/geek-cookbook/elf-infra)
![GitHub Repo stars](https://img.shields.io/github/stars/geek-cookbook/elf-infra)](https://github.com/geek-cookbook/elf-infra)

#### :simple-github: [geek-cookbook/elf-charts](https://github.com/geek-cookbook/elf-charts)

Contains the charts we use to provide apps, under a single umbrella chart "myprecious". Heavily inspired by https://github.com/k8s-at-home/charts, which I've since forked to https://github.com/geek-cookbook/charts, and continue to maintain

[![GitHub commit activity (branch)](https://img.shields.io/github/commit-activity/w/geek-cookbook/elf-charts/main)
![Lines of code](https://img.shields.io/tokei/lines/github/geek-cookbook/elf-charts)
![GitHub Repo stars](https://img.shields.io/github/stars/geek-cookbook/elf-charts)](https://github.com/geek-cookbook/elf-charts)

#### :simple-github: [geek-cookbook/elfhosted.com](https://github.com/geek-cookbook/elfhosted.com)

Contains source used for https://elfhosted.com, and is built with mkdocs-material on Netlify

[![GitHub commit activity (branch)](https://img.shields.io/github/commit-activity/w/geek-cookbook/elfhosted.com/main)
![Lines of code](https://img.shields.io/tokei/lines/github/geek-cookbook/elfhosted.com)
![GitHub Repo stars](https://img.shields.io/github/stars/geek-cookbook/elfhosted.com)](https://github.com/geek-cookbook/elfhosted.com)

!!! question "What's missing?"
    Ha. Good question. What's **not** public is the repo which houses our user configs (*each user's particular combination of helm charts and values*), for obvious reasons, and all the secrets etc which make the magic work.