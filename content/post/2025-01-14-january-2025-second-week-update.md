---
author_profile: true
date: "2025-01-14T00:00:00Z"
title: January 2025, Second Week Update
---

Already two weeks into January, it's time for an update on my projects! I'm really happy with the progress on [Prosettr.com](https://prosettr.com), my crossword generation app. It will soon be time to share it with the world (HackerNews...). Yesterday evening, I added login functionality (a choice of email + password or Google sign-in) using Firebase Authentication, as well as a button to load PUZ files.

The latter was surprisingly easy to do: I gave ChatGPT o1-mini the [PUZ format description](https://gist.github.com/sliminality/dab21fa834eae0a70193c7cd69c356d5) and asked it for a loader/writer in Go with my expectations for the input/output, followed by an HTTP handler. Thirty minutes later, here we are with the "Upload PUZ File" in production!

![Prosettr.com as of Jan 14th, 2025](/assets/images/prosettr_20250114.png)

It seems like for every feature I add, I get an idea for another one, so I started prioritizing and separating "must-have" and "nice-to-have" features. "Nice-to-have" features include everything related to "word scores" (the "quality" of a word) and prioritizing high-quality words in the search. It's important, but getting users first seems more important. The same goes for multithreading—I wish the search was faster, but for now, there is no one waiting for the results, so...

"Must-have" features, however, include finding a better word list, an export button, authenticating the backend endpoints, implementing per-user search quotas (easy now that users are logged in), writing an "About" page, etc. There's so much left to do!

I'm taking a week off at the end of the month for Lunar New Year. I'll try to push and finish the app by then.

