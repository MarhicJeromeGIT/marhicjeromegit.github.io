---
layout: single
title: February update
date: 2025-02-28 14:57 +0000
author_profile: true
---

February went by in a blink ! I barely had any time for myself this month between work, a pregnant wife and my 2 years old being in the "I want papa only" phase. These days, the first thing I do in the morning is playing Lego. It beats doomscrolling, but at 7 am and before my coffee it's tough to be creative. Here's an elephant I made this morning, the trunk moves.

<div style="text-align: center;">
    <img src="/assets/images/lego_elephant.jpg" alt="An elephant in Lego" width="300">
</div>

I've also rewrote a big part of the backend of [Prosettr.com](https://prosettr.com). In a HackerNews thread about Donald Knuth ([Donald Knuth's 2024 Christmas Lecture: Strong and Weak Components](https://news.ycombinator.com/item?id=42970240)), I've learned there was an improvement to the algirhtm that my app is based on, Dancing Links. I'm not going to go into much details here (maybe in a future post), but I procured the Art of Computer Programming volume 4B, and indeed the improved version uses half the memory, each option's items having only up and down links, and no left and right links - those being replaced by a "spacer" node. Here's my original implementation in Go I made while following the chapter : [/backtrack_aocp/main.go](https://github.com/goverture/exact_cover/blob/master/examples/backtrack_aocp/main.go). Then I replaced the previous implementation by this one, with some added optimizations (support for secondary columns, using channels instead of an input matrix, another channel to output the solutions etc).

The best part of the algorithm is that, even though the book describes the links between nodes as "pointers", they really are just an offset into the Node array. Which makes copying the structure super easy, which in turn enables parallelizing the search process ! It's still not perfect, but here's what I have at the moment.

The other advantage is that, since it's an offset and not a pointer, I can actually chose to use int32 (instead of 64-bits pointers), and halved the memory usage again ! I just defined `type AppInt int32` and used that instead of `int` for the offsets. It works as long as you have less then 2 billions nodes, I have around 100 million for a 21x21 crossword so I'm safe.

![Generating a crossword with thematic words](/assets/images/fruits.gif)

In a few seconds, you can generate a crossword using as much thematic words as possible.

Lastly, I've started using [Aider](https://aider.chat/) ("Aider is AI pair programming in your terminal"). I've been feeling more and more FOMO recently with the newest LLMs release (Claude 3.7 and GPT4.5 just this week) and the various agentic tools ([Cursor's composer](https://docs.cursor.com/composer), Claude Code...). I want to give them a proper try, but I'm not ready to give up control on my workflow. I'm actually using Aider with git-commit disabled, as I prefer to view the diff before committing. It went well so far, I've been able to save quite some time (compared to copy and pasting to and from ChatGPT). For some reason it sometime edits the wrong part of the code though (I saw it editing the wrong CI job definition, and the wrong test, but with correct code - I just had to manually move it).

Let's see, what else ? Andrej Karphathy just released a video titled [How I use LLMs](https://www.youtube.com/watch?v=EWvNQjAaOHw), which threw me back to my earlier, pretty half-assed blog post: [How I use GitHub Copilot]({% post_url 2024-12-25-how-i-use-github-copilot %}). Curious to see how my programming process will evolve this year. I've been following G. Huntley's posts about cursor and the future of programming (See [https://ghuntley.com/ngmi/](https://ghuntley.com/ngmi/) for instance) about the necessity of embracing LLM powered programming, and anyway It's a pretty exciting development to follow. It has been humbling to realize a machine can do a better job than me at writing code - and frankly it's a good thing, I don't miss searching stackoverflow or some API docs to find out what flags to pass to append to a file or such trivialities, and I get more time to focus on the big picture. It's almost midnight so I'm going to stop here and push the post before we move to March !