---
title: a diversion, one of many
description: ""
date: 2023-01-15T07:48:14.782Z
preview: ""
tags: ""
categories: ""
---

Well, this is kind of a shit with respect to my recent posts.

0 update on the game. Since work came back this year, it's been a bit tricky to work on it. I've been focusing on getting my routines and schedules and relaxing back on track. That's not to say I haven't done any outside-of-work coding.

### My problem:

I exercise on a stationary bike. I like to track my heartrate, and my pace. Pace on a stationary bike is a bit weird but it's a metric I use to see if body is getting more used to it (I go for long periods without exercising). And I like to track that on Strava so when I do actual rides, I can better compare.

### Solution:

Smart-watch. Tracks heart rate and exercise specifics. Pace is missing but the good, important stuff is there. But I really want to record my distance to calculate my pace.

Can I enter my distance in somewhere? For Polar, yes you can. Great! Oh, an allergic reaction means you have to try a dozen different watch bands. Thanks to an underwhelming 3rd party market, there aren't any straps that are big enough for my watch.

Hrmm, which smartwatch does have that? Fitbit! Cool, back to Fitbit `</s>`. Oh it now has "Spinning" as a workout option.

Can I enter my distance? No. Hrmm, what if I used the "Ride" workout? No.

So how can I get this into Strava? Oh, I can have Fitbit automatically upload exercise data to Strava.

Oh why isn't it working? "Spinning" doesn't record a heart-rate so Strava won't recognise it, and "Ride", since I'm stationary, doesn't record a distance.

### The (actual) problem:

When I was using Polar, my process would involve: sync watch, load Polar dashboard on browser, open recorded exercise, for lap 1 alter the distance to match what I did, export exercise as a TCX file, upload to Strava.

But Fitbit, I can't do this, but I can export an exercise as a TCX file. So, that's what I did and I was horrified. If your activity is set to "Spinning", the TCX file only records the start time and the end time. However, if it's set to "Ride", it exports a segment every 5 seconds with the current heart rate, but a distance of 0. Oh easy right, lets just use "Ride" and manually add the distance to the TCX file.

Not so. Strava calculates distance based on the total distance accumulated from each segment. So if I rode for 30 minutes, I would need to alter 360 segments and do something like distance/(time\*60/5) for each segment. That's too annoying, especially by hand. But there is a field called `DistanceMeters` I can use. Oh nope. Since "Ride" also records lat/lon, Strava will think there's distance in that segment if it sees the lat/lon. Easy, remove all the lat/lon and segment distances.

And that's the solution: Use the "Ride" workout, scrub all the lat/lon and distances from the segments, and add the total distance to the parent `DistanceMeters`. Of course, this isn't that easy to do. But still, `tcxa` (TCX Anonymiser) exists and does just that.

```
tcxa.exe -i input-file.tcx -o output-file.tcx -d distanceInMetres
```

It's in `Rust`, it's ugly as hell, but it does exactly what I want.

### Next step:

This is too ugly. My next version of this will instead call the Fitbit API, get the HR and exercise data, ask for the distance, and output a TCX to upload to Strava (ideally all in a browser). Next step from there is remove the manual upload, but that's going to be a long time. This way I can stop using "Ride" and instead use "Spinning", which means I won't upload any positional data to Fitbit.

We'll see when that happens...

## The game:

I'll get back to it soon. I've been enjoying playing games a bit too much as well, but that has been good I think. 

---
Until next time, where my head will be mashed by trying to do something wacky with K8S.
