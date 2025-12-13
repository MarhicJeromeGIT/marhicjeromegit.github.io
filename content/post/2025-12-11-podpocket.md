---
title: "Podpocket release"
date: 2025-12-11T10:10:18+09:00
draft: false
---

I've been frustrated with YouTube Music as a podcast player ever since Google retired [Google Podcast](https://killedbygoogle.com/) last year, mostly because they now play ads before each episode! So I've decided to develop and release a minimal podcast player, [Podpocket](https://podpocket.jmarhic.com/).

It was really a pleasure to develop it with [Pocketbase](https://pocketbase.io/), as it handled everything I need:
- authentication (including oauth) setup in a few clicks
- a UI to create new collections (sqlite tables), and a complete admin dashboard
- Even Cron jobs (to refresh the RSS feeds periodically)

And best of all, it's written in Go so you can extend it super easily. For instance, I added an endpoint to register new RSS feeds, and I still have a single unified backend. This is unlike Firebase where you end up with a split architecture where some calls go directly to Firebase services and others to your custom backend. I'm definitely going to reuse it in my next project. A fun feature is the [user impersonation](https://pocketbase.io/docs/authentication/#users-impersonation) that lets an admin login as another user.

All said, I'm pretty happy with the result itself, especially given how quickly I made it. It's bare-bone but I do actually use it myself! It looks decent on mobile, the feeds are refreshed regularly, the player saves the listening progress. I hosted the frontend on AWS Cloudfront, and the backend is now on Hetzner. I originally put it on Fly.io (with scaling to 0) but as I needed cron jobs I first moved it to my home Raspberry Pi behind a [Tailscale Funnel](https://tailscale.com/kb/1223/funnel) but it didn't feel resilient (I regularly power down the raspberry), so I eventually decided to put it on a Hetzner VPS.

![Hetzner VPS configuration](/assets/images/hetzner_vps.png)
*Let me guess, you need more ?*

Anyway, feel free to give it a try! There is a big issue with discoverability; I just mark my episodes as recommended. I could find [a list of podcasts](https://github.com/rShetty/awesome-podcasts) but I don't want to recommend stuff that I don't listen to myself. So you have to bring your own RSS links, basically :) The link is [podpocket.jmarhic.com](https://podpocket.jmarhic.com/) – I don't want to pay for a custom domain for it.