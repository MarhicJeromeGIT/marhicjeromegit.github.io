---
layout: single
title: OpenAI o3-mini first impressions
date: 2025-02-02 09:27 +0000
author_profile: true
---

Two days ago, OpenAI released their latest model, [OpenAI o3-mini](https://openai.com/index/openai-o3-mini/), a follow up to the reasoning models o1 and o1-mini. They were immediately available on chatgpt.com, so I had a chance to put them to work. I had a simple task in mind (writing a python script that would prompt a LLM to rate a list of words for use in my crossword app, [prosettr.com](https://prosettr.com)). The first output was good, but when I asked for a few minor tweaks I was presented with a refusal:
>Your request was flagged as potentially violating our usage policy. Please try again with a different prompt.

![openai o3-mini refusing to perform](/assets/images/o3_refusal_1.png)

I guess it's due to Openai trying to hide their own model chain of thought, but here I was just asking for a prompt tweak in my script, not trying to get OpenAI's secret sauce.

Later on I decided to use vllm's "offline batched inference" instead of the server mode, so I asked for the corresponding change. And... for some reason it refused again ?

![openai o3-mini refusing to use a competitor model](/assets/images/o3_refusal_2.png)

The optics are pretty ugly on that one: It's a policy violation to replace openai's by vllm calls now ? To be fair, afer I insisted it gave a second thought and acceeded to my request, but it felt more like... Not sure how to say it, like a customer service doing me a favor just for this time, rather than a tool being reliable. But I think it's clear that the censor model used by OpenAI is too restrictive, getting in the way of real work done. And it makes me glad for open source LLMs existing, a future where some reasonable requests like "use a competitor" are flagged is not unimaginable.

So, mixed feelings on o3-mini so far, I haven't noticed an obvious quality difference compared to o1-mini, I'm happy with the increased message rate limit, but I'll switch to Claude or Deepseek the next time I see a refusal.