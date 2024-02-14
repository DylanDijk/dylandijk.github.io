---
layout: post
title: Eigenvectors
date: 2023-01-02 13:54 +0000
math: true
categories: [Maths, Linear Algebra]
---

# Linear Algebra - Eigenvectors

## Singular values

**Singular values** of a matrix $A$, are the square roots of the eigenvalues of $A^TA$

If $A$ is symmetric the eigenvalues of $A^TA$ are the squared eigenvalues of $A$.

<details>
    <summary markdown="span" style="color:#4863A0">Proof</summary>
<div markdown="1">

$$\begin{align*}
Ax &= \lambda x \\
A^TAx &= AAx = \lambda Ax = \lambda^2 x
\end{align*}$$

</div>
</details>

Therefore the singular values of a symmetric matrix are the absolute values of its eigenvalues.

## Positive definiteness

- An $n \times n$ matrix $M$ is **positive definite** if $x^T M x > 0$ for all non-zero vectors $x \in \mathbb{R}^n$.
- An $n \times n$ matrix $M$ is **positive semi-definite** if $x^T M x \geq 0$ for all non-zero vectors $x \in \mathbb{R}^n$.

- Covariance matrices are positive semi-definite.  
The quadratic form can be equal to zero if $\exists x \in \mathbb{R}^n$ such that $x^T (X - \mu) = 0$ a.s. In other words, if one of the random variables is a linear combination of the others.




