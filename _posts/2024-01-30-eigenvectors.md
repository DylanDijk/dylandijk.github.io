---
layout: post
title: Eigenvectors
date: 2023-01-02 13:54 +0000
math: true
---

# Linear Algebra - Eigenvectors

**references**:
  1. Choleski decompostion - [blog post](https://www.statlect.com/matrix-algebra/Cholesky-decomposition) - [notes](https://www.stat.uchicago.edu/~lekheng/courses/302/notes8.pdf)

***

## Positive definiteness

- An $n \times n$ matrix $M$ is **positive definite** if $x^T M x > 0$ for all non-zero vectors $x \in \mathbb{R}^n$.
- An $n \times n$ matrix $M$ is **positive semi-definite** if $x^T M x \geq 0$ for all non-zero vectors $x \in \mathbb{R}^n$.

- Covariance matrices are positive semi-definite.  
The quadratic form can be equal to zero if $\exists x \in \mathbb{R}^n$ such that $x^T (X - \mu) = 0$ a.s. In other words, if one of the random variables is a linear combination of the others.

## Cholesky decomposition

- Cholesky decomposition exists $\iff$ $M$ is symmetric and positive definite.



