---
layout: post
title: Factor Models
date: 2023-06-12 08:34 +0000
math: true
---

# Factor Models

The idea of a factor model is to represent each observed variable as a linear combination of some latent (not observed) factors, plus some noise. In particular, if we let $X$ be an $\mathbb{R}^p$ valued random variable, that represents the variables we observe. We then introduce, $F$, a $k$ dimensional random vector as the factors. We then assume that $X$ can be written as:

$$\begin{align*}
X = \mu + \Lambda F + \epsilon
\end{align*}$$

For the rest of this post, I will assume the data is centred, $\mathbb{E}(X) = 0$.

**Main references**:
  1. [Multivariate analysis. Probability and
mathematical statistics](https://shop.elsevier.com/books/multivariate-analysis/mardia/978-0-08-057047-1)
  2. 


## Standard factor model

$$\begin{align*}
X = \Lambda F + \epsilon
\end{align*}$$




## Normal linear factor model

Another formulation of the factor model, makes distributional assumptions on the random components of the model. 

$$
\begin{gather*}
    X | F \sim N_p(\mathbf{\Lambda} F, \boldsymbol{\Psi}) \\
    F \sim N_k(0, \boldsymbol{I}_k) 
\end{gather*}
$$

An advantage of this formulation, is that statistical tests that test for the $k$ common factors are sufficient to describe the data (see [1.] section 9.5).

With these additional probabilistic assumptions, the covariance parameters and loadings matrix can be derived via maximum likelihood estimation.
I have previously created [these slides](https://github.com/DylanDijk/dylandijk.github.io/blob/main/assets/pdf/SM2_EM_Factor_Model.pdf), that give a brief description and provides the derivation of the EM steps (after the references).