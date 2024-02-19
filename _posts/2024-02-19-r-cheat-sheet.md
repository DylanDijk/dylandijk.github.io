---
layout: post
title: R Cheat Sheet
date: 2024-02-19 17:13 +0000
---

- Finding C source code for internal R functions
 
 ```r
 library("pryr")
 show_c_source(.Internal(backsolve()))
```