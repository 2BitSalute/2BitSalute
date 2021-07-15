---
layout: page
title: "PR Flows"
date: 2021-07-15 15:05:00 -0700
permalink: /articles/pr-flows
---

| NOTE: Draft

# PR Flows

This article is going to compare the main PR flow that everyone in the world uses and the one that Facebook uses.
I would strongly advocate for all organizations that are able to maintain the tools and infrastructure supporting PRs (that includes Azure DevOps, GitHub, etc.) to follow Facebook's model.

## The Usual PR Flow

The main operations are:
- Make a branch
- 1:1 branch to PR relationship
- Until merge into main, all the intermediate commits are linear in the history of the branch
- Squash and merge to merge into main to keep main's history clean

[TODO: draw pictures]

Downsides:
1) hard to work on multiple interdependent changes at the same time
2) discourages from creating small PRs (see 1)
3) ...

## Facebook's Flow

The main operations are:
- Don't bother with named branches - commit locally (no concept of detached HEAD - this is Mercurial-specific)
- Each commit corresponds to a PR
- Commits are amended (as opposed to new commits being made)
- A sequence of commits can be submitted as a "stack" for code review
- The sequence of commits can be fully or parially merged into main
- Because the sequence of commits corresponds to logical work and not to code edits, the stack commits are applied individually (no squashing)
