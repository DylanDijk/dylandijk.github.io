---
layout: post
title: pandoc md file to pdf
date: 2023-01-28 14:23 +0000
---


On linux to install pandoc:

```terminal
$ sudo apt install \
    pandoc \
    texlive-latex-base \
    texlive-fonts-recommended \
    texlive-extra-utils \
    texlive-latex-extra \
    texlive-xetex
```

Then if you want to convert a markdown file to pdf you run:

```terminal
$ pandoc file-name.md -o file-name.pdf --pdf-engine=xelatex
```

To change the colour scheme for the code chunks, add the `--highlight-style=<style name>` option. A list of them are shown [here](https://www.garrickadenbuie.com/blog/pandoc-syntax-highlighting-examples/)

For example you could run:

```terminal
$ pandoc --highlight-style=breezedark file-name.md -o file-name.pdf --pdf-engine=xelatex
```