---
published: true
---
# Reclaiming Fibres

Many eons ago, I used to make interactive fiction.  
I was good at it.  

So I'm trying to get them back up and working again. And boyyy is it taking a while. So I might run through the steps. It has been a LONG time since I checked out the Twine scene, and as such, I'm rather behind on developments. 

## From Twine 1 to Twine 2

Fibres was made a long time ago (2012 or 2013). Twine 1 (or more importantly Twee2) was the cutting edge. The story format (Sugarcube) had some limitations, so custom macros were all the rage. Porting from Twine 1 to 2 was easy. A tool that advertised as such could be downloaded and ran. Did it work? Of course not. It was from 2015, what did I expect?[^1] Take 2: Maybe Twine's export to Twee code feature would produce a file that could be imported into Twine 2. Ei/non/no. Twine 2 can only import compatible HTML files. Take 3: Generate the HTML from Twine 1 and import into Twine 2. Ei/non/no. Silent failures on both in browser and downloaded versions of Twine 2 [^2]. What to do?  

Well, tweego exists[^3]. And can do some cool things. Like convert between versions of Twee code, but most importantly export to Twine 1 or 2 archives. C'est magnifique!  

`tweego my-poor-twee-file.tw2 -a -o output-to-twine2.html`  

Import into Twine 2 and suddenly it appears.  
Oh god, the issues.  

So those custom macros I mentioned? Well, the JS for them no longer works. Bollocks I hear you say. Never. Twine macros are Story Format dependent. `Fibres` used `Sugarcube`, a Twine 1 format. A increased captial version exists for Twine 2 called `SugarCube`. As it just so wonderfully turns out, my custom macros are now core in `SugarCube`. Just with different names and parameters. Regex made short work of that.  

An interesting issue that was probably exclusive to me was a passage link failing on a number of chapters. Specifically:  

`[[-->|Passage]]`  

The documentation for linking is quite straight forward: `[[Text|Link]]`. So why does `-->` fail?  
Well, how are Twine2 files stored? HTML. And what is a comment in HTML? That's right 
`<!--comment-->`  
Easy fix, just replace --> with literally anything else. 

And Fibres comes to life. Glorious.  

Intermission`<blink><marquee>`

### A Caveat: Twine Version Control

A big surprise to me is that NONE of my Twine projects were in any form of version control outside of Dropbox. Something that needed to be fixed in the middle of all this. Because of how Twine 2 behaves, this is not a straightforward solve.  

The main issues:
- Twine 2 runs as an Electron app, and doesn't include any features for selecting where stories may live.
- Well, having to use Twine 2 since it's a really nice tool and I don't want to edit branching stories in Sublime Text.  

**Stage 1: Get the essentials into a repo.**  
Twine 1 source file, Twee2 file, and the Tweego converted Twee3 file. Cool. Bananas. A starting point.  

**Stage 2: Use Twine 2 to edit and update these files** 
Twine 2 does use a /nice/ directory for storing stories which makes this easier, namely `$HOME/Documents/Twine`  
We need to prepare our Twee file for use in it.  

`tweego Fibres.twee --archive-twine2 --output=$HOME/Documents/Twine/Stories`[^4]  

Now we can open in Twine 2.  

\*edits\*  

How can we bring it back and save the changes, both layout and textual, to our VCS of choice?  
Not hard.  

`mv $/Documents/Twine/Stores/Fibres.html our/vcs/repo`  

And then update our source file.  

`tweego Fibres.html -d -o Fibres.twee`  

This is all rather straightforward. There is additional issue that Twine 2 creates: When `Fibres` archive was opened, Twine 2 saves an archive that uses the `StoryTitle` parameter. Which in this case wasn't `Fibres` but instead `Fibres[Part 1]`. Oops. Easy fix.  

Now we're all happy. Generate the Twine 2 archive, copy to the Twine 2 story directory, work on the file, copy the file back and decode to Twee3 code. E.A.S.Y

## From Twine generated html to an executable in the year of our lord 2020

Hrmm, this was the hard part. Why? Because lots of different tools have lots of little issues that break. I will have nightmares about `ENOTDIR` for a while to come.  
The plan: make an executable of a Twine game to put on itch.io. I'm aware I could deploy for web there (or quite frankly anywhere), but I want distributables because then a JS update won't come along and cripple it (a la `Awaken` on GameJolt until recently).  

**Approach 1: Use someone else's Twine/HTML game tool.**  
Simples. There's a few listed. Some are very old and unmaintained. Some are overkill (one day I'll try you Cradle). A promising one called HTMLE exists. It however doesn't work nicely at uses a very old nw.js build. Not ideal.   

**Approach 2: Do my own NW.js build**  
This did not look particularly fun and lots of people have moved away from NW.js to...  

**Approach 3: Electron seems good. Let's use that**  
Twine 2 uses Electron, so if it's good enough for them, it's good enough for me. 
Simplified creating of Electron apps is ironically not very simple due to NPM/NPX vs Yarn issues. Three main tools exist: `electron-packager`, `electron-builder`, and `electron-forge`. I tried them in this order. Why did I try 3? Because the first two kept throwing up either issues during build or execution of the final output. `electron-forge` however worked almost perfectly once I realised that I still had some stray .yarn directores and thus purged them.
So now I have a distributible Fibres. Yay! The goal reached!  

Ha.  

Can we include working audio in this app?  
Yep.  

Oh good.  

`electron-forge` does require some boilerplate to be saved to make life easier. And thats the only addition to the repository. Excellent. Well, now we have a build script that moves stuff around so that out final executables contain everything and work correctly. Just need to remember to update that `packages.json` file every so often.  

## The full workflow. 
### From an old Twine 1 game to a stable, safe Twine 2 one with distributing

I think it's worth preserving, at least for my sake, how to do this. I have a LOT of Twine 1 files. There's a number of tools to be made from this, but I'll save that for a future bout of hypomania.  

How does the directory in version control look now?  
    
	/
	--src
        --audio
        --imgs
        index.html
        Fibres.twee
    --twine1
        Fibres.tws
        Fibres.tw2
    --dist
        --fibres
            -Package.json
            -**other stuff**
        Makefile
    

Of course, saving audio and images to VCS is an issue because of size, so they currently remain in Dropbox. For lack of a VPS, this must be the way.

Whether or not this is helpful to anyone remains to be seen, but at least it is for me.

The links to the saving graces of the day:

- Tweego <https://www.motoslave.net/tweego/>
- electron-forge <https://github.com/electron-userland/electron-forge>


[^1] the author of it is rather important in the Twine scene so it was a bit of a shock.  
[^2] I mean the downloaded Twine 2 still exists in a browser, but a steady Electron one at least.  
[^3] And is authored by the person that made the tool mentioned in [^1]  
[^4] This if for \*-nix systems. On Windows it is likely different. I will update once I move to Windows land for editing Twine files.
