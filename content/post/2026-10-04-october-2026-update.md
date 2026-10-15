---
author_profile: true
date: "2026-10-04T00:00:00Z"
title: October 2026 Update
draft: false
---

Walking in downtown Ho Chi Minh City these days I feel a bit nostalgic. I am brought back to 6 years ago, when I was staying there during Covid. Streets were much more quiet back then ! I have fond memories of riding my rental scooter along the canals and stopping by in random cafes. As I was waiting for borders to reopen so I could go live in Japan, as I had been dreaming to for a number of years, I met my wife and somehow 6 years later, I am still here, now married with two kids. You could say social distancing didn't sit well with me.

Sometime I think about my early 30s as being like a quantum particle in a superposition of "potential outcomes", not yet observed, a set of more or less improbable futures ranging from desirable like winning the lottery and retiring, to bad, like being in prison or dead. And when my girlfriend got pregnant it suddenly "collapsed" into one observed state, admittedly the best possible, and also somehow the most probable. No more uncertainty or unrealized potential, it doesn't get better than that.

It has been 3 months without a post, we went back to France during summer, I vibe-coded a couple of projects (a PBF based water simulation, after reading about OpenAI's solving Navier-Stokes equations...). It all became so easy there is nothing worth speaking about. It's like art I guess, modern art objectively sucks because you don't get the feeling that someone spent time making it compared to the traditional painting or sculpting of yore.

I'm kind of surprised and thankful for every day that passes where I am employed. Somehow I like the state of "having a job", and it occasionally brings some interesting projects along with a regular salary. I've been repeatedly questioning what value I can add over the model, apart from a meat proxy (common sense ? some kind of "taste" ?).

Last Friday was a rare one, I got this support ticket. Without giving too much details, the issue was losing some state across app restarts. I passed the ticket to Sol 6.1 and let it rip, only to come back and see its solution consisted in 10 files changed including a new column in some db table... Smelly ! I guess it had no way of knowing, but it's obvious to me that we don't want this column in the db, it's not a property of that table, it's just a hack that got added at some point. We absolutely don't want to make it "official" by giving it it's own db persistence ! Alright, so I had to do the fix myself. A bit of reading and searching later, and I got a nice, 10 lines solution that did not require a schema change. Felt like a win over the model, but it has become rare !

Trying to prepare for the future, I decided to attend some tech events in Saigon in order to go out of my comfort zone for once and maybe do some networking. Saturday I attended [XConf Lite by Thoughtworks](https://www.thoughtworks.com/about-us/events/xconf/2026/xconf-apac-2026---vietnam). Kind of mixed feelings, it was hard to understand who was the target of the talks. Actually I kind of disagreed with their content itself. One talk was about how a new employee started "producing" after 3 days by using AI summarization tools (Jira Rovo, Slack bot) to read doc etc. Another was about an automated incident response tool. Yes you can onboard faster and yes, you can auto resolve incidents, but in my opinion it's kind of a waste. Onboarding is your chance to get to know your colleagues, so take your time to ask questions, figure out who wrote which doc, what they are working on now, who left the company ? Same for the incidents, you can merge a fix PR created by a bot, but the war room is a shared experience with colleagues that can bring the team together and shine light on some corners of the infra.

I talked a bit to a couple of people, so at least it got me out of my comfort zone. I might try different kinds of events in the future, maybe some hackathon, will see.

I've also been vibe-coding a Miro clone. It is based on Excalidraw, with some websocket and pubsub for live collaboration over a board, persistence, SSO... The hard step will be to get the company to switch ! Miro apparently costs 20$ per seat per month so it would lead to some nice savings, I will see if I can push it.

Wrapping up for today !

