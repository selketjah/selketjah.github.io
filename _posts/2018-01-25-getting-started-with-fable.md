---
layout: post
title: Getting started with F# Fable
category: fable
date: January 25, 2018
tags:
- Fable
- F#
---

Getting started with fable is really easy! If you use dotnet, all you need to learn are these 5 simple commands to have a Fable project up and running:

```
dotnet new -i Fable.Template
dotnet new fable -n YourName -lang F#
npm install
dotnet restore
dotnet fable npm-start
```

<!--more-->

There is some great documentation on the website with some explanation about the commands, how and when to execute them, which you can find [here](http://fable.io/docs/).

There is just one problem: I haven't been paying a lot of attention to the whole front-end scene these last few years and things have really changed. I just didn't understand what was going on behind the scene...
So when I tried to move away from the default layout that the template offers, I ran into a few problems and I didn't even know how to start fixing things. So, that is why I decided to get [Fable-Elmish with react](https://fable-elmish.github.io/react/) up and running without using the template that is available.

<!--more-->

These are the steps that I took to get to a working application from scratch. I kept the same structure as the default template has. I do have some preknowledge about certain libraries/frameworks, which made it a bit easier on me.

* I know the basics of dotnet
* I know Paket and have worked with it for the passed 2 years, so I won't go into detail about that.
* Surprisingly, I already had npm and node installed. I am not sure how having both already up and running correctly could influence the installation steps if you don't have that installed yet.

As a side note:
* I still have no idea what webpack is or how it works :-( (but I'll get there in the end)
<br>

<!-- -->

### 1. Add [Paket](https://fsprojects.github.io/Paket/getting-started.html)

### 2. Add the [dependencies](https://fsprojects.github.io/Paket/getting-started.html#Installing-dependencies)
```
source https://nuget.org/api/v2

storage:none

nuget Fable.Core
nuget Fable.Elmish.Browser
nuget Fable.Elmish.Debugger
nuget Fable.Elmish.HMR
nuget Fable.Elmish.React
nuget FSharp.Core

clitool dotnet-fable
```

### 3. Initiate the structure
* create src and public folders
* Add a new library project in the src folder

```
dotnet new classlib -n Client -lang F#
```

### 4. Add [references](https://fsprojects.github.io/Paket/getting-started.html#Installing-dependencies-into-projects)

```
FSharp.Core
Fable.Core
Fable.Elmish.React
Fable.Elmish.Browser
Fable.Elmish.Debugger
Fable.Elmish.HMR
dotnet-fable
```

### 5. Create `webpack.config.js` file in your root folder and don't forget to change the path in `module.exports` so it can find your fsproj correctly.

``` js
var path = require("path");
var webpack = require("webpack");
var fableUtils = require("fable-utils");

function resolve(filePath) {
    return path.join(__dirname, filePath)
}

var babelOptions = fableUtils.resolveBabelOptions({
    presets: [["es2015", { "modules": false }]],
    plugins: [["transform-runtime", {
        "helpers": true,
        // We don't need the polyfills as we're already calling
        // cdn.polyfill.io/v2/polyfill.js in index.html
        "polyfill": false,
        "regenerator": false
    }]]
});

var isProduction = process.argv.indexOf("-p") >= 0;
console.log("Bundling for " + (isProduction ? "production" : "development") + "...");

module.exports = {
    devtool: "source-map",
    entry: resolve('./src/Client/Client.fsproj'),
    output: {
        filename: 'bundle.js',
        path: resolve('./public'),
    },
    resolve: {
        modules: [
            "node_modules", resolve("./node_modules/")
        ]
    },
    devServer: {
        contentBase: resolve('./public'),
        port: 8080,
        hot: true,
        inline: true
    },
    module: {
        rules: [
            {
                test: /\.fs(x|proj)?$/,
                use: {
                    loader: "fable-loader",
                    options: {
                        babel: babelOptions,
                        define: isProduction ? [] : ["DEBUG"]
                    }
                }
            },
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: {
                    loader: 'babel-loader',
                    options: babelOptions
                },
            },
            {
                test: /\.sass$/,
                use: [
                    "style-loader",
                    "css-loader",
                    "sass-loader"
                ]
            }
        ]
    },
    plugins: isProduction ? [] : [
        new webpack.HotModuleReplacementPlugin(),
        new webpack.NamedModulesPlugin()
    ]
};
```

### 6. Create `package.json` file

``` json
{
  "name": "Client",
  "version": "1.0.0",
  "description": "Simple Fable App",
  "scripts": {
    "build": "webpack -p",
    "start": "webpack-dev-server",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "Author",
  "license": "ISC",
  "dependencies": {
    "babel-runtime": "^6.26.0",
    "react": "^15.6.2",
    "react-dom": "^15.6.2",
    "remotedev": "^0.2.7"
  },
  "devDependencies": {
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-plugin-transform-runtime": "^6.23.0",
    "babel-preset-es2015": "^6.24.1",
    "bulma": "^0.5.2",
    "css-loader": "^0.28.7",
    "fable-loader": "^1.1.2",
    "fable-utils": "^1.0.6",
    "loglevel": "^1.5.0",
    "node-sass": "^4.5.3",
    "sass-loader": "^6.0.6",
    "style-loader": "^0.18.2",
    "webpack": "^3.6.0",
    "webpack-dev-server": "^2.8.2"
  }
}
```

### 7. Create `index.html` in the `public` folder 

``` html
<!doctype html>
<html>
<head>
  <title>Your app name here</title>
  <meta http-equiv='Content-Type' content='text/html; charset=utf-8'>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css" />
  <script src="https://cdn.polyfill.io/v2/polyfill.js?features=default,fetch"></script>
</head>
<body>
  <div id="main-app"></div>
  <script src="bundle.js"></script>
</body>
</html>
```

### 8. run `npm install`

### 9. create `App.fs` and add it to your project file

``` fsharp
module App.View

    open Fable.Core
    open Fable.Import.React
    open Fable.Helpers.React.Props
    open Fable.Helpers.React

    open Elmish
    open Elmish.React

    module R = Fable.Helpers.React

    type Model = int

    type Msg = Increment | Decrement

    let init () =
      0

    let update (msg:Msg) count =
      match msg with
      | Increment -> count + 1
      | Decrement -> count - 1

    let view model dispatch =
      R.div []
          [ R.button [ OnClick (fun _ -> dispatch Decrement) ] [ R.str "-" ]
            R.div [] [ R.str (sprintf "%A" model) ]
            R.button [ OnClick (fun _ -> dispatch Increment) ] [ R.str "+" ] ]

    // App
    Program.mkSimple init update view
    |> Program.withReact "main-app"
    |> Program.run

```

### 10. add `yourapp.sln` file in your root folder

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 2012
Project("{f2a71f9b-5d33-465a-a702-920d77279786}") = "Client", "src\Client\Client.fsproj", "{25053F1A-0F95-4CFD-994B-F87F81670C91}"
EndProject
Global
	GlobalSection(SolutionConfigurationPlatforms) = preSolution
		Debug|Any CPU = Debug|Any CPU
		Release|Any CPU = Release|Any CPU
	EndGlobalSection
	GlobalSection(ProjectConfigurationPlatforms) = postSolution
		{25053F1A-0F95-4CFD-994B-F87F81670C91}.Debug|Any CPU.ActiveCfg = Debug|Any CPU
		{25053F1A-0F95-4CFD-994B-F87F81670C91}.Debug|Any CPU.Build.0 = Debug|Any CPU
		{25053F1A-0F95-4CFD-994B-F87F81670C91}.Release|Any CPU.ActiveCfg = Release|Any CPU
		{25053F1A-0F95-4CFD-994B-F87F81670C91}.Release|Any CPU.Build.0 = Release|Any CPU
	EndGlobalSection
EndGlobal

```

### 11. run `dotnet restore`

### 12. run `dotnet fable npm-run start` in the `src/Client` folder. This creates bundle.js and bundle.js.map files in public folder.