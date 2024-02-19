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

**Singular Value Decomposition (SVD)**  

Any real $n \times p$ matrix $X$ admits the following decomposition:

$$
\begin{align*}
    X = ULV^T
\end{align*}
$$

Where $U$ is an $n \times n$ orthogonal matrix, $L$ is an $n \times p$ rectangular diagonal matrix with non-negative entries ([singular values](https://dylandijk.github.io/posts/eigenvectors/#singular-values)), and $V$ is a $p \times p$ orthogonal matrix.

This is saying that:

>"Every matrix is diagonal provided one uses the proper bases for the domain and range spaces."

And the **geometric** interpretation of this is that the linear transformation represented by any matrix is given by: a rotation, then scaling of the axis by the singular vlaues, and then rotating the axis again. Figure 4 in this [blog post](https://gregorygundersen.com/blog/2018/12/10/svd/) visualises this.

>This also helps to explain to me why we take such an interest in eigenvalues/singular values, as they tells us by how much a linear transformation distort the spaces. This then helps to explain why matrices with zero valued eigenvalues are not invertible, as they collapse the space. In addition, why orthogonal matrices have all eigenvalues equal to 1, as they do not distort the space. 
{: .prompt-info }


***

**Spectral Decomposition**  

Let $A$ be a symmetric matrix, then $A$ admits the following decomposition:

$$
\begin{align*}
    A = EDE^T
\end{align*}
$$

Where $E$ is the orthogonal matrix with columns being the eigenvectors of $A$. And $D$ is a diagonal matrix with eigenvalues of $A$. 

This has the same **geometric** interpretation but now the second rotation is the same as the first. This [video](https://youtu.be/mhy-ZKSARxI?t=724) provides a visualisation.
 

### Relationship between the two

https://gregorygundersen.com/blog/2018/12/20/svd-proof/#1-gram-matrices-as-positive-semi-definite

http://theanalysisofdata.com/probability/C_5.html#:~:text=The%20following%20corollary%20shows%20that,are%20the%20eigenvectors%20of%20A.

## Cholesky decomposition

- Cholesky decomposition exists $\iff$ $M$ is symmetric and positive definite.
