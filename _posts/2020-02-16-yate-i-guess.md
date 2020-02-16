---
published: false
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

In it's current state, it treats each new build as an entirely new Electron app. Which means lots of NPM downloads.
