---
author_profile: true
date: "2025-02-02T00:00:00Z"
title: OpenAI o3-mini first impressions
---

Two days ago, OpenAI released their latest model, [OpenAI o3-mini](https://openai.com/index/openai-o3-mini/), a follow-up to the reasoning models o1 and o1-mini. They were immediately available on chatgpt.com, so I had a chance to put them to work. I had a simple task in mind (writing a Python script that would prompt an LLM to rate a list of words for use in my crossword app, [prosettr.com](https://prosettr.com)). The first output was good, but when I asked for a few minor tweaks I was presented with a refusal:
>Your request was flagged as potentially violating our usage policy. Please try again with a different prompt.

![openai o3-mini refusing to perform](/assets/images/o3_refusal_1.png)

I guess it's due to OpenAI trying to hide their own model's chain of thought, but here I was just asking for a prompt tweak in my script, not trying to get OpenAI's secret sauce.

Later on, I decided to use vLLM's "offline batched inference" instead of the server mode, so I asked for the corresponding change. And... for some reason it refused again?

![openai o3-mini refusing to use a competitor model](/assets/images/o3_refusal_2.png)

The optics are pretty ugly on that one: It's a policy violation to replace OpenAI's by vLLM calls now? To be fair, after I insisted it gave a second thought and acceded to my request, but it felt more like... not sure how to say it, like a customer service doing me a favor just for this time, rather than a tool being reliable. But I think it's clear that the censor model used by OpenAI is too restrictive, getting in the way of real work done. And it makes me glad for open-source LLMs existing, a future where some reasonable requests like "use a competitor" are flagged is not unimaginable.

So, mixed feelings on o3-mini so far. I haven't noticed an obvious quality difference compared to o1-mini, I'm happy with the increased message rate limit, but I'll switch to Claude or Deepseek the next time I see a refusal.

