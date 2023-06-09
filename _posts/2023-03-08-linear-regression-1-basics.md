---
layout: post
title: Linear Regression 1 - Basics
date: 2023-03-08 11:29 +0000
categories: [Statistics, Regression]
tags: [ML, Statistics, Linear Regression] 
math: true
---

In this post I will describe the setup of linear regression, and main results.  
I will be looking at the **fixed design setting**, which is where we assume that the covariates $x_i^0$ are fixed, and then model the outcome variable $Y_i^0$ as a linear function of the covariates plus some **random error** $\epsilon_i$.

***

## Setup

$$\begin{align*}
Y_i^0 = \alpha + \beta^T x_i^0 + \epsilon_i, \quad i = 1, \dots, n 
\end{align*}$$

Additioanlly, we assume that $\text{Cov}(\boldsymbol{\epsilon}) = \sigma^2 I, \; \mathbb{E}(\boldsymbol{\epsilon}) = 0$, where $\boldsymbol{\epsilon} = (\epsilon_1, \dots, \epsilon_n)^T$.  

I emphasise that the error terms $\epsilon_i$ are the only **random** part on the RHS of the equation. The covariates $x_i^0$ are fixed, and the parameters $\alpha$ and $\beta$ are unknown.

The objective is to estimate the parameters $\alpha$ and $\beta$, and the standard approach is to use the **least squares** estimator:

$$\begin{align*}
(\hat{\alpha}, \hat{\beta}) := \underset{\alpha, \beta}{\argmin}||Y^0 - (\alpha + \mathbf{X}^0 \beta)||_2^2
\end{align*}$$

Here we are using the usual convention, that a real number added to a vector we add it to each element of the vector.


***
This least squares loss function can be motivated by assuming that the outcome variables $Y_i^0$, conditional on the predictors $x_i^0$, are independent samples from the normal distribution $N(\alpha + \beta^T x_i^0, \sigma^2)$. This assumption can be equivalently made, by assuming the errors $\epsilon_i$ are i.i.d samples from the normal distribution $N(0, \sigma^2)$.

What I mean by motivated, is that the MLE of $\alpha$ and $\beta$, under this probabilistic assumption is equivalent to the least squares estimator.  

<details>

  <summary markdown="span" style="color:#4863A0">Showing that Least Squares is Equivalent to MLE under Probabilistic Assumptions</summary>
<div markdown="1">

Assume $\{(\mathbf{x}_i, y_i) \mid i = 1, \dots n\}$ are repeated independent samples from random variables $\mathbf{X}$ and $Y$ respectively. With $Y \mid \mathbf{X} \sim N(f(\mathbf{x};\mathbf{w}), \sigma^2)$. 

We then can write that:

$$\begin{align}
    p(y_1, \dots y_n \mid \mathbf{x}_1, \dots \mathbf{x}_n; \bw, \sigma) &= \frac{\prod_{i=1}^{n}{p(\mathbf{x}_i,y_i;\bw, \sigma)}}{\prod_{i=1}^{n}{p(\mathbf{x}_i;\bw, \sigma)}} \\
    &= \prod_{i=1}^{n}{p(y_i \mid \mathbf{x}_i;\bw, \sigma)}
\end{align}$$

And therfore under the distributional assumption the log-likelihood is given by:

$$\begin{align}
  \log(p(y_1, \dots y_n \mid \mathbf{x}_1, \dots \mathbf{x}_n; \bw, \sigma)) = C + \frac{\sum_{i=1}^{n}{(y_i - f(\mathbf{x}_i;\bw))^2}}{2\sigma^2}
\end{align}$$

And hence the MLE of $\bw$ is given by solving the least squares problem.

Alternatively, it can be sometimes be more easily thought of in the fixed design setting, where the covariates $x_i^0$ are fixed. And then we sample the $y_i$'s independently from the normal distribution $N(\alpha + \beta^T x_i^0, \sigma^2)$. 

In that case we would just write the density as a function of the constants $\mathbf{x}_i$:

\begin{align}


</div>
</details>

***

## Estimation

$$\begin{align*}
\hat{\alpha} &= \bar{Y}^0 - \hat{\beta}^T \bar{X}^0 \\
\hat{\beta} &= (X^TX)^{-1}X^TY 
\end{align*}$$

Under the model setup we have that, $\mathbb{E}(Y^0) = \alpha + \mathbf{X}^0 \beta$.  
Therefore the OLS estimate $\hat{\mu}^0$ of  $\mathbb{E}(Y^0)$ is given by $\hat{\mu}^0 = \hat{\alpha} + \mathbf{X}^0 \hat{\beta}$.

If we let $Y = Y^0 - \frac{1}{n}\sum_{i=1}^n Y_i^0$, then under the model setup we have that $\mathbb{E}(Y) = \mathbf{X} \beta$.  
Therefore the OLS estimate $\hat{\mu}$ of $\mathbb{E}(Y)$ is given by $\hat{\mu} = \mathbf{X} \hat{\beta}$.

### Unbiased

$$\begin{align*}
\mathbb{E}(\hat{\mu}) &= X(X^TX)^{-1}X^T \mathbb{E}(Y) = X(X^TX)^{-1}X^T \mathbf{X} \beta = X \beta \\
 &= \mathbb{E}(Y)
\end{align*}$$