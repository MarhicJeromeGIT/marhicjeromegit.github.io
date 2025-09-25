---
title: "September Update"
date: 2025-09-25T16:28:00+07:00
draft: false
---

I just came back from a two weeks vacation in France with my daughter, and without my laptop, which was pretty nice. As a result I don't have much to say for this month !

After coming back I had an idea for a small project, a "guess who" app that I vibecoded in a few hours with [Firebase Studio](https://firebase.studio/). It got me a Next.js+tailwindcss app pretty quickly, with LLM calls handled by [Genkit](https://genkit.dev/). Originally it was using the Gemini API and hosted on Firebase, but I've changed it to GPT-5 and Fly.io for hosting.

![Guess Who game app](/assets/images/guesswho.png)

I haven't looked much at the code actually, but the LLM part of it seems clean and use Genkit flows, and the app works well enough that I call it a success ! I'm not quite ready to release (mostly I need to put some kind of spending limit on the API token). It's so strange that the main LLM providers don't allow setting a maximum spending limit on a given API token already. I'm not going to risk spending thousands on a stupid app in case it might go viral !

Oh, and I migrated my blog from [Jekyll](https://jekyllrb.com/) to [Hugo](https://gohugo.io/). No special reason for the change, these days I'm much more into Go than Ruby, and it was pretty painless with the [Import](https://gohugo.io/commands/hugo_import_jekyll/) command. I still have to fix some links.

To finish with, a cool picture of my home viewed from the plane, on the way back !

![Vinhomes](/assets/images/vinhomes.png)
