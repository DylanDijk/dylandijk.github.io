---
layout: post
title: Reproducing Kernel Hilbert Space - RKHS
date: 2023-03-11 18:50 +0000
math: true
categories: [Maths, Kernel Methods]
tags: [ML, Kernel Methods, RKHS]
---

In this post I give the main results of Reproducing Kernel Hilbert Space (RKHS). Taken from the introduction chapter of [this book](https://www.cambridge.org/core/books/an-introduction-to-the-theory-of-reproducing-kernel-hilbert-spaces/introduction/6441D25013A86ED66AFC17CD28C76CAF).

***

Let $X$ be a set and $\mathcal{F}(X, \mathbb{F})$ the set of functions from $X$ to $\mathbb{F}$, where $\mathbb{F}$ is a field. $\mathcal{F}(X, \mathbb{F})$ is a vector space over $\mathbb{F}$, with the usual operations of addition and scalar multiplication.

Now for the definition of a reproducing kernel Hilbert space (RKHS):

$\mathcal{H} \subseteq \mathcal{F}(X, \mathbb{F})$, is a RKHS on $X$ if:

1. $\mathcal{H}$ is a **vector subspace** of $\mathcal{F}(X, \mathbb{F})$.
2. $(\mathcal{H}, \langle \cdot, \cdot \rangle)$ is a **Hilbert space**.
3. $\forall x \in X$ the linear evaluation functional $E_x: \mathcal{H} \rightarrow \mathbb{F}$ defined by $E_x(f) = f(x)$ is bounded.

***

If $\mathcal{H}$ is a RKHS on $X$, there is a theorem that says that there is a unique element in $\mathcal{H}$ such that the linear evaluation functional can be given as an inner product with this element.  

In other words, $\forall x \in X$, $\exists k_x \in \mathcal{H}$ such that $\forall f \in \mathcal{H}$

$$\begin{align*}
f(x) = E_x(f) = \langle f, k_x \rangle
\end{align*}$$

$k_x$ is known as the **reproducing kernel** of the element $x$

Now if we define the function

$$\begin{align*}
K: X \times X \rightarrow \mathbb{F}\\
K(x, y) = \langle k_x, k_y \rangle
\end{align*}$$



Then $K$ is known as the **reproducing kernel** of $\mathcal{H}$.