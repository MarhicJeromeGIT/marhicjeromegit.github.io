---
author_profile: true
date: "2025-07-05T00:00:00Z"
title: July Update
---

Just a quick update to say I am still making progress on the Password Game Agent project I mentioned last post. I have now reached up to step 16 where we need to solve a chess position... Seems like a suitable job for a reasoning model !

![Step 16 of the password game require solving a chess puzzle.](/assets/images/password_game_step16.png)

The main changes that enabled going from step 11 (Wordle answer) to 16 were adding a "search tool" based on [OpenAI web search tool](https://platform.openai.com/docs/guides/tools-web-search) and changing the reasoning effort from "medium" to "high".
The current version of the code is here : https://github.com/goverture/password-game-agent/blob/master/manually.py I'm still making regular changes and trying new ideas to make progress. I've noticed we often seem to get stuck for various reason (for instance a badly recognized Capcha), so I want to add a new step to ensure that we make progress consistently, or backtrack, in order to not get stuck.