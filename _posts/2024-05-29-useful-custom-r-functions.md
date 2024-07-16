---
layout: post
title: Useful custom R functions
date: 2024-05-29 09:49 +0000
categories: [R, Functions]
tags: [R]
---

# Heatmaps

Given two matrices, this function plots heatmaps for each one with a fixed colour scale to allow for comparison.
```r
heatmap_scale = function(matrix1, matrix2){
    
  global_min <- min(matrix1, matrix2)
  global_max <- max(matrix1, matrix2)
  
  my_palette <- colorRampPalette(c("blue", "white", "red"))(n = 299)
  
  heatmap(matrix1, Colv = NA, Rowv = NA, scale = "none",
          col = my_palette, breaks = seq(global_min, global_max, length.out = 300))
  heatmap(matrix2, Colv = NA, Rowv = NA, scale = "none",
          col = my_palette, breaks = seq(global_min, global_max, length.out = 300))
  
}
```
Quick heatmap plot in R:
```r
heatmap(matrix, Colv = NA, Rowv = NA,  scale = "none")
```