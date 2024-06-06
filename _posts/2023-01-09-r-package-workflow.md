---
title: Creating an R Package - Cheat Sheet
date: 2023-01-09 09:42:00 +0000
categories: [R, Cheat sheet]
tags: [R, R Packages, Cheat sheet]
img_path: /assets/img/figures/
---

In this post, I cover the main commands that are used in the process of creating an R package. The majority of the commands are from the `usethis` and `devtools` R packages.

**Main references**:
- The [R Packages](https://r-pkgs.org/) book by Hadley Wickham covers the entire workflow of creating an R package.

# R Package

## Vignette

  - To start new vignette `usethis::use_vignette("vignette-name")`
    - There also exists `usethis::use_article("vignette-name")` which creates an article, this is similar to a vignette but it is added to `.Rbuildignore`. Therefore it is not part of the packages source code, but it will appear in `pkgdown` sites.





