---
author_profile: true
date: "2025-06-18T00:00:00Z"
title: The password game agent
---

There is this javascript game called [The Password Game](https://neal.fun/password-game/) where you have to chose a password, following increasingly ludicrous requirements.
Agentic coding/research is all the rage today and I got the idea of making an "agent" that would solve it. Conceptually it's just about calling a LLM in a loop, giving it the proper tools and context until it solved the task at hand.

Here's where I got so far, using ChatGPT 4o and [Playwright MCP](https://github.com/microsoft/playwright-mcp) (only gave it the navigate and type tools for now). It's solving correctly the first few steps, but gets stuck at the "sponsor" rule because it cannot view the image. The next step is to give it access to the playwright's screenshot tool. Let's see how far it can go !

<video controls src="/assets/video/password_game_1.webm" title="Title" height=500></video>

On an unrelated note, my company finally decided to self host a model ! We are going for vLLM+Skypilot. Pretty excited about the possibilities here, though hosting on AWS is expensive and I have doubts about the return on interest (last time I did the math, it was basically impossible to beat gpt-4o-mini pricing on token/\$, so let's hope the quality is there and that we can migrate to a cheaper GPU provider).

# Edit: June 29th

Alright a quick update on the password game, I now pass a screenshot after each step and with a little bit of [context engineering](https://simonwillison.net/2025/Jun/27/context-engineering/), and adding an extra thinking step with o4-mini, I was able to consistently clear the "sponsor" image step (as well as the captcha step !). I reached up to step 11, which requires knowing "Today's Wordle answer"... gonna be hard to solve ! I think I need a different approach for this one (multi agent ?), where I can delegate a subtask to be cleared by a different agent (ie "find today's wordle answer" using search and navigation). I'll see if I can use the [OpenAI Agent SDK](https://github.com/openai/openai-agents-python) to make progress.

![Step 11 of the password game require knowing today's wordle answer...](/assets/images/password_game_wordle.png)
