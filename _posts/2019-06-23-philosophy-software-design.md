---
layout: post
title: A Philosophy of Software Design by John Ousterhout
category: books
date: June 23, 2019
tags:
- books
---

Since I mentioned this book during [my interview](https://developeronfire.com/podcast/episode-421-gien-verschatse-choosing-your-way) with [Dave Rael](https://twitter.com/raelyard) for the podcast [Developer on fire](https://developeronfire.com/), I thought it was time to put my favorite quotes of the book online.

`A Philosophy of software design` looks at the creation of software through the lens of complexity in your system.
This book is very small, only 200 pages, so don't expect an in depth explanation of every topic in it. 
It covers the basics of every topic and it is up to you to venture out and find a more in-depth book about one of the topics in it.

> The most fundamental problem in computer science is problem decomposition: how to take a complex problem and divide it up into pieces that can be solved independently. (Location 198)

<!--more-->

<br>

### 1 Introduction
> the greatest limitation in writing software is our ability to understand the systems we are creating. (Location 258)

### 2 The Nature of Complexity
> Complexity is anything related to the structure of a software system that makes it hard to understand and modify the system. (Location 339)

<br>

> Change amplification: The first symptom of complexity is that a seemingly simple change requires code modifications in many different places .

<br>

> Cognitive load: The second symptom of complexity is cognitive load , which refers to how much a developer needs to know in order to complete a task. (Location 369)

<br>

> Sometimes an approach that requires more lines of code is actually simpler , because it reduces cognitive load. (Location 379)

<br>

> Unknown unknowns : The third symptom of complexity is that it is not obvious which pieces of code must be modified to complete a task , or what information a developer must have to carry out the task successfully. (Location 384)

<br>

> An obvious system is one where a developer can make a quick guess about what to do , without thinking very hard , and yet be confident that the guess is correct. (Location 399)

<br>

> a dependency exists when a given piece of code cannot be understood and modified in isolation ; the code relates in some way to other code , and the other code must be considered and / or modified if the given code is changed. Obscurity occurs when important information is not obvious. Complexity comes from an accumulation of dependencies and obscurities. (Location 406, 423, 446)

### 3 Working Code Isn’t Enough
> Most programmers approach software development with a mindset I call tactical programming . In the tactical approach , your main focus is to get something working, such as a new feature or a bug fix. The first step towards becoming a good software designer is to realize that working code isn’t enough. Your primary goal must be to produce a great design, which also happens to work. This is strategic programming. (Location 457, 482, 485)

<br>

> I suggest spending about 10 – 20 % of your total development time on investments. This amount is small enough that it won’t impact your schedules significantly , but large enough to produce significant benefits over time. (Location 500)

### 4 Modules Should Be Deep
> most important techniques for managing software complexity is to design systems so that developers only need to face a small fraction of the overall complexity at any given time. (Location 553)

<br>

> we think of each module in two parts : an interface and an implementation. (Location 564)

<br>

> The interface to a module contains two kinds of information : formal and informal. (Location 582)

<br>

> An abstraction is a simplified view of an entity , which omits unimportant details. (Location 597)

<br>

> The best modules are deep: they have a lot of functionality hidden behind a simple interface. (Location 623)

<br>

> a shallow module is one whose interface is relatively complex in comparison to the functionality that it provides. (Location 660)

<br>

> classitis, which stems from the mistaken view that “classes are good , so more classes are better.” (Location 685)

## 5 Information Hiding (and Leakage)
> The most important technique for achieving deep modules is information hiding . This technique was first described by David Parnas1 . The basic idea is that each module should encapsulate a few pieces of knowledge , which represent design decisions. (Location 729)

<br>

> The hidden information includes data structures and algorithms related to the mechanism . It can also include lower - level details such as the size of a page, and it can include higher - level concepts that are more abstract , such as an assumption that most files are small. (Location 736)

<br>

> In temporal decomposition , the structure of a system corresponds to the time order in which operations will occur. (Location 774)

<br>

> When designing modules, focus on the knowledge that’s needed to perform each task , not the order in which tasks occur. (Location 784)

<br>

> Whenever possible , classes should “ do the right thing ” without being explicitly asked . Defaults are an example of this. (Location 876)

## 6 General-Purpose Modules are Deeper
> The most important (and perhaps surprising) benefit of the general - purpose approach is that it results in simpler and deeper interfaces than a special - purpose approach. (Location 923)

<br>

> What is the simplest interface that will cover all my current needs? (Location 1001)

<br>

> if you have to introduce lots of additional arguments in order to reduce the number of methods, then you may not really be simplifying things. (Location 1006)

<br>

> If you have to write a lot of additional code to use a class for your current purpose , that’s a red flag that the interface doesn’t provide the right functionality. (Location 1011)

## 7 Different Layer, Different Abstraction
> A pass - through method is one that does little except invoke another method, whose signature is similar or identical to that of the calling method. (Location 1035)

<br>

> In order for an element to provide a net gain against complexity , it must eliminate some complexity that would be present in the absence of the design element. (Location 1196)

## 8 Pull Complexity Downwards
> Most modules have more users than developers, so it is better for the developers to suffer than the users. (Location 1208)

<br>

> Another way of expressing this idea is that it is more important for a module to have a simple interface than a simple implementation. (Location 1209)

<br>

> Thus , you should avoid configuration parameters as much as possible . Before exporting a configuration parameter , ask yourself : “will users (or higher - level modules) be able to determine a better value than we can determine here?” (Location 1246)

<br>

> Ideally , each module should solve a problem completely; (Location 1249)

<br>

> Pulling complexity down makes the most sense if (a) the complexity being pulled down is closely related to the class’s existing functionality , (b) pulling the complexity down will result in many simplifications elsewhere in the application , and (c) pulling the complexity down simplifies the class’s interface. (Location 1252)

## 9 Better Together Or Better Apart?
> the act of subdividing creates additional complexity that was not present before subdivision ... Some complexity comes just from the number of components. Subdivision can result in additional code to manage the components. Subdivision creates separation. Subdivision can result in duplication. (Location 1271, 1272, 1274, 1275, 1281)

<br>

> Here are a few indications that two pieces of code are related: They share information; They are used together; They overlap conceptually , in that there is a simple higher - level category that includes both of the pieces of code. It is hard to understand one of the pieces of code without looking at the other. (Location 1283, 1284, 1284, 1287, 1289)

<br>

> In general, the lower layers of a system tend to be more general - purpose and the upper layers more special - purpose. However, length by itself is rarely a good reason for splitting up a method. When designing methods, the most important goal is to provide clean and simple abstractions. (Location 1341, 1488, )

<br>

> Each method should do one thing and do it completely. (Location 1500)

<br>

> ( a ) someone reading the child method doesn’t need to know anything about the parent method and ( b ) someone reading the parent method doesn’t need to understand the implementation of the child method.

<br>

> The decision to split or join modules should be based on complexity. (Location 1534)

----
Version of the book

[The philosophy of software design, John Ousterhout, kindle edition](https://www.amazon.com/Philosophy-Software-Design-John-Ousterhout-ebook-dp-B07N1XLQ7D/dp/B07N1XLQ7D/ref=mt_kindle?_encoding=UTF8&me=&qid=1561306872)