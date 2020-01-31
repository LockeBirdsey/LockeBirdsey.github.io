---
published: true
---
## A Pointless Script

I like making tools. That's well known. I needed to do something that seems not very niche, so now there's a script for it.
What did I need to do?  
Crop video, both in time and dimensions, rotate, and save as nice format.  
Why? To upload to services like Byte and Instagram (stories at least). It's way nicer to do self-promotion if a) you don't force people to rotate their device, and b) you provide a nicely focused bit of material for them.


I tried to make it as `bash` friendly as possible. The only weird tool it uses is `ffmpeg`. I should make a version for `mencoder` at some point.
The gist is here: <https://gist.github.com/LockeBirdsey/9566de6787f87079df319c94f6592adc>