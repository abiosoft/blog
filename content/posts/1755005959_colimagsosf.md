+++
title = "Colima participated in the Github Secure Open Source Program"
description = 'Colima participated in the Github Secure Open Source Program'
date = 2025-08-12T14:39:19+01:00
readTime = true
tags = ["colima", "github", "opensource", "security"]
draft = false
+++

[Colima](https://github.com/abiosoft/colima) was selected for the [Github Secure Open Source Fund](https://resources.github.com/github-secure-open-source-fund/) and participated in the security program
with [70 other projects](https://github.blog/open-source/maintainers/securing-the-supply-chain-at-scale-starting-with-71-important-open-source-projects/).

### What is Colima?

Colima provides container runtimes on macOS and Linux.

While it is regarded as an alternative to Docker Desktop, Colima supports multiple container runtimes
including [Docker](https://docker.com), [Containerd](https://containerd.io), [Kubernetes](https://kubernetes.io) and [Incus](https://linuxcontainers.org/incus).

### Some history

Colima started out as a personal [bash script](https://github.com/abiosoft/colima/blob/81cd704a6a8ce970cca75b47a54975a56b2c3afe/limakube) for running Docker and Kubernetes containers without needing Docker Desktop.

It builds on a project called [Lima](https://github.com/lima-vm/lima). The initial name was in fact, [LimaKube](https://github.com/abiosoft/colima/blob/81cd704a6a8ce970cca75b47a54975a56b2c3afe/README.md) before deciding on Colima [two days later](https://github.com/abiosoft/colima/commit/d0686356eb7c81bf453b63746e6219ca4f90ad58).

Due to positive feedback, it was later re-written in [Go](https://go.dev) to add more capabilities.
Nonetheless, it was meant to be just another toolkit for my use.

### Surprising Popularity

Github issues kept piling and community engagements are on the rise. They however do not mean much, until I saw a notification
in a WhatsApp group (of me and some of my friends) that reads as follows.

> We're leaving Docker Desktop at my office to use your work Colima

That opened the floor for conversations and it turned out some of my friends are already aware but waiting for the right
moment to mention it to me. A while later another friend posted the following message.

> We've been told to switch to Colima before end of month

I cannot help but wonder how a project without any documentation (asides the offical readme), is getting this much
adoption.

There are many articles written and many videos made about Colima. However, this is the first time I would personally
write about the project. I guess I must've done something right, for once.

Colima would go on to see [contributions from 90 people](https://github.com/abiosoft/colima/graphs/contributors)
and amass [**24k** stars on Github](https://github.com/abiosoft/colima/stargazers).
It also sees thousands of downloads monthly on [HomeBrew](https://formulae.brew.sh/formula/colima).

![Downloads count on HomeBrew](/images/1755005959_colimagsosf_1.jpg#small)

### My toy, their tool

I have a personal saying that goes like this.

> You can guage your project's usefulness by pushing out a breaking change.

It was something I learned in the early days of [Caddy](https://caddyserver.com) as the maintainer of the
[docker image for Caddy v1](https://hub.docker.com/r/abiosoft/caddy).

I assumed that the docker image is barely used by others and knowingly [mutated some tags](https://github.com/abiosoft/caddy-docker/issues/31), even though tags are meant to be immutable, ideally.

While Colima is a personal toy for my workflows, it is a tool relied upon by many with verying level of use-cases, like [this one](https://youtu.be/CuCC_r79gck?t=530).

I do get reminded of Colima's relevance anytime something goes wrong. Apart from Github issues, I do get contacted in all
possible communication channels I have. [^1]

### Github Secure Open Source Program

Colima was nominated and selected for the [Github Secure Open Source Fund](https://resources.github.com/github-secure-open-source-fund/),
a testament to it's relevance.

Over the past few weeks, I attended days of workshops and trainings with focus on security for open source projects.

I had the honour of e-meeting maintainers of very popular open source projects including
[ExpressJS](https://expressjs.com/), [Oh-My-Zsh](https://ohmyz.sh/), [Flux CD](https://fluxcd.io/), [JUnit](https://junit.org/),
[Bootstrap](https://getbootstrap.com/), [NativeScript](https://nativescript.org/) and [NVM](https://github.com/nvm-sh/nvm).
I also met multiple open source leaders, as well as security leaders at Github and Microsoft.

You can read the official announcement of the [Github Secure Open Source Program here](https://github.blog/open-source/maintainers/securing-the-supply-chain-at-scale-starting-with-71-important-open-source-projects/), which mentions Colima alongside 70 other projects.


### What is next?

The current focus of the Colima project is to improve it's stability, attend to security and bug fixes, and reliability related issues.

With the launch of [Apple Containers](https://github.com/apple/container/) and [Lima gaining Windows support (via WSL2)](https://lima-vm.io/docs/config/vmtype/#wsl2),
there is more in store for Colima in the coming months.

### Supporting the project

You can support Colima in multiple ways.

- Using Colima and providing valuable feedback.
- Engaging other users in communication channels (Github issues, Slack).
- Source code contribution
- Financial support on [Github Sponsors](https://github.com/sponsors/abiosoft/), [Buy Me a Coffee](https://buymeacoffee.com/abiosoft) and [Patreon](www.patreon.com/colima).

[^1]: I do not honour messages outside of the designated communication channels for the project.
