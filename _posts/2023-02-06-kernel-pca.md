---
layout: post
title: Kernel PCA
date: 2023-02-06 20:38 +0000
---

In traditional PCA, as shown in my [PCA post](https://dylandijk.github.io/posts/pca/#best-low-rank-approximation), we look for a **linear subspace** to project the data vectors onto orthogonally to provide a low dimensional representation of the data.

However, restricting ourselves to a linear subspace may not be sufficient in order to reveal interesting structure in our data.

## Transform the data

The idea is that we transform the data vectors and then apply PCA. We then hope that performing PCA in this space reveals some structure/seperation in the data.

The question now is, which function do we choose to transform our data?

In this post, we denote the transformation function as the function $\phi: \mathbb{R}^p \rightarrow \mathcal{H}$. The naive approach would be to simply apply the function $\phi(\cdot)$ to every data vector, giving us a new data matrix which we denote as $\Phi^0$, and then apply PCA as usual.

However, if $\mathcal{H}$ is a high dimensional space then computing $\Phi^0$ is computationally expensive, and furthermore if $\mathcal{H}$ is infinite dimensional then it is computationally impossible to store this matrix.

It turns out that the kernel trick can be implemented, and we can retrieve the eigenvectors and eigenvalues without computing the transformations $\phi(\bx_i)$ directly. In particular instead of computing the $m \times m$ covariance matrix: 

$$\Phi^T\Phi$$

We compute the eingevevtor decomposition of the $n \times n$ Kernel/Gram matrix:

$$\Phi\Phi^T$$


