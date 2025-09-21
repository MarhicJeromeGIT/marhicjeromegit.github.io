---
author_profile: true
date: "2025-01-27T00:00:00Z"
title: Happy Lunar New Year
---

This week it's Lunar New Year, or Têt celebrations in Vietnam. Which means my daughter's school is off, which means I get approximately 30 seconds of free time per day. Despite that, it was hard to miss the hype regarding the release of Deepseek R1. I didn't have time to read the paper or anything, but I gave it a quick try at [chat.deepseek.com](chat.deepseek.com). I still don't have a good handle on what is a good "reasoning question," but I came up with a good use case today: coming up with a memorable port number for a service I'm hosting locally.

> Can you come up with a good, 4-number goroawase for a port number? I want to host an RSS reader (Miniflux), so something related to reading/RSS/blogs if possible (otherwise it's okay).

(Goroawase is Japanese wordplay with numbers, more on [Wikipedia](https://en.wikipedia.org/wiki/Japanese_wordplay)).
Contrary to OpenAI, which hides them, it was fun seeing the model's thoughts - in total, the model thought for 94 seconds. Here are a few excerpts of the thoughts:

> First, let's think about keywords related to RSS readers. Words like read, feed, blog, news, article, subscribe, update, etc. Now, map these to possible Japanese number pronunciations. For example, "read" might be associated with "yo" (4) since "yo" can mean "read" in some contexts.
> Looking for combinations. For example, "read" might be 4 (yo) as in "yomu." "Feed" in Japanese is "fīdo" (フィード), so maybe 4 (fu?) Hmm, maybe not. Alternatively, "RSS" could be R-S-S, which might correspond to numbers like 1 (ichi for 'i'), but not sure. Alternatively, "blog" is "burogu" in Japanese. Maybe 6 (ro) and 9 (gu). So 6-9 could be "rogu," part of "burogu."

> Alternatively, the word "blog." B is the 2nd letter, L is the 12th, O is the 15th, G is the 7th. 2-12-15-7. Doesn't fit into 4 digits. Hmm.

> Hmm, maybe I'm overcomplicating. Maybe the best approach is to find a number where the digits can be read as a word related to reading. For example, "yomu" is 4 (yo) + 6 (mu). So 4-6-XX. But need four digits. Maybe 4-6-1-9 (yo-mu-i-kyu). "Yomu iku" (to read and go). Not perfect, but maybe a stretch.

> Alternatively, 4-6-1-1 (yo-mu-i-i). "Yomu ii" (good to read). That could work! 4611. Let's check: 4 (yo), 6 (mu), 1 (i), 1 (i). "Yomu ii" (読むいい) which means "good to read." That's a possible candidate. But 4611. Is that a valid port? Ports are 0-65535, so yes. And not reserved. So 4611 as "yomu ii" (good to read). That might be a good fit.

You can really see it examining different alternatives, but ultimately coming back to the best choice, in my opinion, with "4-6," which reads "yo-mu" (to read). It thought a bit more after the "4-6-1-1" thought, but ultimately that was its answer. Which I'm quite happy with!

As a comparison, I asked the same prompt to ChatGPT 4.0 and got this:

> Here’s an idea for a goroawase port number related to reading, RSS, or blogs:
> 8645 (ハムシゴ, "Ha-mu-shi-go")
>    Breakdown:
>        8 = ハ (Ha)
>        6 = ム (Mu)
>        4 = シ (Shi)
>        5 = ゴ (Go)
> Interpretation: It loosely sounds like "読む仕事" (yomu shigoto), meaning "reading job" or "reading work," which aligns nicely with the idea of an RSS reader for staying on top of blog content.
> Let me know if you'd like to brainstorm others!

Which is quite bad (it should be 4 instead of 8). OpenAI thought for 27 seconds and came up with:

> 1106 → いい本 (ii hon)
> In Japanese, “いい” (ii) means “good” and “本” (hon) means “book.” So 1106 can be read as “ii hon,” literally “good book.” It’s quick to say, easy to remember, and ties nicely to the idea of reading!

Which was a bit better, but ultimately I went with Deepseek's 4611 to host my RSS reader, [Miniflux](https://miniflux.app/), on my Raspberry.

![Elevated Highway in Vinhomes, HCMC, January 2025](/assets/images/elevated_highway_vinhomes.jpg)

They are building an elevated highway not far from my place, so I get to see the progress daily. Currently, they are laying down the beams across the pillars. It's quite impressive from my point of view (we don't see a lot of those in France). It must require a lot of organization. Last week, I got stuck in a 10-person, 1-hour meeting to discuss a feature to allow for the import of a CSV into our app. At those times, I kind of wish I was doing some "real" work instead of this.

