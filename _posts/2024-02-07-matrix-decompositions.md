---
layout: post
title: Matrix Decompositions
date: 2023-01-02 13:55 +0000
math: true
categories: [Maths, Linear Algebra]
---

**References**:
  1. Multivariate Statistics [Lecture notes](https://dylandijk.github.io/assets/pdf/ST412MultivariateStatsNotes.pdf) - by [Shahin Tavokoli](https://stavakoli.com/)
  2. Choleski decompostion - [blog post](https://www.statlect.com/matrix-algebra/Cholesky-decomposition) - [notes](https://www.stat.uchicago.edu/~lekheng/courses/302/notes8.pdf)
  3. Some very nice linear algebra [blog posts](https://gregorygundersen.com/blog/tags/la/)


***

## Spectral Decomposition and SVD

**Spectral Decomposition**  

Let $A$ be a symmetric matrix, then $A$ admits the following decomposition:

$$
\begin{align*}
    A = EDE^T
\end{align*}
$$

Where $E$ is the orthogonal matrix with columns being the eigenvectors of $A$. And $D$ is a diagonal matrix with eigenvalues of $A$. 

The **geometric** interpretation of this is that the linear transformation represented by any symmetric matrix is given by a rotation, then scaling of the axis, and then rotating back. This [video](https://www.youtube.com/watch?v=mhy-ZKSARxI&t=762s&ab_channel=VisualKernel) provides a visualisation.
 
**Singular Value Decomposition (SVD)**  

Any real $n \times p$ matrix $X$ admits the following decomposition:

$$
\begin{align*}
    X = ULV^T
\end{align*}
$$

Where $U$ is an $n \times n$ orthogonal matrix, $D$ is an $n \times p$ rectangular diagonal matrix with non-negative entries, and $V$ is a $p \times p$ orthogonal matrix.

This is saying that:

>"Every matrix is diagonal provided one uses the proper bases for the domain and range spaces."

### Relationship between the two

https://gregorygundersen.com/blog/2018/12/20/svd-proof/#1-gram-matrices-as-positive-semi-definite

## Cholesky decomposition

- Cholesky decomposition exists $\iff$ $M$ is symmetric and positive definite.
