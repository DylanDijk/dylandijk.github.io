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
alias pers='cd /home/zl22291@bristol.ac.uk/Documents/Projects/Personal-webpage/dylandijk.github.io/'
alias projs='cd /home/zl22291@bristol.ac.uk/Documents/Projects/'
alias be='bundle exec'
alias checkall='find . -name .git -type d -execdir sh -c '\''git status --porcelain | grep -q "^ M" && echo -e "\\033[0;31m${PWD}\\033[0m"'\'' \;'
alias copypwd='pwd | xclip -sel clip'

```
{: .nolineno file=".bashrc" }
