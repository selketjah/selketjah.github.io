---
layout: post
title: Aiming for Successful Software
category: successful-software
date: February 05, 2026
tags:
- software
---

A company I consulted at had some issues with their synchronisation. The synchronisation between the microservices of their software system had not been implemented according to the users needs. On top of that, it had a lot of failures too. The users would add or change information on one UI screen, but it would not show up or showed up hours later on other UI screens. Because of that the trust in the software system had vanished. Too many failures during synchronisation without any notifications and bad requirements resulted in the users no longer trusting the software system.

<!--more-->

Since the users needed software they could trust, they bought their own applications, and used those instead. These applications had functionality very similar to their internal software. This was not good for anyone:

- The company had to pay for software, while it had software that could already do all of those things.
- The software teams needed to create more synchronisations (which they weren’t very good at implementing) and spend hours implementing functionality that nobody was using. Time and money that didn’t deliver value.
- The business had to swap between multiple applications constantly, because the software they purchased didn’t have all the functionality required. They still needed to use the internal software system too but didn’t trust them causing tension between business and IT.

I came up with a campaign to re-establish trust while fixing the failure issues, but re-establishing trust is a slow process.

This is just one company, and the software is internal, so no big deal in the grand scheme of things. But I have seen this happen at other companies too. They replace their current applications or software tools with new ones because it did not do what they were promised it did, it was too hard to use, too many error messages, … Whatever the reason, the software was just not giving them a successful experience. The software was unsuccessful. 

As a business we want to be successful. In order to do that, we need our software to be successful too. But what does it mean, to have successful software? In this blogpost, I will go over the definition of successful software, and the principles and practices to help you achieve that.

## What is successful software?

The success of software depends on a mix of technical, business, and user-centric factors:

- it delivers value over a longer period of time for multiple stakeholders.
- it is stable and reliable: it is healthy.
- it can evolve over time.

### Successful software delivers value.

First and foremost, software is valuable when it has value to its users. Software is there to help people deal with their problems. When I thought what I wanted to do career wise, I knew I wanted to help people. I chose creating software as a way to do that. Software is supposed to make the user’s life easier. It seems that somewhere along the way, we have forgotten that.

But successful software isn’t only valuable to the users. It is also valuable for the company. Companies exist to make money. Software makes you money directly, or it supports the company in making money indirectly. Companies which sell software, have both.

### The software is healthy

Software has to be healthy, which means software has to be stable and reliable.

Stable software can run consistently without crashes, or performance issues. Unfortunately, that is almost impossible, but when those do happen, the software can deal with them gracefully. Our example of the synchronisation not working without any notifications of what went wrong earlier is a good example of unstable software.
As far as our infrastructure goes, most of our software runs in the cloud now, and we don’t have to worry (much) about it any more. That is a good thing, although when it goes wrong, it goes really wrong. But we still need to be able to deploy to that infrastructure. So stable software also means that we can deploy in a timely and safe manner.

Reliable software means the software does what it is supposed to do from a domain logic perspective. Software should perform its functions consistently and according to its stakeholder’s expectations. We, the users of the software, should not be surprised when using our software because that is not what we expected would happen. When software surprises us too much when we are using it, we lose our trust in it. Once the trust is gone, we either look for other solutions or we feel we need to protect ourselves against unexpected results.

### The software can evolve over time

The market is not a fixed thing, it changes all the time. New companies arise, other companies fold, the wants and needs of the customer changes, etc. When the market changes, the company has to change with it. It has to revisit and adapt its goals, its business plans, its focus. That affects the software. So software is not a fixed thing. In order for software to be successful, it has be able to evolve with the company and the market. Removing features that are no longer needed, adding features that are desired, and changing how features work. 

Technology is also a volatile market. Sometimes technological changes make certain features possible. In order to stay ahead, we need to evolve the software from technical perspective too. Frameworks and libraries need to be up to date to access to the latest features they have to offer. But while somethings inside your software system must evolve, some of it needs to stay stable in order to remain maintainable.

Successful software there is both evolvable and maintainable.

## How to make your software successful?

What we want is successful software, but how do we get there? There are a few things that you need in order to build successful software:

- alignment with the business,
- operational excellence,
- resilient design, architecture and modelling,
- feedback loops,
- culture, team and organisation.

### Business alignment

