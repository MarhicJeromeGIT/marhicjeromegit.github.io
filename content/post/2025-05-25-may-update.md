---
author_profile: true
date: "2025-05-25T00:00:00Z"
title: May update
---

Another May update ! Not much going on as usual, rainy season arrived in Ho Chi Minh city so we get some strong rain and nice sunsets.

![Rainy season sunset](/assets/images/sunset.jpg)

Yesterday we got the announcement that [Pocket was saying goodbye](https://support.mozilla.org/en-US/kb/future-of-pocket). Kind of bummed because I found the service convenient, though I just used it as a link bookmark (I never cared much about the reading mode, I always go to the original link - though apparently that worked well with the Kobo e-reader). Anyway I switched to a self-hosted alternative immediately: [Wallabag](https://wallabag.org/). It's kind of sluggish but it does the job, and it has an Android app so I can still "share link" to save a link from my phone.

That brings my current self hosted service collection to:

* Wallabag (Read-it later)
* Pihole (DNS)
* Miniflux (RSS)
* Prometheus/Graphana
* Jellyfin (Media)
* Openwebui (AI Chatbot)

Anyway, I was importing my old pocket saves into my new Wallabag setup (I've got a script to import your links from Pocket [here](https://gist.github.com/MarhicJeromeGIT/6a87d8f8744b49c7e32315180729ae9b)) and I found an old save from Russ Cox's blog, [Regular Expression Matching Can Be Simple And Fast ](https://swtch.com/~rsc/regexp/regexp1.html). It has this scary looking graph for a not so scary looking regex:

![regex to the moon](/assets/images/regex_backtracking.png)

I decided to check if that was true (or at least still the case) with that code:

```ruby
require 'benchmark'

n = 33
regex = Regexp.new("a?" * n + "a" * n)
str = "a" * n

time = Benchmark.realtime do
  puts regex.match?(str)
end
```

Not sure about Ruby 1.8, but indeed on Ruby 2.7.2, the above took around 30 seconds to execute. The good news is that it got fixed in Ruby 3.2 and this is now pretty much instant !

Not much else going on, on the AI front recently I gave [Lovable](https://lovable.dev) a try and it makes nice designs, but I don't have a project idea at the moment. In the past few weeks there has been so many new product release and model updates that I kind of checked out... Are [Google AI Studio](https://aistudio.google.com) and [Firebase Studio](https://firebase.studio/) two different things ? [OpenAI Codex](https://openai.com/index/introducing-codex/) is a cool name, but it used to be the [original copilot code completion model right](https://github.com/openai/codex) right ?? And one month after VSCode adds ["Agent mode"](https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode) to copilot, we get [Github Copilot coding agent](https://github.blog/news-insights/product-news/github-copilot-meet-the-new-coding-agent/) ??? Come on.

Anyway, so far I'm happy with my oldschool VSCode + Copilot Agent based workflow. At work, people have been onboarding Devin but I'm still waiting to be wowed (I'm doubtful this will happen, as long as you need to describe in minute details the task to perform, then it's faster to go ahead and do it yourself). But things are clearly moving fast toward a "github based" agent workflow where an external service clones your repo and make entire pull requests for you, can't say I'm thrilled.
