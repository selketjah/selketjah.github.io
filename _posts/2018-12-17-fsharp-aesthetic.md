---
layout: post
title: My F# aesthetics
category: F#
date: December 17, 2018
tags:
- F#
---

I love churches, more specifically I love the architecture of a Catholic church build during the Gothic time period. I know, a weird way to begin an F# blogpost for the fsadvent, but bear with me for a moment.

I have tried to explain by enthusiasm for churches, cathedrals and such to many people but I have rarely succeeded in doing so. But still, I will keep trying. 

Imagine a church that you visited, perhaps Notre Dame de Paris? Picture yourself standing in front of her.

In the middle of the building you have double doors, which divide the entire building into two halves. One tower on the left, one tower on the right. <!--more--> Each tower has three levels: first level has a Gothic arch, which you could fold in two and you would have a perfect match. For the other levels you have the same symmetry: a window on the left, a window on the right. You start moving forward to entry and you look at the door in more detail. The door is surrounded by statues: for every statue on the left, you will find a similar one on the right. You walk through the door and onwards to the altar in front of you. As you walk through the hallway, you see that symmetry again: for every pillar on the left, you will find a pillar on the right. For every stained-glass window on the left, you will find one on the right. For every shrine on the left, you have a shrine ... Ah... Well, almost always a shrine on the right I guess.

The harmony and predictability of that building is so strong that the outside world fades away and a tranquility comes over me from walking through it. That applies to most the Catholic churches I have visited. I could cut any of them in half and end up with two similar halves.

That is what it should feel like when walking through your code: a strong sense of harmony that brings tranquility to the reader of it, 99% predictability, 1% deviation.

### What are aesthetics anyway?

When you mention aesthetics, most people think about whether or not something is beautiful. But on a more abstract level, aesthetics is about offering a set of guidelines that will allow you to create beauty.

