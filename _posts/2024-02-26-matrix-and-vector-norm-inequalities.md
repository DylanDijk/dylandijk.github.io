---
layout: post
title: Matrix and Vector norm inequalities
date: 2024-02-26 16:34 +0000
math: true
---


From [this answer](https://math.stackexchange.com/a/1361853/762889):

$$
\begin{align*}
\|Ax\|_2 \leq \|A\|_F \|x\|_2
\end{align*}
$$


From [this question](https://math.stackexchange.com/q/4871629/762889) can do better with:

$$
\begin{align*}
\|Ax\|_2 \leq \|A\|_2 \|x\|_2
\end{align*}
$$

where $\|A\|_2$ is the spectral norm of $A$.

Reason we can do this is that operator norms are submultiplicative, with respect to the 
***

According to [this answer](https://math.stackexchange.com/questions/1681041/does-the-concept-of-submultiplicative-norm-make-sense-for-non-square-matrix?rq=1) operator norms (induced norms) are submultiplicative. This means that for any two matrices $A$ and $B$,

$$
\begin{align*}
\|AB\| \leq \|A\| \|B\|
\end{align*}
$$

***

Some great [notes](https://www.cs.utexas.edu/users/flame/laff/alaff-beta/chapter01-norms-matrix-submultiplicative.html) on matrix norms and submultiplicativity.