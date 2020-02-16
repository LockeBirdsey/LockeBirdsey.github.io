---
published: false
---
## Making some tools to make someones? life easier

Deploying Twine stories as executables is slightly annoying, especially when working across multiple platforms. In the "Reclaiming Fibres" post, I devised a structure for simplifying this while keeping it logical for VCSs. However, lots of Twine users don't use any VCS and it'd be easier to use a standalone application to package things for release.

So I see 2 main problems here:
1. How can we make this easy while still being platform and user independent?
2. Interoperability with the Twine2 structure

Problem 1 is where the bulk of this post lies.

I still plan on using electron to package the executables. 