>  An underlying principle, a set of principles, or a view often manifested by outward appearances or style of behavior [free dictionary](https://www.thefreedictionary.com/aesthetic)

> (noun) A set of principles underlying the work of a particular artist or artistic movement. [Oxford dictionary](https://en.oxforddictionaries.com/definition/aesthetic)
    ‘the Cubist aesthetic’

<br>

We stare at our code all day long, yet we seem to care so very little about what makes it pleasant or beautiful to look at. So this is my fsadvent present for the F# software developers this year. A set of principles that will guarantee beautiful code ... 99% of the time ;-)

### Whatever is on the left ...

... must be on the right. In general, the more symmetry something has, the more beautiful we find it.
So, make your code symmetrical:

* anything with 2 or less elements, goes on one line
* anything with more than 2 elements, goes on separate lines
* spaces before and after symbols (f.e. `:`, `*`, `+`, `;`)


```fsharp
type Behavior = Naughty | Nice // Don't write the first |

type Nickname = string

type Elf = { FirstName : string ; LastName : string }

type Child =
    { FirstName : string
      LastName : string
      City : string
      Behavior : Behavior }

// This is a:
// discrimated union, with 4 union cases.
// Each union case has a Tag, some have a component type too.
type Character =
    | Santa // Always write the first |
    | Elf of Elf 
    | Deer of Nickname
    | Child of Child

```

Principle #1 of my code: balance your types with spaces and new lines

### Creating harmony in your code

As you saw in my code sample above: I am a 4 spaces sort of person, if that is a thing... Always have been. I would prefer a tab, but those have gone out of style, so I had no choice but to embrace the 4 space equivalent of it.

```fsharp
type Tree =
    | Leaf of int
    | Branch of (Tree * Tree)

let tree =
    Branch(
        Leaf(1),
        Branch(
            Leaf(2),Leaf(3)))

let rec sum (acc : int) (tree : Tree) =
    match tree with
    | Leaf(x) -> acc + x
    | Branch(left,right) ->
        let sumleft = sum acc left
        sum sumleft right

sum 0 tree;;
```

The reason I like tabs is because it gives you a separate symbol to add meaning to your code. Like you have punctuation marks in spoken languages, you had a set of marks in programming languages that hold meaning and a tab was part of that. Without that, I felt a bit lost in my F# code. I use to add 2 empty lines between top level functions, but when I swapped back to tabs (well, the 4 space equivalent), I noticed the need to group like that went away because I could take the tab into account to figure out the grouping.

Rules for harmony
* group logic that belongs together by adding an empty line
* level indication with tabs (yes yes, 4 spaces)
* code colors must be in harmony (Although I am still swapping Color Themes in vscode every couple of months because I haven't found the right one yet)

That way I can roughly understand the flow of my code 2 meters away from my desk. 

So, principle #2 of my code: design your code to understand it 2 meters away from your desk.

### Parameters

```fsharp
let example name age birth city = () // A - best case scenario

let example (name : string) (age : int) (birth : DateTime) (city : string) = () // B - best case scenario on the other end

let example (name : string) age (birth : DateTime) city = () // C - try to avoid

let example (name : string) (birth : DateTime) age city = () // D - grouped

```

One of the cool things about F# is [type inference](https://docs.microsoft.com/en-us/dotnet/fsharp/language-reference/type-inference). Unfortunately, it is not infallible, sometimes conflicts occur and you need to specify your type. 
I try to group them and put the parameters with type annotation first.

Principle #3: be consistent in your function signatures.

### Match expressions

Same as with a Discrimated Unions, if you only have two union cases in your match expression (and they are short), I write it on one line.

```fsharp
match found with Some day -> day | None -> "-"

match found with
    | Some day -> day
    | None -> "-"

match moment with
    | Yesterday ->
        ()

    | Today ->
        ()

    | Tomorrow ->
        ()

```

I try to avoid more than two lines in a [match expression](https://docs.microsoft.com/en-us/dotnet/fsharp/language-reference/match-expressions). I started doing this because of my match expressions in Elmish Fable. Your `update` function can run away easily from you there. Seeing how the readability of my code improved, I've extended this to my server-side code too.

```fsharp
let skipOrGive behavior =
    let skipHouse = ()

    let givePresents = ()

    match behavior with
        | Naughty -> skipHouse ()
        | Nice -> givePresents ()

```

Client side I create `private` functions to keep my `update` function as compact as possible, but server side I just make subfunctions in my top level function, as shown in the example above.

[J.B. Rainsberger](https://twitter.com/jbrains) talks about creating black boxes of code. And if you open the black box, you find more black boxes, and so on and so on. All the way down. I like that analogy, so:

Principle #4: create tiny black boxes of code.

### No robotic naming

For the past month I have been pondering the concept of having 5 simple rules by which the team can validate the quality of the code that we deliver or review both on a technical and aesthetical level.

So, I finally found a good name for one of my principles that I have been applying: `no robotic naming`, which means:
* no suffixes (*Repository, *Manager, *Request, *Response)
* no prefixes
* no abbreviations
* know the difference between acronym and abbreviation

This principle is not written in stone, my code example also contained an `acc` and `x`. That is just fine. This exists to make sure that I think about the concepts that I am introducing and perhaps even discover missing concepts that are hidden by these kind of naming patterns.
So, this is my last principle: no robotic naming.

### The End

Software developers like to pretend that there is this objective way to write and judge code aesthetics, but there isn't. A tab or a space often turns into a quibble...
I guess that is why it took me so long to write this blogpost... I don't want this to turn into a quible. I mean, how could I be sure that my set of principles actually made any sense?

I was lucky, I got the confirmation I was looking for a while back when I looked at the proposition of the [F# guidelines](https://docs.microsoft.com/en-us/dotnet/fsharp/style-guide/) and I discovered that the way I thought about code aesthetics, matched the draft version of the guidelines pretty closely.

Maybe yours don't. That is fine too. Whether or not you adapt them, It doesn't really matter. In the end there is really only one principle you need to remember: your code has to feel like walking through a Gothic Catholic church. Predictability and harmony, 99% of the time, 1% deviation.
