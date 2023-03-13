---
layout: post
title: Reproducing Kernel Hilbert Space - RKHS
date: 2023-03-11 18:50 +0000
math: true
categories: [Maths, Kernel Methods]
tags: [ML, Kernel Methods, RKHS]
---

In this post I give the main results of Reproducing Kernel Hilbert Space (RKHS). Taken from the introduction chapter of [this book](https://www.cambridge.org/core/books/an-introduction-to-the-theory-of-reproducing-kernel-hilbert-spaces/introduction/6441D25013A86ED66AFC17CD28C76CAF).  
For later sections I used these [slides](http://www.gatsby.ucl.ac.uk/~gretton/coursefiles/RKHS2013_slides1.pdf) which I though were very clear.

***

# RKHS Definition

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
K: X &\times X \rightarrow \mathbb{F}\\
K(x, y) :&= k_y(x) \\
&= \langle k_y, k_x \rangle = \langle k_x, k_y \rangle \\
&= k_x(y)
\end{align*}$$

Then $K$ is known as the **reproducing kernel** of $\mathcal{H}$.  


Note that $k_x$ is an element of $\mathcal{H}$, so $K$ is taking the inner product of two elements of $\mathcal{H}$.

From the definition above of the reproducing kernel, this function is **symmetric** and **positive semi-definite**. (see bottom of this [wiki page](https://en.wikipedia.org/wiki/Positive-definite_kernel#Definition))

***


The **Moore-Aronszajn theorem** gives a converse of the construction given above. That is, for every symmetric positive semi-definite function $K: X \times X \rightarrow \mathbb{F}$, there exists a unique RKHS $\mathcal{H}$ on $X$ such that $K$ is the reproducing kernel of $\mathcal{H}$. 

***

# Mercer's Theorem

Below I give a simplified version of Mercer's theorem, excluding some technical details. The full version is theorem 11.15 in [Chapter 11](https://www.cambridge.org/core/books/an-introduction-to-the-theory-of-reproducing-kernel-hilbert-spaces/applications-of-rkhs-to-integral-operators/8AC0B047A0D4C081770508A2846039D1), of the book mentioned above.
Note that they assume at the start of that chapter that $X$ is assumed to be a compact subset of $\mathbb{R}^d$, and a Mercer Kernel is a continuous kernel.

**Mercer's theorem:**  
Let $K$ be a Mercer kernel on a compact subset $X$ of $\mathbb{R}^d$. Then there exists a countable collection of orthonormal continuous functions $ \lbrace e_i \rbrace_{i=1}^{\infty} $ on $X$ and non-negative numbers $ \lbrace \lambda_i \rbrace_{i=1}^{\infty}$ 
such that:

$$\begin{align*}
 K(x, y) = \sum_{i=1}^{\infty} \lambda_ie_i(x) e_i(y) \quad \forall x, y \in X
\end{align*}$$

# Kernel Trick in Machine Learning

In Machine Learning the "kernel trick" is often used, the "kernel trick" is where you replace the inner product of two vectors by a Kernel function. This is often motivated by saying that it can be thought of as mapping your vectors to some higher dimensional space and then taking the inner product in that space. 

Now a definition of a Kernel function is given by:

***

## Kernel Function

A function $K: \mathcal{X}  \times \mathcal{X} \rightarrow \mathbb{F}$  is a **kernel function** if there exists a Hilbert Space  $\mathcal{H}$ (not necessarily an RKHS) and a map $\phi : \mathcal{X} \rightarrow \mathcal{H}$, such that  $K(x, y) = \langle \phi(x), \phi(y) \rangle_{\mathcal{H}} \; \forall x, y \in X$

Note that every reproducing kernel is a kernel function, in that case the feature map is $\phi(x) = k_x$ and the feature space is the RKHS $\mathcal{H_k}$.

***

Now, if we are given a kernel $K$, there are infinitely many feature transformations, that is, there exist many different $\phi: \mathcal{X} \rightarrow \mathcal{H}$ such that we can write $K(x, y) = \langle \phi(x), \phi(y) \rangle_{\mathcal{H}}$. However, by Moore-Aronszajn theorem, there is a single unique RKHS $\mathcal{H}$ such that $K$ is the reproducing kernel of $\mathcal{H}$. 

At first when I learnt about RKHS I was confused by what 

