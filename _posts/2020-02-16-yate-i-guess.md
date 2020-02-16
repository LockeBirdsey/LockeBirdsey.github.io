---
published: true
---
## Making some tools to make someones? life easier

Deploying Twine stories as executables is slightly annoying, especially when working across multiple platforms. In the "Reclaiming Fibres" post, I devised a structure for simplifying this while keeping it logical for VCSs. However, lots of Twine users don't use any VCS and it'd be easier to use a standalone application to package things for release.

So I see 2 main problems here:
1. How can we make this easy while still being platform and user independent?
2. Interoperability with the Twine2 structure

Problem 1 is where the bulk of this post lies.

I still plan on using electron to package the executables. This requires NPM/NPX to do. As such, writing this in something that depends on NPM/NPX is slightly problematic for the non-technical user. This pushed me to make it in something else, however, the ease of use consideration made this choice easy. I decided on Python as prior experience with GUI development in C++ and Java is painful. A package for Python called "PySimpleGUI" makes this VERY easy. The problem now becomes a design problem.

So, this tool (or set of tools really) has to accomplish certain tasks:
- Set up the Electron app builder directory
- Move all the necessary Twine, HTML, and other files to the correct directory
- Add the correct data to the various JSON files
- Build the app for Platform X
- Build the app for Web

In it's current state, it treats each new build as an entirely new Electron app. Which means lots of NPM downloads, and it doesn't alter the Electron config files. My goal is to have this as a single program, with two main functions: 1) setup the Electron app builder directory, 2) build an executable.

Cool. Great. But back up to problem 2. How do we cater for people that only user Twine2?
Of course, this shadows another problem but alas.
I think the *best* port of call for this is to rely on the Twine2 user to "Publish to HTML".

The proposed workflow for a Twine 2 user is as follows:
1. Work on story
2. Publish to HTML to any directory
3. Open my app, select the HTML file, choose a directory to build in
4. Build directory, copy HTML to it
5. Alter settings (if needed)
6. Build executable

In the case the entire story is self-contained as an HTML file, done! But of course, thats not always the case. I fear it may even be very seldom the case.

What happens if you have images and audio included? We now run into a problem that Twine2 handles differently compared to using Tweego and CLI. Paths are absolute compared to relative. In the latter, this is easy (assuming the author is logical) because a common structure is usually followed:

```
twine_project_dir/

    story.html
    
    imgs/
    
        an_image.png
        
    audio/
    
        some_audio.mp3
```

Easy. Copy ``twine_project_dir`` to the Electron directory. 
Twine2 is not so simple. Potential solutions are: 
- Parse the story file, copy all the images and audio to local directories, replace the paths
- Make the author conform to the above structure manually
- Prompt the user to move their audio and images to the Electron directory and update their story

None of these options are nice and it will take a while to think this through.

I'll make a post once I've finished this app (currently known as YATE) to see which design decisions I ended up making.
