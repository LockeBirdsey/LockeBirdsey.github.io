---
title: golang? I hardly know him-g
description: ""
date: 2022-12-04T08:17:45.262Z
preview: ""
tags: ""
categories: ""
published: true
---
So there's been some more from the previous post. I quite like `golang` I think, although the lack of actual concrete style rules is very weird as a Google product but hey, I can live with that.

BUT! In my maybe an hour a day of wrangling with `golang` and `ebitengine` I've actually gotten somewhere. There has also been a LOT of refactoring to get things to behave nicer and faster[^1]. Maybe once this goes a bit further I'll do a quick architecture overview but it's going to look a lot like normal ECS & "scene-based" game-dev architectures because, well, that's basically what I've been doing[^2]. There's one thing my brain sucks at and that's geometry. Since I can't visualise stuff ([Aphantasia](https://en.wikipedia.org/wiki/Aphantasia) and all) doing geometric calculations sucks. So I spent a lot of my time refactoring in such a way I would be able to do fewer of them. And I got it down to 2 from 5. Pretty good. But what was that main hurdle:

![](/assets/setfirstgroundselect.gif)

Yep, looks pretty *okay* I would say. Highlighting tiles is pretty important in what I have planned (TB/S RPG probably but maybe more). But as you can see, there is still minor hiccough. There's a LOT still to come (my to-do list[^3] is ever expanding) but this is a big, big hurdle to get over.

Of course I did make it hard for myself by trying to have the tiles generate their highlighted state automatically but it was very ineffective, but I'm keeping that code for later since it might work in other contexts.

I also have an idea of how this game should sound but we are a looooong way from that.

I guess next week there may be something more, unless I get bored or frustrated.


[^1]: who knew that initialising an `ebiten.Image` 60 times a second might eventually cause issues...
[^2]: but as I usually do, off the top of my head without reading anything :+1:
[^3]: I might write up something about task tracking in different projects because different methods tickle my brain in different ways
