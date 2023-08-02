---
layout: post
title: Factor Models
date: 2023-06-12 08:34 +0000
math: true
---

# Factor Models

**Main references**:
  1. [Multivariate analysis. Probability and
mathematical statistics](https://shop.elsevier.com/books/multivariate-analysis/mardia/978-0-08-057047-1)


## Model description 

The idea of a factor model is to represent each observed variable as a linear combination of some latent (not observed) factors, plus some noise. In particular, if we let $X$ be an $\mathbb{R}^p$ valued random variable, that represents the variables we observe. We then introduce, $F$, a $k$ dimensional random vector as the **factor**. We then assume that $X$ can be written as:

$$\begin{align*}
X = \mu + \Lambda F +  \xi
\end{align*}$$

Where the matrix of constants $\Lambda$ is referred to as the **loadings matrix**.

Additional assumptions of this model are:
- $\mathbb{E}(F) = 0$
- $\text{Var}(F) = \boldsymbol{I}_k$
- $\mathbb{E}(\xi) = 0$
- $\text{Var}(\xi) = \boldsymbol{\Psi} = \text{diag}(\psi_1, \dots, \psi_p)$
- $\text{Cov}(F, \xi) = 0$

And for the rest of this post, I will assume the data is centred, $\mathbb{E}(X) = 0$, i.e. $\mu = 0$.

The factor model with the assumption that $\text{Var}(F) = \boldsymbol{I}_k$ is often referred to as the **strict factor model**. 

## Properties

For this model with the assumptions listed above, on the random components, the covariance matrix of $X$ is given by:

$$\begin{align*}
\text{Cov}(X) = \Lambda \Lambda^T + \boldsymbol{\Psi}
\end{align*}$$

Hence if we look at the variance for a single variable, we can see that it is decomposed into the common variance from the factors and the unique variance from the noise.

$$\begin{align*}
\text{Var}(X_i) = \sum_{j=1}^k \lambda_{ij}^2 + \psi_i
\end{align*}$$


- **Scale-invariance**  
If the variables $X$ are rescaled then the factor model holds with the same factor $F$, but with rescaled loadings and noise covariance matrix.

- **Non-uniqueness**  
If the factor model holds then the loadings matrix and factors are not unique. In particular if we have an orthogonal matrix $G$ we can write:

$$\begin{align*}
X = \Lambda F + \xi = (\Lambda G) (G^T F) + \xi
\end{align*}$$

We now cover the estimation of the parameters $\Lambda$ and $\boldsymbol{\Psi}$, under two frameworks: the standard factor model and the normal linear factor model. In practice we observe a data matrix $X$ and we want to estimate the parameters using the data.

## Relation to PCA

If we just look at how the covariance matrix is decomposed in either model.  
Let $\mathbf{\Gamma}_x$ denote the covariance matrix. 

- PCA: $\quad \mathbf{\Gamma}_x = \mathbf{\Gamma}_{x_{[q]}} + \mathbf{\Gamma}_{\xi}$
- FM : $\quad \mathbf{\Gamma}_x = \mathbf{\Lambda} \mathbf{\Lambda}^T + \mathbf{\Psi}$

That is they are decomposed into a rank $q$ matrix plus another matrix. Where the representation used in PCA (no modelling assumptions), the additional matrix is not necessarily diagonal.



## Standard factor model

$$\begin{align*}
X = \Lambda F + \xi
\end{align*}$$




### Estimation

The loadings matrix $\Lambda$ and the covariance matrix of the noise $\boldsymbol{\Psi}$, need to be estimated. Algorithms for estimating these parameters include: ...

Once we have an estimate 



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
I have previously created [these slides](https://dylandijk.github.io/assets/pdf/SM2_EM_Factor_Model.pdf), that give a brief description and provides the derivation of the EM steps (after the references).