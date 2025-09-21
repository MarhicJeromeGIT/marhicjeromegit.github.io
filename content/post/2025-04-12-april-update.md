---
author_profile: true
date: "2025-04-12T00:00:00Z"
title: April update
---
Unsurprisingly with a newborn and a very sticky 3 years old at home, I haven't been doing much in the past 3 weeks. Since I stopped working on it, I've released my thematic crossword generation app, [Prosettr](https://prosettr.com), to a complete (and expected) indifference (zero traffic came from the [HackerNews announcement](https://news.ycombinator.com/item?id=43521279), and I got about 10 likes from LinkedIn). Oh well, it was a fun project anyway and I'm quite happy with the result!

When getting ready for release I was considering my hosting options - GCP Cloud Run kind of rugged pull me with their CPU and memory quotas being way too low! And I was not going to beg them for a quota increase. Luckily, [Fly.io](http://fly.io) saved the day with their super easy to use fly machines. My app requires a lot of CPU and memory (4cpu, 16 Gb of RAM) in very short bursts - just a few seconds when the user is doing a solve. I made a simple "controller" endpoint that starts and stops "solver" machines on demand, for that. The Fly.io API was a pleasure to work with, and it's nice to be able to connect via a wireguard network.

Here is the code of the controller endpoint for later reference: [Fly.io controller endpoint in go](https://gist.github.com/MarhicJeromeGIT/2d883c7b295bc4ab26b0f1b92597869a). With that, I get a fleet of solver machines (I scaled to 8), and a single controller machine start them and proxies the websocket connection. I put it together in an evening and was pleased with the results. Fly machines really do start in a few milliseconds! I'll use them in my next project, whatever that may be.

Moving on, VSCode finally released their [MCP support](https://code.visualstudio.com/updates/v1_99)! I've been eyeing MCP stuff for a while but I didn't have a MCP client (think Claude Code or Cursor) to play with. Now I have one with Copilot Agent! I asked our Infra team to enable the Copilot "Preview Features" for our organization, otherwise the MCP Servers didn't appear in the list somehow.

I followed a video tutorial on [youtube](https://www.youtube.com/watch?v=dutyOc_cAEU) and got the Postgres MCP working locally. It seems promising, I'll have to play more with it.

I'll close with a generated image of Nvidia's CEO as a lego figurine, the new ChatGPT image generation rocks!

![Jensen Huang Lego](/assets/images/jensen_lego_figurine.png)

