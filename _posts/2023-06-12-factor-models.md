---
layout: post
title: Factor Models
date: 2023-06-12 08:34 +0000
---

# Factor Models

The idea of a factor model is to represent each observed variable as a linear combination of some latent (not observed) factors, plus some noise. In particular, if we let $X$ be an $\mathbb{R}^p$ valued random variable, that represents the variables we observe. We then introduce, $F$, a $k$ dimensional random vector as the factors. We then assume that $X$ can be written as:

$$\begin{align*}
X = \mu + \Lambda F + \epsilon
\end{align*}$$

## Normal linear factor model

Another formulation of the factor model, makes distribution assumptions on the random components of the model. 

\begin{itemize}
    \item $X | F \sim N_p(\bLambda F, \boldsymbol{\Psi})$
    \item $F \sim N_k(0, \boldsymbol{I}_k)$ 
\end{itemize}
