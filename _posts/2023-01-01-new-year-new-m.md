---
title: new year new m
description: ""
date: 2023-01-01T12:53:35.812Z
preview: ""
tags: ""
categories: ""
published: true
---
Well in continuing with the fortnightly updates, the fifth(!) in this series lands on new years day. And I am tired. Luckily (or not), there's not too much to talk about. I have taken a few days off this fortnight from it to work on some other things and also relax. I did start playing Final Fantasy Tactics for the first time in many, many years, and that has given me a whole bunch of new ideas.

Since last time, we now have:
* Cutscenes
* Rotation
* \> 1 height tiles!
* Level importing/exporting
* A level editor!

In addition to these things, I've also spent a bunch of time in spreadsheets figuring out rules and stats. We're actually getting somewhere which is nice.
I won't write much about the tile height stuff. Just that it was a pain because they kept drawing in insane locations. However, I'm still not 100% set on the method I ended up with. It's likely in the future I'll investigate the cooler method I was trying which allowed any height and width structures made of tiles. Does height actually matter though in gameplay yet? Nope. 

### Rotation

This was a biggy, and also kinda simple once I realised I was reading from the wrong matrix... There are 4 rotations now and it is really cool being able to see the battlefield from these angles. There are *some* issues though e.g. some tiles lose their meaning in other orientations. I'll figure that out later and decide if it's really worth keeping.

### Cutscenes

They are in a traditional visual novel style. They have their own JSONs as well and I can do an awful lot with them already. I won't post a picture because it is very ugly with placeholders and flat fills. Maybe soon. The cutscene player has a typewriter mode and automatic text-wrapping so I don't need to add `\n` in the dialogue manually (unless I want to). This was pretty easy to do, although I spent lot of time having the text being cut off really early. Spent a good 30 minutes investigating that to only find the wrap value was set to the height of the textbox and not the width. Ooops. I do need to spend some more time with fonts because I just can't find one I like. 

### Level editor & importing/exporting

![](https://i.imgur.com/xBSLFES.png)

This was borne out of necessity. It actually begun with level generation. I started writing a random level generator because a) infinite levels, and b) I'm not a level designer. After a day[^1] or so of work, I began to realise that maybe generation would get me 75% of the way and the rest would need to be tweaked manually. So I wrote an exporter for the levels. It took about 20 minutes and most of that time was spent deliberating how they should be stored. I chose a way that was ~27% more space efficient than the simplest way and still maintains some readability. Considering my maps are currently 20x20 i.e. 400 tiles, it's still not so readable. 
Entries kinda look like:

```

"tile_sprite_id": { "coords": [coord1, coord2] }

```

At this point I was *seriously* thinking of editing the points in the JSON. Yes, that was insane. And that's how the level editor came to be. Again, it was very simple, about an hour of work and I could load in the level JSON, click on each tile to cycle through the available tile sprites and then export (albeit to `stdout` but still). I guess I'm going to have to learn some level design, or just play more tactics games. I still have a few things I need to consider & implement such as depth, cover and line-of-sight.

---

I'm back at work as of tomorrow and back to my old routines, so there'll be a couple of hours work on this a week which kinda sucks, especially since some hard bits are coming up and I can't just do them in front of the TV. Also actually thinking about narrative again and since this will be part of the universe I set my book in, I need to check my notes. 

Until next time (probably in another 2 weeks. Maybe)

[^1]: A day is a bit subjective and changeable. 30 minutes minimum to 4 hours max