---
published: false
---
# Reclaiming Fibres

Many eons ago, I used to make interactive fiction.  
I was good at it.

So I'm trying to get them back up and working again. And boyyy is it taking a while. So I might run through the steps.

## From Twine 1 to Twine 2

Fibres was made a long time ago (2012 or 2013). Twine 1 (or more importantly Twee2) was the cutting edge. The story format (Sugarcube) had some limitations, so custom macros were all the rage. Porting from Twine 1 to 2 was easy. A tool that advertised as such could be downloaded and ran. Did it work? Of course not. It was from 2015, what did I expect? [^1] Take 2: Maybe Twine's export to Twee code feature would produce a file that could be imported into Twine 2. Ei/non/no. Twine 2 can only import compatible HTML files. Take 3: Generate the HTML from Twine 1 and import into Twine 2. Ei/non/no. Silent failures on both in browser and downloaded versions of Twine 2 [^2]. What to do?

Well, tweego exists[^3]. And can do some cool things. Like convert between versions of Twee code, but most importantly export to Twine 1 or 2 archives. C'est magnifique! 

``tweego my-poor-twee-file.tw2 -a -o output-to-twine2.html``

### A Caveat: Twine VCS


## From twine generated html to an executable in the year of our lord 2020

Hrmm, this was the hard part. Why? Because lots of different tools have lots of little issues that break. I will have nightmares about `ENOTDIR` for a while to come.  
The plan: make an executable of a Twine game to put on itch.io. I'm aware I could deploy for web there (or quite frankly anywhere), but I want distributables because then a JS update won't come along and cripple it (a la `Awaken` on GameJolt until recently).

## The full workflow. 
### From an old Twine 1 game to a stable, safe Twine 2 one with distributing

[^1] the author of it is rather important in the Twine scene so it was a bit of a shock.  
[^2] I mean the downloaded Twine 2 still exists in a browser, but a steady Electron one at least.
[^3] And is authored by the person that made the tool mentioned in [^1]