# ElfHosted is an Open (Source) Startup

This means that our business metrics, as well as our technical resources, are open for public inspection and input.

!!! question "Isn't it risky to give away your sekrit sauce?"
    Meh. Maybe. There's nothing we do that's especially propriatery or competitive. 
    
    Part of the reason ElfHosted exists is to provide a "reference design" for similar platforms. If you want help doing something like this, hit me up - it's my DayJob(tm)!

## Technical

### Repositories

#### [geek-cookbook/containers](https://github.com/geek-cookbook/containers) 

Contains the containers we run ([available at ghcr.io](https://github.com/orgs/geek-cookbook/packages)), with a build process inspired by https://github.com/onedr0p/containers/

![GitHub Repo stars](https://img.shields.io/github/stars/geek-cookbook/elf-infra) 
 
#### [geek-cookbook/elf-infra](https://github.com/geek-cookbook/elf-infra)

Contains the flux GitOps manifests used to run various services on the cluster, as well as the ansible playbooks / roles to maintain these.

![GitHub Repo stars](https://img.shields.io/github/stars/geek-cookbook/elf-infra) 

#### [geek-cookbook/elf-charts](https://github.com/geek-cookbook/elf-charts)

Contains the charts we use to provide apps, under a single umbrella chart "myprecious". Heavily inspired by https://github.com/k8s-at-home/charts, which I've since forked to https://github.com/geek-cookbook/charts, and continue to maintain

![GitHub Repo stars](https://img.shields.io/github/stars/geek-cookbook/elf-charts) 

#### [geek-cookbook/elfhosted.com](https://github.com/geek-cookbook/elfhosted.com)

Contains source used for https://elfhosted.com, and is built with mkdocs-material on Netlify

![GitHub Repo stars](https://img.shields.io/github/stars/geek-cookbook/elfhosted.com) 

!!! question "What's missing?"
    Ha. Good question. What's **not** public is the repo which houses our user configs (*each user's particular combination of helm charts and values*), for obvious reasons, and all the secrets etc which make the magic work.