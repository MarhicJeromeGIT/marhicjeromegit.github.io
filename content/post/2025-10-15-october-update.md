---
title: "Logic riddle (October update)"
date: 2025-10-15T15:04:24+09:00
draft: true
---

> A programmer says "I have 2 kids, and the sum of their age is 4".
>
> The logician thinks and says "not enough info".
>
> The programmer adds "The eldest likes Bluey".
>
> The logician smiles and replies "Ah ! You must be using vibe coding a lot".

Alright, I've been working on a new project, [Goxy](https://github.com/goverture/goxy): an OpenAI proxy that track & limit spending. You can set an hourly limit (say 1$ per hour) and the proxy will return 429 errors when the spend reaches the limit. That lets you release LLM using projects while being confident you won't get hit with a thousand-dollar bill at the end of the month.

It's written in Go and mostly vibe-coded (from VSCode copilot), though I'm controlling the flow and trying to make piece-wise PRs. Execution notwithstanding, I think the idea is sound, I'm not aware of a way to set a hard budget limit to a given OpenAI API key, they'll just email you when you reach a preset budget but nothing prevents you to go over it. I'm kind of excited about it because I shared it in the latest HackerNews "What are you working on" thread and got 2 stars on it !

Not much else going on, I've just came back from Tokyo so here's a picture of Shibuya station ongoing construction.

![Shibuya construction](/assets/images/shibuya.png)
