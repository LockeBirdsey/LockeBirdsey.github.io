---
title: self-host? more like self-coast-into-hell
description: ""
date: 2023-07-08T15:25:14.782Z
published: true
preview: ""
tags: ""
categories: ""
---

took me a while but i've been bitten by the self hosting bug. current plans are to run:

* some wiki (wikijs, dokuwiki or [mycorrhiza](https://mycorrhiza.wiki/))
* commento for adding a comment section to my personal blog
* jenkins so i can run ci from my codeberg (more about that later) \[but also maybe woodpecker instead\]
* some tools to help my partner out with video stuff
* either wallabag or shaarli for bookmark management (i'm a little annoyed with raindop.io)
* and probably something to replace this gh pages stuff

the yunohost image seems like it'd be easy to get most of this going. although i have seen a comment that suggests it does some silly things with `systemd`

some form of vanilla linux with docker or even k3s/microk8s would also be fine

## but why?

i deal with too many services and a lot of the nice replacements tend to be require self-hosting. i also want to reduce my dependence on `obsidian` and also be able to access it at work. 

i could also add some fedi* stuff but we'll see. that stuffs expensive on the ol' bandwidth

## the missing thing?

backups. if i do any of this, i need solid ways to back everything up. i will make a post about that (assuming i ever even get around to all this)
