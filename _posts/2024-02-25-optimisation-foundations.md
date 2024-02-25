---
layout: post
title: Optimisation foundations
date: 2024-02-25 14:24 +0000
---

- Matteo theory of inference note chapter 8 is on MLE and talks about optimisation. Says stuff like:

        The terminology relates to the fact that a likelihood containing
        lots of information about θ will be sharply peaked (Fishers information matrix will have large magnitude eigenvalues).

Reminds me that I need to brush up on basics of multivariable calculus and optimisation.


- hessian
  - eigenvalues
- taylor expansion

In the one dimensional case:

**Taylor's theorem** $\quad$ Univariate case

$$
\begin{align*}
f(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \dots + \frac{f^{(k)}(a)}{k!}(x-a)^k + R_k(x)
\end{align*}
$$

where $R_k(x) = o((x-a)^k)$ as $x \to a$.

This naturally extends to the multivariate case. I give the definition in terms of the second order approximation.

**Taylor's theorem** $\quad$ Multivariate case

$$
\begin{align*}
f(\mathbf{x}) = f(\mathbf{a}) + \nabla f(\mathbf{a})^T(\mathbf{x}-\mathbf{a}) + \frac{1}{2}(\mathbf{x}-\mathbf{a})^T \nabla^2 f(\mathbf{a})(\mathbf{x}-\mathbf{a}) + R_2(\mathbf{x})
\end{align*}
$$

where $R_2(\mathbf{x}) = o(||\mathbf{x}-\mathbf{a}||^2)$ as $||\mathbf{x}-\mathbf{a}|| \to 0$.


- convexity
- directional derivative
  - why is gradient the direction of steepest ascent
- first and second order conditions
