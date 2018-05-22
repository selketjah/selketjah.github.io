---
layout: post
title: Adding Fulma to an existing Fable project
category: Fable
date: May 22, 2018
tags:
- Fable
- F#
- Fulma
---

About a month ago I went to F# eXchange, I wandered into a talk about Fable and Elmish, given by [Maxime Mangel](https://twitter.com/MangelMaxime).
Before you read any further, you have to know something: I don't really like front-end development. But I have to know how to do it either way, So, I sat myself down in the last row and starting listening with half an ear.

Until I heard a magical sentence:
> "We could take the benefits of the compiler and intellisense by using another project, called Fulma, which allows you to strongly type your css."

<!--more-->

I hate css. It is just one of those necessary evils that comes with the job. It is safe to say, the talk had my full attention at that point. Anything that makes it possible to avoid hard-coded class names and a lot of frustration because I make a lot of typos, is worth checking out! So I did and it is great.
I made a nice summary so I will never forget how to make the necessary evil in my job a little bit more pleasant.

## Please tell me more!

Basically, there are two ways to get started with Fulma. The first one is to use the minimal template that is available, the second is to add it manually.

Using the template it really easy:

```
> dotnet new -i Fable.Template.Fulma.Minimal
> dotnet new fulma-minimal -n MyApp [-lang F#]
```

I like easy, but I also like understanding what exactly I'm doing. So I added Fulma manually to an already existing project first.
I highly recommend that you to this manually at least once. Although templates are fantastic things to have and I am very grateful they exist, they prevent you from banging your head against a desk to deeper insights on how Fulma works behind the scenes.

## Installing Fulma in an existing project

First thing you need to do, is add `Fulma`. I know, very surprising!

```
paket add Fulma --project <your project>
```

You also need to install `Bulma` and `FontAwesome`...

```
yarn add bulma --dev
yarn add font-awesome
```

... and import them into your `main.scss`

``` css
@import "./../../node_modules/bulma/sass/utilities/initial-variables";
@import "./../../node_modules/bulma/sass/utilities/functions";

$fa-font-path: "./../../node_modules/font-awesome/fonts/";
@import './../../node_modules/font-awesome/scss/font-awesome.scss';

@import './../../node_modules/bulma/bulma.sass';
```

After that, you need to update your `webpack.config.js` file.

```js
//config entry
resolve('./../MuggleFront/scss/main.scss')

// module rules
{
    test: /\.s?[ac]ss$/,
    use: [
        isProduction ? MiniCssExtractPlugin.loader : 'style-loader',
        'css-loader',
        'sass-loader',
    ],
},
{
    test: /\.css$/,
    use: ['style-loader', 'css-loader']
},
{
    test: /\.(png|jpg|jpeg|gif|svg|woff|woff2|ttf|eot)(\?.*$|$)/,
    use: ["file-loader"]
}

```

And that's it! A few extra bruises on your forehead, but you are good to go ;-)

### package.json

```json
"dependencies": {
    "babel-polyfill": "^6.26.0",
    "font-awesome": "^4.7.0",
},
"devDependencies": {
    "bulma": "^0.7.1",
    "css-loader": "^0.28.11",
    "file-loader": "^1.1.11",
    "node-sass": "^4.8.3",
    "sass-loader": "^7.0.1",
    "style-loader": "^0.21.0"
}
```

### Info
On 22-05-2018, when this blogpost was written:
> The current version of `Fulma` is 1.0.0-beta-022

> The current version of `Bulma` supported by Fulma is 0.7.1

> The current version of `FontAwesome` supported by Fulma is 4.7.0

### Links
* [Docs](https://mangelmaxime.github.io/Fulma/)
* [Github project](https://github.com/MangelMaxime/Fulma/)
* [F# eXchange talk - Fulma starts around 15:10](https://skillsmatter.com/skillscasts/11310-elmish-get-your-dev-stack-back-under-control)