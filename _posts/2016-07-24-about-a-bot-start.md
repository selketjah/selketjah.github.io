---
layout: post
title: About a bot [Part I - How it started]
tags:
- F#
- mentorship
---

So, in the beginning of the year I did a remote F# mentorship with [Mathias Brandewinder](http://brandewinder.com/). 
This is the first blogpost that will be part of a serie about the mentorship.

It was a super fun experience, but organising remote programming sessions does come with some struggles. 
In this blogpost I will cover the general setup of the mentorship and the issues we came across during it.

<!--more-->

## Strangers on a train

For some people it is very easy to get to know others and make friends. I am not one of those people.
I knew Mathias by 'reputation', but we hadn't seen one another in person.
Before the sessions started, we did a small introduction via e-mail, but when they started, we went 'straight to work'.
Although I loved the level of focus, this is one of the things I recommend doing different.
Take a bit of time during that first session to have a general conversation if you are not acquainted with one another to break the ice.

Having a camera up and running during the sessions is also a big help to make them better (read less awkward ;-)).
During the fourth there was a video feed. We hadn't been able to get the video working up until then (more about that later), 
but I noticed that it made it a lot easier for me to speak up.

## Hello, can you hear me?

The most repeated (and extremely frustrating) question during the entire sessions. Setting up your environment so that you can talk to each
other and share your screen was actually a difficult process in the beginning.

We tried a variety of ways to do it:
First, there was Google Hangouts. It hates us, I swear!
Althought we both had successful hangouts with other people, we did not get this to work _at all_. Why? Well, because.

Second, I looked into ScreenHero because I heard good things about the tool. Unfortunatly, at that point in time they were
migrating into Slack and I couldn't check it out. Right now the migration is finished, but it was a full Slack integration
and you cannot use the product separately anymore. How exactly it works right now, I don't know.

Next up was Teamviewer. Teamviewer is a collaboration tool and is available for most operating systems and is free for private usage.
It should be able to do audio, video and screen collaboration, but we did not get the audio and video to work. To be honest, after all the trouble
we had with the other tools, I wasn't in the mood anymore to try to get it to work.

We ended up with a combination of Teamviewer and Skype.
You have screen sharing on Skype, but not screen collaboration (as far as I know). It's important that both parties have control
over the screen. Even if you don't type, it's very handy to be able to point or select some code when asking a question.

Having to tackle these kind of problems is very frustrating, but it did have an upside too.
It helped with the 'strangers on a train'. There is something about cursing together at Google Hangouts that breaks the ice and takes away
some of the nerves you have. ;-) 

## Let's get this party started

Besides finding the right tools for the job, finding the right moment to have a session is the second hurdle
you have to take. 
Although we didn't have difficulties with this, I can imagine this being a bit of a struggle.
We were living in different time zones, so when we e-mailed about setting up the sessions, we always
included both times. Very handy!
Mathias mailed me some possible moments in which we could hold the sessions, we picked one and stuck with it.

The first 4 sessions were a general introduction into F# itself, aka getting into the groove.
I will dedicate the next blogpost about those sessions, so I will not go into detail right now.

After that, we had 6 sessions where we worked on a project together. We made a twitter quiz bot! So cool :-D
Because we hadn't covered all interesting F# topics yet (we still haven't), the homework continued.
Going over it ate up a lot of our project time, so we introduced a 15 minute time box to answer the questions I had 
during the week about it. After the 15 minutes were up, we continued on the project.
In the coming posts of this series I will go into more detail of the project.

One thing we agreed upon during the retrospective was that one hour wasn't long enough to make serious progress on the 
bot, and the sessions never ended after one hour (we were having too much fun). It would be better to find a different format for the project sessions.
You could do 4 sessions of 2 hours, or 5 of one and a half... 

## How did we do?

Seeing how this was the first time for both of us to participate in a mentorship, we knew it would be a trial-and-error approach.
I am actually very happy with the way the mentorship went: pretty much everything was trial, but we had very little error.
Still, it is important to know where things could be improved for mentor and mentee, so we had two retrospectives: 
one after the first 4 sessions, before we started the project and the other at the end of the mentorship.

The first one was initiated by Mathias and was via e-mail. I really liked that.
It gave me some time to think about the answers and how to formulate my feedback in a way that didn't sound negative.

The second retrospective was organized as an eleventh session. We both thought about what we wanted to ask (or say) and
send the questions upfront to each other so we had some time to formulate the answers. Open and honest retrospectives can be 
a hardship sometimes, so preparing for it can make all the difference.
Below you can find our questions for inspiration.

## Questions

My questions:

1. What did we do well during our sessions that you would recommend to others?
2. What did we do well during our sessions that you might forget to mention when blogging/talking about the sessions?

3. What would you have done differently?
4. What do you think I would want you to do differently?

5. What is the most important thing that you learned from our sessions?
6. What do you think is the most important thing I learned?

7. Did you ever get the impression that I had not prepared my homework good enough?
8. Did you ever get the feeling I wasted your time with a question/conversation?
9. Did you ever get the impression that my questions were due to insufficient search for the answer?
10. If you could give me one advice for the future which would improve me as a developer, what would it be?

Mathias' questions:

- Was it prepared enough on my side? I think it's valuable to think through problems together live, but it can also slow things down, would more guidance have been better?
- If a friend asked you to take a look at their F# code, would you be comfortable with it? What would be missing?
- If a friend asked you whether it would be worth their time to do a similar mentorship with me, what would you ask them and tell them?
- If a friend asked you to mentor them on F#, how would you change the "program"?
- Was there anything surprising, in a good or bad way, over the 10 weeks? Was it different from what you expected?
- Based on the initial description/commitment, did you expect something that didn't happen/was missing?
- What type of person do you think I should do this with? Who would not get much out of it?
- Do you think you will get stuck on the bot project? Why/how/where?
- What are the 3 most valuable things you learnt over the 10 weeks? Will you do anything differently in the future?
- Any input on my attitude, on the content, on the format!

## What comes next?

In the next part of the series, I will dig a little deeper into each session.
First I will go into the 4 'Into the groove' sessions and after that I will go into detail about the quiz bot!