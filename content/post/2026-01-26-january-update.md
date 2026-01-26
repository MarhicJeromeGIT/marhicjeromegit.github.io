---
title: "January Update"
date: 2026-01-26T23:23:07+09:00
draft: false
---

Almost the end of January and no blog post yet !

Time to remedy that. One reason for the silence is I don't have much going on, in the past 6 months or so Claude Code and other coding agents have made such progress that pretty much anyone at my company (former QA, designers etc) is able to contribute new features to our product. It was foreseable and gradual for the past 2 years so it's not a huge shock, though it came faster than I expected, and last year (2025) caused a big questioning about my career as a software engineer. What value can I add when anyone with minimal experience can contribute to the codebase ? The situation is not so dire yet, I do have some answers at the present (like I'm good at debugging, experience with the whole stack, etc) but nothing that feels particularly future proof. Take debugging, it takes 30 seconds of searching to find a "vscode debugger mcp" that lets agent use VSCode integrated debugging (not that I would trust it enough to install it, but we're bound to have an official one someday). We're already at the point where a multiple agent setup can create an app, launch it, interact with it in a browser, and debug the backend, without human assistance. Am I a better debugger than a swarm of Claude-5.2-banana agents running in the background ? I don't believe so.

There is still that mysterious (to me) issue that agents can't use interactive terminal yet (like my [Gopilotty PoC](https://github.com/goverture/gopilotty)), but I'm sure they'll get to it (I found a feature request for Claude here https://github.com/anthropics/claude-code/issues/9881 , and [Gemini CLI implementation](https://developers.googleblog.com/en/say-hello-to-a-new-level-of-interactivity-in-gemini-cli/) only let the human, not the AI, use the PTY).

And it's not only about justifying a software engineer salary, even for personal projects it's hard to come up with ideas that can't be trivially done by AI yet (I want to believe my project from last year, [Prosettr.com](https://prosettr.com/), is still AI proof though ! maybe I should just revive it). Not saying AI can one shot big projects, but I'm talking about "one weekend-er" kind of projects. I used to have some idea, work on it on friday night and saturday night, maybe see it through sunday. Now it's done in 30 minutes and it's not even Friday evening, what do we do next ?

On a related note, VS Code finally added support for [Agent skills](https://code.visualstudio.com/docs/copilot/customization/agent-skills) (originally introduced in Claude Code around October last year I believe), just simple markdown files with "recipes" for the model on how to do specific tasks. It feels like it will only serve to reduce the gap between experienced engineers and agent users, once I've skill.md'ed all my "internal knowledge" about the product I'll really have nothing more to add, I guess it will be time to move on.

Not that it's a bad thing mind you ! I've always be doubtful of this "eternal sprint" product organization, our product is more than 10 years old, it was working fine before I joined the company, and it feels harder and harder to justify a whole division continuously working on it.

By the way, when I try to commit recently I'm welcomed by this new error, apparently some devs added a hook to perform a "commit lint" to make sure we respect the "conventional commit" format... I won't comment on the pedanticity of the matter (I could write a whole post about the loss of the last place of creativity in coding, but we want to autogenerate changelogs), however I noticed that to run the hook, I add to install... 89 fucking packages ? For a linter that can be implemented in a regex or a small parser ? Bonus point for the potential security vulnerability added to my dev env (I use dev container so i'm not too worried about my machine, but it's my employers API keys...)

```
npm install -D @commitlint/cli @commitlint/config-conventional

added 89 packages, and audited 140 packages in 6s

23 packages are looking for funding
  run `npm fund` for details

1 moderate severity vulnerability
```

Which brings me back to the first point, I think one way the whole "everyone can code" thing might play out is a "let's do everything in house" policy for more and more company. I mean that instead of importing external opensource and untrusted gems/packages, you'd just AI generate them yourself, possibly as an external library, but still controlled by you instead of some random github user. I would like that personally, in the past few years I've been favoring Go over Ruby or Typescript notably due to the completeness of their standard library, and I just generate dependencies instead of finding them on github (like some kind of file parser, etc). Maybe it's not doable yet for everything (PDF parsing...) but I feel like we'll get there. At the very list that stupid commit lint command would be the first one to go if I had my way.

Oh by the way I was on a business trip to Japan earlier this month, here is a nice view of Shibuya (a little farther than the usual crossing view you get from the Starbucks). 

<img src="/assets/images/shibuya_view.png" alt="Shibuya view from Hikarie 11th floor" height="500" loading="lazy" style="display:block;margin: 0 auto;" />
<p style="text-align:center"><em>Shibuya view from Hikarie 11th floor</em></p>

