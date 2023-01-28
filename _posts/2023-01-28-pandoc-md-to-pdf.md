---
layout: post
title: pandoc md file to pdf
date: 2023-01-28 14:23 +0000
---


On linux to install pandoc:

```console
$ sudo apt install \
    pandoc \
    texlive-latex-base \
    texlive-fonts-recommended \
    texlive-extra-utils \
    texlive-latex-extra \
    texlive-xetex
```

Then if you want to convert a markdown file to pdf you run:

```console
$ pandoc file-name.md -o file-name.pdf --pdf-engine=xelatex
```