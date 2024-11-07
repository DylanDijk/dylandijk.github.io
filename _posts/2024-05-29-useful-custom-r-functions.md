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
heatmap_scale = function(matrix1, matrix2, main1 = NULL, main2 = NULL){
    
  global_min <- min(matrix1, matrix2)
  global_max <- max(matrix1, matrix2)
  
  my_palette <- colorRampPalette(c("blue", "white", "red"))(n = 299)
  
  heatmap(matrix1, Colv = NA, Rowv = NA, scale = "none",
          col = my_palette, breaks = seq(global_min, global_max, length.out = 300), main = main1)
  heatmap(matrix2, Colv = NA, Rowv = NA, scale = "none",
          col = my_palette, breaks = seq(global_min, global_max, length.out = 300), main = main2)
  
}
```
Quick heatmap plot in R:
```r
heatmap(matrix, Colv = NA, Rowv = NA,  scale = "none")
```

# Eigen-analysis

Plot eigen values of covariance matrix
```r
plot_eig_values = function(x, main = NULL){
     cov_d = (1/nrow(x)) * ( t(x) %*% x )
     cov_d_eig = eigen(cov_d)
     plot(cov_d_eig$values, main = main)
}
```

# Max index of matrix

Get the row and column number of largest element of matrix
```
max_ind = function(mat){
  max_index <- which(mat == max(mat), arr.ind = TRUE)
  max_index
}

```