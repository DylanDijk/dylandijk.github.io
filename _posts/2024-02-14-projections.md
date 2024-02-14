---
layout: post
title: Projections
date: 2024-02-14 16:13 +0000
math: true
categories: [Maths, Linear Algebra]
---

**References**:
  1. [Online lecture notes](https://textbooks.math.gatech.edu/ila/projections.html)


## Projections

In linear algebra a projection is a linear map from a vector space to itself $P:V \rightarrow V$, often a subspace, such that  

$$P^2 = P$$

From this we can deduce the following properties:

- We can write any point in the space $V$ as the sum of an element from $Im(P)$ and $Ker(P)$.
- The eigenvalues of a projection matrix are 0 or 1.


## Orthogonal Projections

An **orthogonal projection** 



- An **orthogonal projection** is a projection for which the image and the null space are orthogonal subspaces
- A projection is orthogonal if and only if it is **self-adjoint**/**symmetric**
	- A self-adjoint matrix with real entries is called symmetric

> If we have a vector space $V$ with subspace $U$, out of all projections with image $U$. The projection that minimises the distance from a point $v \in V$ to its projected element $u \in U$, is **the** orthogonal projection.
{: .prompt-tip }

**Proof:**  

Let $v \in V$ and $u \in U$ and $\pi()$ be the orthogonal projector. 
By the Pythagorean theorem we have that:
$||v - u||^2 = ||v - \pi(v)||^2 + ||\pi(v) - u||^2 \geq ||v - \pi(v)||^2$  

So $\pi(v) \in Im(\pi)$ and $u \in Im(\pi)$. 
Therefore $\pi(v) - u\in Im(\pi)$.

$\pi(v - \pi(v)) = 0$ therefore $v - \pi(v) \in ker(\pi)$

Therefore $v - \pi(v)$ and  $\pi(v) - u$ are orthogonal, so can use  Pythagorean theorem.

Now can see that the minimum is attained if we let $u = \pi(v)$. I.e the projection to the subspace U that minimises the distance is the orthogonal projection.




- In an inner-product space, the  **Pythagorean theorem**  states that for any two orthogonal vectors  **v**  and  **w**  we have 
$||v + w||^2 = ||v||^2 + ||w||^2$


The matrix that represents the orthogonal projection onto the column space of a matrix $X$ is given by:

$$X(X^TX)^{-1}X^T$$

In addition, as for any full rank/invertible matrix $A$, $XA$ will have the same column space as $X$. And hence it makes sense that substituting $X$ with $XA$ will give the same projection matrix above.