You need to have a deep understanding of your business to be able to deliver valuable software. Your software needs to align with the strategic and financial goals of the company. I often see a disconnect there, specifically between the company and the software strategy. e.g. the development side plans to refactor heavily for the next year while the business plans to take on some big new investment like creating 3 new products for the next 5 years. Or one of the teams wants to use [Kafka](https://kafka.apache.org/), but they can’t explain why that is valuable for the company. These are misalignments between the business and the software. There are ways to avoid this misalignment. Domain-Driven Design (DDD), a design discipline, helps you align your software better with the business. 

### Resilient design, architecture and modelling

When we look at a business, e.g. finance, there are a lot of business processes, rules and policies in place. It can get complicated very fast when we try to design successful software for it. Trying to design a single model that can express every aspect of a problem will lead to a lot more problems. We need to design good domain models that solve a specific problem. In order to deal with this we design boundaries, referred to as bounded contexts in DDD. You can see them as a tool to manage complexity. They allow us to refine our domain models within the bounded context, without having to worry how that impacts our entire software system. Designing good bounded contexts is not  easy, but it gives our software system great resilience and adaptability. They become modules in a monolith or microservices in our architecture, and help us evolve our software. 

### Operational Excellence

Features only deliver value when they are in production, available for your customers to use. Operational Excellence ****is a set of practices that aim to maximise value delivery in software development. For software teams this means building, deploying, and maintaining systems in a way that enable high performance, and continuous improvement.

Testing is in my opinion the most important practice of operational excellence. Implementing tests help software developers to catch issues early, reduced human error, and gives them the confidence to change code while implementing new features. There are different types of tests that help you with different things:

- Unit tests: test individual units of code (e.g., functions, methods, or classes) in isolation to ensure they work as expected.
- Integration tests: test the interaction between multiple components and/or systems (e.g., databases, APIs, services) to ensure they work together correctly.
- End-to-end tests: test the entire application workflow from the user’s perspective, simulating real-world usage. Often there is some manual testing done by QA people for end-to-end testing.

Another close second practice that helps software teams with high performance and continuous improvement is software delivery automation. Software delivery automation is often referred to as “[the CI/CD Pipeline](https://about.gitlab.com/topics/ci-cd/cicd-pipeline/)” and uses automated testing, continuous integration (CI) and continuous delivery (CD) to speed up delivering value to production in a safe way. It speeds up processes, and frees up your teams to focus on innovation. The [DORA](https://dora.dev/guides/dora-metrics/) metrics are a great starting point for measuring how well you can deliver software.

There are a lot more practices out there like monitoring, caching, infrastructure as code, etc. Making sure software teams are high performing and can continuous improve is a job all on its own (DevOps). Operational excellence is not a one-time effort—it’s about learning, adapting, and evolving over time.

### Feedback loops

Successful software delivers value to its customers. We are not always sure if an idea will be valuable for our customer though. Which is why we need feedback loops. A lot of companies have feedback loops at the end of the development cycle, where everybody involved has already done all the work. Slow feedback loops like this require our ideas to be more correct because it is more costly if they are not. Yet, we don’t have the necessary information that can tell us that.

What we need are faster feedback loops and short iterations. Fast feedback and short iterations allow you to learn, improve and adapt earlier and therefore cheaper. It starts with validating our idea. First, we can see what is the minimum valuable thing that we can do instead of implementing everything straight away. Secondly, we want to get our idea in front of our users/stakeholders as fast as possible to get feedback on it. We can make mock-ups, show them and see what our users think of them. 

Once we have established that it is worth investing in our idea, we can start designing it. Collaborative modelling is good way to get feedback earlier. So is prototyping. Besides prototyping and collaborative modelling, there are many feedback loops possible that give us important information. Tests are a form of feedback that tell us whether or not we are breaking anything while we are changing our code. A/B testing is a way to do user research on which of our solutions is more effective at solving our problem.

### Culture, teams and organisation

None of the previous items can be achieved without a healthy company culture in place. A “stay in your lane” attitude will make it impossible to align with the business. If teams have to jump through hoops to get their software licenses approved, operation excellence will suffer. When teams are designed according to skill (product managers, front-end, back-end) your design will be suboptimal.

I have seen all of these at companies. A company needs a culture that encourages continuous learning, with financial support behind that encouragement. It needs a culture that empowers teams, where there is room for experiments and learning from failure in a healthy way.

## Conclusion: building software that lasts

The anecdote I started with is a reminder of what happens when software fails to meet the basic expectations of its users. This isn’t just a single occurrence; it’s an industry wide problem. I see unsuccessful software everywhere I look. And it isn’t just annoying the users, it is costing companies money, trust, and opportunities.

Successful software is not just about writing code that works—it delivers lasting value, is healthy, and can adapt to change. But achieving this requires more than technical prowess. It demands alignment - ensuring your software strategy mirrors your business goals. It calls for resilience - designing systems that can absorb change without breaking. It relies on operational excellence - automating delivery, testing rigorously, and monitoring continuously. And it thrives on feedback - shortening the loop between idea and validation, so you can learn, adapt, and improve faster.

Most importantly, success is rooted in culture. A culture that fosters collaboration, empowers teams, and embraces learning - even from failure - is the bedrock of software that doesn’t just function, but flourishes.

So, ask yourself: *Is your software set up for success?*

-------------

This blogpost is sponsored by [Aardling](https://www.aardling.eu). Struggling with software that doesn’t deliver value, crashes unexpectedly, or can’t keep up with change? We specialise in helping teams and businesses transform their software from a source of frustration into a reliable, valuable, and adaptable asset. Whether you’re launching a new product, modernising legacy systems, or trying to align your tech and business strategies, We’d love to discuss how we can work together. [Get in touch to start a conversation](https://aardling.eu/en/contact). 