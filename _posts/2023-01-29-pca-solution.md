---
layout: post
title: PCA - Solution
date: 2023-01-29 12:18 +0000
math: true
---

In a previous post we introduce PCA, and two equivalent objective definitions. In this post we now give the exact solutions to PCA.

We saw that the objective can be written as:

$$
\begin{align*} \underset{V \in \mathbb{R}^{p \times d}}{\text{argmax}} \quad &\text{Tr}(V^TSV) \\ &\text{s.t} \quad V^TV = I_d \end{align*}
$$

Where $S = \frac{X^TX}{n-1}$ is the sample covariance matrix.

***

**Theorem**  $\quad$ Spectral Decomposition.  
Let $A$ be a symmetric matrix, then $A$ admits the following decomposition:

$$
\begin{align*}
    A = UDU^T
\end{align*}
$$

Where $U$ is an orthogonal matrix, and $D$ is a diagonal matrix with real entries.

**Theorem**  $\quad$ Singular Value Decomposition (SVD).  
Any real $n \times p$ matrix $X$ admits the following decomposition:

$$
\begin{align*}
    X = UDE^T
\end{align*}
$$

Where $U$ is an $n \times n$ orthogonal matrix, $D$ is an $n \times p$ rectangular diagonal matrix with non-negative entries, and $V$ is a $p \times p$ orthogonal matrix.

***

Let $U$ denote a matrix with the right singular vectos of $X$. The PC loadings are then given by the first $k$ columns of $U$. 

$$
\begin{align*}
    V = U_k
\end{align*}
$$

Therefore, the reconsrtuction error with respect to the frobenius norm is given by:

$$
\begin{gather*}
    \|X - X V V^T\|_F = \|X - X U_k U_k^T\|_F = \| X - E D U^T U_k U_k^T \|_F \\
    = \| X - E_kD_kU_k\|_F = \| X - X_k \|_F
\end{gather*}
$$

The **Ekhart-Young theorem** tells us that the best rank $k$ approximation to $X$, under unitarily invariant norms, is given by $X_k = U_k D_k E_k^T$. Note that both the the Frobenius norm and the spectral norm are unitarily invariant.