---
author_profile: true
date: "2025-02-08T00:00:00Z"
draft: true
title: Concurrent exact colver solving - Parallelizing Knuth's X algorithm
---

I just want a journal of my thoughts on the issue. The backtracking algorithm is trivially paralellizable if you fork the process at some branch, but the problem is that doubles the memory usage (I know about "copy on write", but eventually both childs will touch almost all rows).

I think there is a way to parallelize work for crossword problems in particular: if you think of the crossword grid as a graph (the words being the nodes, with an edge when they share a letter) then you can cut the graph in two, solve each half concurrently, and the whole puzzle is solved if both halves share the same "frontier" words.

![A simple connected crossword](/assets/images/crossword_graph.png)

For instance you can split the above crossword into two (1H and 1V) and (1V and 2), and if "1V" is the same then the whole crossword is solved.

![A solved connected crossword](/assets/images/crossword_graph_solved.png)
