---
layout: post
title: F# Fable 2.0 -> 2.1
category: fable
date: December 18, 2018
tags:
- Fable
- F#
---

This morning one of my colleagues ran into a weird error when trying to build one of our web applications with Fable:

> ERROR in ./src/*/*/*/*.fsproj
Module build failed (from ./node_modules/fable-loader/index.js):
Error: Cannot find module 'fable-compiler'

At first I was very confused because as far as I could tell, fable-loader didn't use a module called fable-compiler.

But then I remembered something from Twitter: there were plans to eliminate the dotnet cli tool in the next Fable release and replace is with a javascript module again. Yeey for reading Twitter!?

<!--more-->

## Steps to update to Fable 2.1 (from Fable 2.0):

### Update yarn

Add ´fable-compiler´ and ´npx´ and upgrade ´fable-loader´ to the latest version.

```
yarn add fable-compiler --dev
yarn add npx --dev
yarn upgrade fable-loader@latest

```

### Update paket

Remove ´clitool dotnet-fable´ from your paket.dependencies and paket.references

### Update build scripts

Instead of using the cli tool, you need to update your FAKE5 script to work with npx or yarn

```
Yarn.exec "npx webpack --config whatever/the/path/is/to/webpack.config.js"  (fun o -> { o with WorkingDirectory = "whatever/the/path/is/to/client.fsproj" })
```

### Links
* [fable-loader usage](https://www.npmjs.com/package/fable-loader#usage)
