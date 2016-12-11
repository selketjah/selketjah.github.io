---
layout: post
title: Forge, my first OSS contribution
tags:
- F#
- Forge
- OSS
---

When speaking to [Pieter Hintjens](http://hintjens.com/) about open source communities and how they should behave towards newcomers, 
he said that a first successful contribution is one of the most important things in a project. Successful meaning that their pull request gets merged back into the project.
Even if the pull request breaks the build, just merge it back. Especially, if you want them to keep contributing.

Aftwards you can send them a nice message saying: 'Hey, your PR broke the build because of x or y, but we merged it anyways. This is how you can prevent it from happening again.'
If they keep submitting pull requests that break the build and don't bother fixing it, draw your conclusions.

The win is more important. I always liked that vision.

<!--more-->

## The path to Forge

When I learned F#, I fell in love with the language and the community. The community was very open and welcoming and it made me want to help out, but 
starting to contribute was very scary for me for a couple of reasons.

The idea that you can do something wrong in a very public setting, is one of the reasons I kept postponing a contribution.
During BuildStuff this year, I had the pleasure to meet Krzysztof Cieslak. He has done some really great work in the F# community
with projects like [Ionide](http://ionide.io/) and [Forge](http://forge.run/) 

It was a good opportunity to remove some of the reasons I kept postponing.
I strapped on by Boots of Courage and asked him if he would be willing to take me through the [code of Forge](https://github.com/fsharp-editing/Forge).
He was. So we went through the code and he explained the big lines on how Forge works behind the scenes. 
He challenged me to make my first pull request by the next week and I accepted that challenge.

After a while we started talking about open source in general. His way of handling his open source projects is very similar
to Pieters: any contribution, no matter how small it may seem, is valued.
It was.

## Forging ahead

If you never contributed, the best place to start is reading the contribution guidelines.
Although the setup can vary from project to project, the initial setup can be generalised in the following steps:

- fork the repository
- clone your fork locally
- add the original repository as an upstream for synchronisation purposes
- make sure it builds
- start contributing

When I'm trying something for the very first time, I find it easier to start over when I execute one of the steps incorrect.
And yes, I had to start over a couple of times:

The first time, I forgot to fork the repository. I got this really nice 'fatal error' when I tried to push my branch.
I threw everything away and started again.

Second time, I forgot to create a branch for my changes.
I added my test implementation to my local master and created a pull request from there.
Once the pull request was merged back into Forge and I synchronised my local copy with the upstream. After that I saw that my master was 3 commits ahead again.
This was because the commits had different SHAs.  

So depending on how your pull request gets merged, your master can get out of sync even more when you are trying to sync it.
It's easier not to add your changes to your master, but create a new branch and start from there.

So I just deleted my fork and tried again.
I just implemented another test an when my pull request was merged back, I had no problems with syncing my fork.
In the end my first successful cycle contained two PR's and I have a very clear picture in my head how an inital setup works now.

## Unforged feelings

Every project can be helped from adding a few tests, cleaning up a few lines of code and the maintainers will be extremely grateful.
To see so many fantastic reactions for even such a small contribution, well ... it made me feel pretty great!

So I will leave the small stuff for those who want to [start contributing](https://github.com/fsharp-editing/Forge/wiki/How-to-contribute-to-Forge%3F), and try something a bit bigger. ;-)
