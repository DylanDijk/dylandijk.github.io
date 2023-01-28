---
layout: post
title: linux aliases
date: 2023-01-28 14:56 +0000
tags: [Linux]
---

To creata a Linux terminal alias you add the alias to the `.bashrc` file in your home directory.

These are the aliases I am currently using:

```bash
# custom aliases

alias gs='git status'
alias pers='cd Documents/Projects/Personal-webpage/dylandijk.github.io/'
alias projs='cd Documents/Projects/'
alias be='bundle exec'
alias checkall='find . -name .git -type d -execdir git status \;'
```
{: .nolineno file=".bashrc" }
