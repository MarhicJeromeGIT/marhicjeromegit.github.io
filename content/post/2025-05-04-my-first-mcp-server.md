---
author_profile: true
date: "2025-05-04T00:00:00Z"
title: My First MCP server
---

So MCP is all the rage these days, and it's not very complex: it's basically a standardized way to provide tools to LLMs. So you have an RPC server that provides a description of the tools and the parameters they expect, and your client (a LLM based application) can connect to it and tell the LLM what tools are available, and the LLM can decide to call them when appropriate. Easy stuff and the [SDK provided](https://github.com/modelcontextprotocol/typescript-sdk) do most of the heavy lifting.

So in order to give it a try I made a simple ["Random number" MCP server](https://github.com/goverture/mcp-random) in typescript. The idea being that the LLM would call it when asked to generate a random number. Apparently VSCode agent only supports "tools" and not "resources" at the moment, and also they only support the legacy "SSE" transport type (by opposition to the newest StreamableHttp) so I added support for both (basically you get two endpoints, /mcp for StreamableHttp and /sse for SSE). And then you can connect your server to multiple different clients ! I tried with VSCode copilot agent, the local [MCP inspector tool](https://github.com/modelcontextprotocol/inspector) and the online [Cloudflare AI Playground](https://playground.ai.cloudflare.com/).

Here's how it looked:

from VSCode Copilot (agent mode)
![Calling my random MCP server from VSCode Copilot agent](/assets/images/mcp_vscode.png)

from locally hosted MCP Inspector
![Calling my random MCP server from MCP Inspector](/assets/images/mc_inspector.png)

from the Cloudflare AI Playground
![Calling my random MCP server from Cloudflare AI Playground](/assets/images/mcp_cloudflare.png)

For the Cloudflare Playground, I hosted my server online with Fly.io, at [https://random-mcp.fly.dev/](https://random-mcp.fly.dev/). Feel free to use it if you need a random number :) Fly.io became my favorite way to spin up a quick backend ! And it's free while my monthly bill is under 5\$, which is super nice of them.

My secret to free infra ? Having no user and no traffic on my apps.
![free fly.io bill this month](/assets/images/free_fly.png)

Anyway, as expected HackerNews is bearish about MCP, but it's pretty nice to finally have a standardized way to create and expose tools to the LLM. It's super easy technically, we'll see if it makes sense to use them in our products.

NB: Re-reading my post, I noticed I insisted quite a bit on the "easy" part, mentioning it 3 times in total. It's because I got a grand total of 1 hour of free time this week and that was enough to get my prototype deployed and working.
