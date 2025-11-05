---
title: "2025 11 05 November Update"
date: 2025-11-05T23:16:40+09:00
draft: true
---

A lot going on these days !

I succumbed to the hype and installed [Omarchy](https://omarchy.org/), the new Linux distro by DHH. It's basically Arch Linux with a tiling window manager ([Hyprland](https://hypr.land/)), but it comes pre-configured and installable with an ISO, which is super convenient compared to the usual Arch install. So out of the box you get a very good looking desktop with nice shortcuts and documentation.

Some will disagree with DHH preferences and choices, but realistically I would never have taken the time to configure Hyprland properly myself, so it's nice to be able to rely on somebody's taste (I trust DHH taste more than mine in that regard !). Same goes for the rest of the desktop environment (waybar for the top bar, walker for the app launcher...). That was my main issue with Arch, too much choice and alternatives that I don't really care about (I just want internet, not to have to choose a network manager...). So I really see the appeal of Omarchy for many people, and it seems to be gaining popularity.

I think it can be a nice gateway to more advanced linux usage, I've already made a few basic changes (added a couple web apps to the launcher, and reduced the gap between windows as my screen is quite small), it's pretty easy to configure. And the themes are very pretty !

Moving on, I've been making little progress on [Goxy](https://github.com/goverture/goxy) my budget limiter for OpenAI API - mostly rewrote the "money" handling to use integer instead of floats :) I just want to handle "streaming" completions and I'll release it.

I also started a new project that I'm quite excited about - not quite ready to release the code but I have a demo, I call it "gopilotty" (it's a go copilot in the tty). The twist is that it works in "interactive" terminal mode (think vim, sqlite3 or a ruby repl), not just for "one off" bash command.

<video controls width="1024">
  <source src="/assets/video/gopilotty_demo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

Basically it opens a two pane window, the left pane is a bash terminal and the right pane a chatbot, but the chatbot is able to execute commands in the left pane - without hanging, even for interactive commands like vim. So you can have the agent write some document in vim, navigate a database and execute some ruby script line by line. Still a bit buggy as you can see in the video but I think it's cool nevertheless :)

It's a combination of [pty/creak](https://github.com/creack/pty) to create a pseudo terminal, [vt10x](https://github.com/hinshun/vt10x) for the terminal emulation (so that special keys like backspace etc are handled properly) and [tcell](https://github.com/gdamore/tcell) (and [tview](https://github.com/rivo/tview)) for the terminal UI.

Alright lastly I've been trying to learn Chinese Chess (Xiangqi).

![Xiangqi starting position](/assets/images/xiangqi.png)

It's... quite a big departure from "western" chess with a slightly bigger board, different pieces (the elephant, which moves like a bishop but limited in range and can't cross the board, the canon is confusing as well as it needs a "screen", a piece in between it and its target in order to be able to capture) and especially the knight that cannot jump. So it's a bit of a mental gymnastic to "unlearn" western chess - which I was never really good at - and figure out how to use those new pieces efficiently. Been doing some puzzles and playing against the computer. Xiangqi is quite popular in Vietnam and many grandpas are playing daily in the square nearby, I look forward to playing with them (I've played once but got defeated immediately -_-).

