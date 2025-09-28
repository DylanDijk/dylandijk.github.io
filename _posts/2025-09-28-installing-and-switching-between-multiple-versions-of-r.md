---
layout: post
title: Installing and switching between multiple versions of R
date: 2025-09-28 10:06 +0000
---

When working on R projects, in order to have reproducible code the renv package is useful to create a lock file that lists all the packages, and their versions, that are used in the project. However, renv does not lock the version of R itself. Therefore, if you want to ensure that your code runs with a specific version of R, you may need to install and switch between multiple versions of R on your system.

To do this on linux (ubuntu), I used these three tutorials:
- [How to install and switch between multiple R versions on a Mac](https://www.monicathieu.com/posts/2024-05-21-multiple-r-versions.html)
- [Posit instructions to install an R version](https://docs.posit.co/resources/install-r.html)
- [Posit switching between R versions](https://support.posit.co/hc/en-us/articles/200486138-Changing-R-versions-for-the-RStudio-Desktop-IDE)

