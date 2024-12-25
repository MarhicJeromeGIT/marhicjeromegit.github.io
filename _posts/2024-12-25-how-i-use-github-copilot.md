---
layout: single
title: How I use GitHub Copilot
date: 2024-12-25 04:07 +0000
author_profile: true
---

Since the release of ChatGPT more than 2 years ago, I have felt a strong disconnect with the opinions on HackerNews about AI. It really feels like an Anti-AI (especially anti-OpenAI) echo chamber, neverendingly predicting the advent of AI winters, always repeating the same arguments (usually some flavor of "it's not intelligent", "what is AGI?", "how can you trust it?"). Well, given that the generated code compiles, the tests pass and the program works as expected, I'm not sure what there is to complain about. I feel that HN is about as wrong about AI as it was about cryptocurrencies. Eventually, I mostly stopped reading the comments, I just use it as a link aggregator now.

So I'm saying it proudly here instead, as a webdev ChatGPT and GitHub Copilot made me a good 50% more efficient. I think people that complain just don't use it properly - learn to prompt ffs, it can't read your mind. If you don't know what you are doing and what result you even expect, you're unlikely to get something satisfying.

And from my experience, 0.1x programmers will never admit to their own failings. Whether it's in online forums or in sprint retrospectives, the reason for failure is always external (those managers! the API!) and never their own inadequacies. So with AI, they will blame the tool for not working, instead of realizing they did not use it properly.

I'll concede however that some use cases are more suitable than others, personally I found I get better results with typed languages, notably in Go, since you can see at a glance whether the generated code is at least syntactically correct, and it helps the model plug into your existing program. Also, the current ChatGPT 4.0 version doesn't seem to know much about Go 1.23 changes and will usually default to older Go constructions, but that's my responsibility as a programmer to stay up-to-date about it and make sure I get the result I want. I'd say this is my value add now.

So these days, an usual development loop goes like this: I have a goal in mind (let's say for instance, I don't want the handler to take a filepath, but instead whatever the file content is). I'll add the relevant code to the context with "Add File to Chat" - I can usually add the whole file as I try to not make them too long - and ask my question plainly and politely "please change the handler so it takes a list of strings from the file, instead of a filepath". That's normally enough to get going, and a cursory look at the changes is enough to validate that I got the result I expected. Oh nice it even updated the comments, LGTM! Another pass to update the tests, and I got a PR ready in 5 minutes instead of maybe 20 if I had done it by myself?

Did I say "a list of strings"? I've been working on and off on this "crossword generator" project, and maybe it's time to share a first preview:
![My Crossword Project](/assets/images/crossword_wip.png)

So what we have here is a Vue.js + TailwindCSS app (The frontend including the grid design was entirely generated by ChatGPT). And the "Solve Crossword" button calls the Go backend, which runs some backtracking algorithm - I wrote an ["exact cover solver library"](https://github.com/goverture/exact_cover) for that use - until it found a solution. It's pretty fast, the search itself takes around 5 seconds if I start from an empty 15x15 grid (loading the word list every time is a bit slow though, so I'm going to ask Copilot to load it once and for all!). I have no plan to make the crossword solver open source though. I have some thoughts about open source that I might blog about later on!

Still a lot of work to do (and not the funnest part unfortunately) before I can release it. First step would be to get a decent word list!

Anyway, that's it for the blog post. Even though I don't use Copilot to generate the text, I'll ask it to fix the typos :)