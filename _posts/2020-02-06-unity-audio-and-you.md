---
published: true
title: 'Unity, (synthetic) Audio, and YOU!'
---
## Unity, (synthetic) Audio, and YOU!
### (Well, me)

I've just spent a week getting acclimatised to Unity (it's been 7 years since I used it last...) for a project I want finished by the 1st of March.

I don't feel like divulging too much since otherwise I'll probably not get on with it, BUT, it involves a lot of audio synthesis and Twine. 

Audio synthesis in Unity is...interesting. After a week it makes a LOT more sense, but this is most likely me understanding how Unity -actually- works. Of course, Unity has a HUGE community and audio synthesis tools exist. But as is always the way, the good ones require $$$. Some not-very-thorough digging resulted in some open source synthesis tools[^1] and pretty much work as is. "Pretty much" is where it gets funky.

Enter sequencing. I started this by making a clock. That...wasn't enough. Random dead open source project to the rescue[^2]. Now I had audio file sequencing. Useful, but not what I needed. A whole lot of tweaking and testing later I know have a set of sequencers and synthetic instruments. Nothing fantastic, but I'm gradually making it more modular and you can guess where this is going.

BUT NOT YET

I want to do this project (or at least get a proof-of-concept out) before going overboard into software modular synthesis[^3]. A secondary likely splinter project that will appear is expanding Cradle[^4] (the Twine > Unity framework) to do some more things. 

Alas, where it stands right now requires more work into thinking how other parts work before blowing up my todo list. So instead I'll be (attemping to) jam over the next few days.



[^1]: <https://github.com/pixlpa/Unity-Synth-Experiments>
[^2]: <https://github.com/Ludomancer/Unity-Audio-Sequencer>
[^3]: I mean FFS we have the glorious VCV rack for that but still, for inside Unity stuff.
[^4]: <https://github.com/daterre/Cradle>