---
layout: post
title: Using Overleaf as a Remote Repository
date: 2023-01-12 21:12 +0000
categories: [Workflows, Overleaf]
tags: [Overleaf, Git, Github]
---

It is possible to set up Overleaf as a remote repository such that you can use it as an interface for a local repository. Then whenever you make a change on Overleaf, and compile, you can run `git pull overleaf master` to pull the changes from Overleaf to your local repo.

If you want to collaborate with others on a latex file and use Overleaf, using Overleaf as a remote repository can be problematic as it is difficult to manage conflicts.  

**Main References**
- Section *Creating an Overleaf project from an existing Git repository* from this [documentation](https://www.overleaf.com/learn/how-to/Using_Git_and_GitHub).

