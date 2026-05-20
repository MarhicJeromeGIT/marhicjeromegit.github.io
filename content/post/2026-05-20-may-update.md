---
title: "May 2026 Update - OpenCode and CTF"
date: 2026-05-20T23:17:20+09:00
draft: false
---

A few days ago, there was a trending post on HN called "The CTF scene is dead." ([link](https://kabir.au/blog/the-ctf-scene-is-dead)), in which the author laments that CTF (capture the flag, "hacking" competitions) are dead due to being mostly solvable by AI, which actually made me want to try it!

I've actually never done any CTF, so after some research, I ended up doing the first 15 levels of the OverTheWire [Bandit](https://overthewire.org/wargames/bandit/bandit0.html) game. Frankly it wasn't super interesting (mostly running find commands with the right flags...) due to it being aimed at absolute beginners.

So I fired up [OpenCode](https://opencode.ai/), set up an OpenAI key and asked it to solve the Bandit CTF, starting from [Level 0](https://overthewire.org/wargames/bandit/bandit0.html). It made some progress, but I noticed it was running bash commands directly from the SSH command (I mean like this `ssh user@1.2.3.4 'cat foo.txt'`) which seemed inconvenient compared to having a persistent SSH session to run commands in. So I installed the [opencode-pty plugin](https://github.com/shekohex/opencode-pty), created an [agent](https://opencode.ai/docs/agents/) with some instructions (using the pty, writing the process and passwords down, etc.) and let it run.

With GPT 5.4 mini, it was able to solve the bandit levels up to 26 and then got stuck in a loop, eventually giving up with this message:
> I’m blocked on bandit26: the key login works locally, but the expected pager/vi escape isn’t triggering in this terminal environment. I can keep trying alternate TTY tactics if you want.

I think there was some issue with the size of the terminal, though I'm not quite sure. Instead, I switched to GPT 5.4, which immediately resolved the issue and breezed through the remaining levels (36 of them). In total it took around $2 in tokens, and less than one hour (maybe around 30 minutes).

Now, this is explicitly a "beginner level" CTF, so to spice things up, I decided to try it against neal.fun's "password game". Last year I wrote an agent to try and solve it and got stuck at level 16 (the chess level). So I fired up OpenCode and after a couple of attempts, with the following prompt I was able to reach rule 18!

> Access https://neal.fun/password-game/ in headed mode like so:
PLAYWRIGHT_MCP_SANDBOX=false playwright-cli open https://neal.fun/password-game/ --headed
Then try to go as far as you can in the game! Play the game fairly as it is meant to (i.e. don't try to read the JavaScript code or something).
If you get stuck just refresh the captcha and try again.

I'm running with sandbox deactivated because I'm inside a dev container, and in headed mode so I could see what's going on. Notice from the prompt that I had some issues with the agent trying to "hack" the game by looking at the source code.

Rule 18 is `The Elements in Your Password Must Have Atomic Numbers That Add Up to 200`. Unfortunately the agent got stuck here: it tried to brute-force it by writing a JavaScript loop, but it didn't seem to notice the already highlighted elements, and the whole thing eventually timed out. Pretty cool run nonetheless! It gets me super bullish on OpenCode as a whole. And if it is as efficient on newer, harder CTF competitions, I can understand the author's claim that CTFs are dead. I totally didn't learn anything technical from watching OpenCode solve it, but it was a lot of fun nonetheless.

On a totally related note, today Google announced that [they are retiring Gemini CLI](https://developers.googleblog.com/an-important-update-transitioning-gemini-cli-to-antigravity-cli/) less than a year after announcing it publicly... Not a big loss, though I gave Gemini CLI a try last year as it was open source and came with some free tokens, I was never able to get great results with it, and I have zero interest in trying their Antigravity replacement (will be waiting for the graveyard announcement!). Instead, I'll just stick with OpenCode for the foreseeable future.

<img src="/assets/images/opencode-password.png" alt="The password game played by OpenCode" height="500" loading="lazy" style="display:block;margin: 0 auto;" />
<p style="text-align:center"><em>The password game played by OpenCode</em></p>

