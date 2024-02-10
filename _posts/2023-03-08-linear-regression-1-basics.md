---
layout: post
title: Linear Regression
date: 2023-03-08 11:29 +0000
categories: [Statistics, Regression]
tags: [ML, Statistics, Linear Regression] 
math: true
---

In this post I will describe the setup of linear regression, and main results.  
I will be looking at the **fixed design setting**, which is where we assume that the covariates $x_i^0$ are fixed, and then model the outcome variable $y_i^0$ as a linear function of the covariates plus some **random error** $\epsilon_i$.

Throughout I will be denoting the uncentered response variable vector by $Y^0$, and the uncentered design matrix by $\mathbf{X}^0$. The centred versions will be denoted by $Y$ and $\mathbf{X}$ respectively, where $\mathbf{X}$ has been centred column wise.

**References:**  
1. [Lecture notes](https://mfasiolo.github.io/TOI/notes.pdf) - Chapter 3

***

## Model Setup

$$\begin{align*}
y_i^0 = \alpha + \beta^T x_i^0 + \epsilon_i, \quad i = 1, \dots, n 
\end{align*}$$

So far I will not make any assumptions about the distribution of the errors $\epsilon_i$. But will makes these clear when making statements about inference and estimation.

I emphasise that the error terms $\epsilon_i$ are the only **random** part on the RHS of the equation. The covariates $x_i^0$ are fixed, and the parameters $\alpha$ and $\beta$ are unknown.

The objective is to estimate the parameters $\alpha$ and $\beta$, and the standard approach is to use the **least squares** estimator:

$$\begin{align*}
(\hat{\alpha}, \hat{\beta}) := \underset{\alpha, \beta}{\argmin}||Y^0 - (\alpha \mathbf{1} + \mathbf{X}^0 \beta)||_2^2
\end{align*}$$

Here we are using the usual convention, that a real number added to a vector we add it to each element of the vector.


***
This least squares loss function can be motivated by assuming that the outcome variables $y_i^0$, conditional on the predictors $x_i^0$, are independent samples from the normal distribution $N(\alpha + \beta^T x_i^0, \sigma^2)$. This assumption can be equivalently made, by assuming the errors $\epsilon_i$ are i.i.d samples from the normal distribution $N(0, \sigma^2)$.

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

From the objective:
$$\begin{align*}
(\hat{\alpha}, \hat{\beta}) := \underset{\alpha, \beta}{\argmin}||Y^0 - (\alpha \mathbf{1} + \mathbf{X}^0 \beta)||_2^2
\end{align*}$$





We have the OLS solutions:  

$$\begin{align*}
\hat{\alpha} &= \bar{Y}^0 - \hat{\beta}^T \bar{X}^0 \\
\hat{\beta} &= (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^TY
\end{align*}
$$

Can see that $\hat{\beta}$ is a linear function of the response variable $Y$.

<details>

  <summary markdown="span" style="color:#4863A0">Proof:</summary>
<div markdown="1">

- Solution for intercept $\alpha$:

$$\begin{align*}
||Y^0 - (\alpha + \mathbf{X}^0 \beta)||_2^2 = (Y^0 - (\alpha \mathbf{1} + \mathbf{X}^0 \beta))^T(Y^0 - (\alpha \mathbf{1} + \mathbf{X}^0 \beta)) \\
= (Y^0)^T Y^0 - 2(Y^0)^T(\alpha \mathbf{1} + \mathbf{X}^0 \beta) + (\alpha \mathbf{1} + \mathbf{X}^0 \beta)^T(\alpha \mathbf{1} + \mathbf{X}^0 \beta) 
\end{align*}$$

Minimising w.r.t to the constant $\alpha$, so just looking at terms that depend on $\alpha$:

$$\begin{align*}
\frac{\partial}{\partial \alpha} - \alpha (Y^0)^T \mathbf{1} + \alpha (\mathbf{1}^T \mathbf{1}) \alpha + 2\beta^T \mathbf{X}^0 \alpha \mathbf{1} \\
= -2(Y^0)^T \mathbf{1} + 2\alpha n + 2\beta^T \mathbf{X}^0 \mathbf{1}
\end{align*}$$

Setting to zero gives:

$$\begin{align*}
\hat{\alpha} &= \frac{1}{n}\left[\left(\sum_{i = 1}^{n}y_i^0 - \left(\sum_{i = 1}^{n}(x_i^0)^T \beta \right) \right)\right] \\
&= \bar{Y}^0 - \bar{X}^0 \beta
\end{align*}$$

Where $\bar{X}^0$ is the mean row vector of the design matrix. Hence plugging $\hat{\alpha}$ back into the objective gives:

$$
\begin{align*}
Y^0 - (\hat{\alpha} \mathbf{1} + \mathbf{X}^0 \beta) = (Y^0 - (\bar{Y}^0 \mathbf{1} - (\bar{X}^0 \beta)\mathbf{1} + \mathbf{X}^0 \beta)) \\
= (Y^0 - \bar{Y}^0 \mathbf{1}) - (\mathbf{X}^0 - \bar{X}^0 \mathbf{1})\beta \\
= (Y -\mathbf{X} \beta)
\end{align*}
$$

Where $Y$ and $\mathbf{X}$ are the centered response variable and design matrix respectively.  


- Solution for intercept $\beta$:




***
</div>
</details>

Least squares looks for $\beta$ that minimises the least squares distance, from $Y$ to a point in the column span of the design matrix $\mathbf{X}$. Therefore $\beta$ is chosen such that $Y$ is orthogonally projected on to the column space of $\mathbf{X}$. Recalling that the matrix that orthogonaly projects vectors onto the column space of a matrix $\mathbf{X}$ is the projection matrix:

$$
\mathbf{X}(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T
$$

***

### Unbiased

Under the model setup, and the <span style="color:red">additional assumption</span> that $\mathbb{E}(\mathbf{\epsilon}) = 0$,  
we have that:

$$
\begin{align*}
&\mathbb{E}(Y^0) = \alpha + \mathbf{X}^0 \beta \\  
&\mathbb{E}(\bar{Y}^0) = \alpha + \bar{X}^0 \beta
\\
\implies &\mathbb{E}(Y) = \mathbf{X} \beta
\end{align*} 
$$  

Using this we can show that $\hat{\beta}$ is an unbiased estimator of $\beta$:

$$
\begin{align*}
\mathbb{E}(\hat{\beta}) &= \mathbb{E}((\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^TY) \\
&= (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbb{E}(Y) \\
&= (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{X}\beta \\
&= \beta
\end{align*}
$$

### Gauss-Markov Theorem

We have shown that $\hat{\beta}$ is unbiased, under the assumption that $\mathbb{E}(\mathbf{\epsilon}) = 0$.  
If we <span style="color:red">further assume</span>  that $Var(\mathbf{\epsilon}) = \sigma^2 I$, then the Gauss-Markov Theorem holds.

**The Gauss-Markov Theorem**  
For all constant vectors $\mathbf{a} \in \mathbb{R}^p$, and linear unbiased estimators $\tilde{\beta}$ (linear in $Y$ i.e $t^TY$). 
$$
\begin{align*}
Var(\mathbf{a}^T\hat{\beta}) \leq Var(\mathbf{a}^T\tilde{\beta})
\end{align*}
$$

In words, under the assumptions:  
- $\mathbb{E}(\mathbf{\epsilon}) = 0$
- $Var(\mathbf{\epsilon}) = \sigma^2 I$, uncorrelated and homoscedastic errors.

The OLS estimator $\hat{\beta}$ is the best linear unbiased estimator (BLUE) of $\beta$. Where by best we mean it has the lowest variance.


## Intervals and Testing

### Model parameters
In order to carry out testing and construct confidence intervals, we additionally assume that:  

$$
\begin{align*}
\epsilon \sim N(0, \sigma^2 I)
\end{align*}
$$

Under this assumption we then have that:

$$
\begin{align*}
\hat{\beta} \sim N(\beta, \sigma^2 (\mathbf{X}^T\mathbf{X})^{-1})
\end{align*}
$$

Therefore in order to have a pivotal quantity we require an estimate of the variance of the errors $\sigma^2$. 

An unbiased estimator of $\sigma^2$:

$$
\begin{align*}
\hat{\sigma}^2 = \frac{\|Y - X\hat{\beta}\|^2}{n - p}
\end{align*}
$$

and therefore an unbiased estimator of the variance of $\hat{\beta}$:

$$
\begin{align*}
\hat{\sigma}^2 (\mathbf{X}^T\mathbf{X})^{-1}
\end{align*}
$$

it can then be shown that:

$$
\begin{align*}
\frac{\hat{\beta_i} - \beta_i}{\hat{\sigma}_{\hat{\beta}_i}} \sim t_{n-p}
\end{align*}
$$

and then this can be used to construct confidence intervals and carry out hypothesis tests.

>An important thing to note is that when carrying out linear regression in practice, in R for example, the estimators listed above are computed using the QR decomposition of the design matrix, which is more numerically stable. 
{: .prompt-info }


### Prediction intervals

There are two types of prediction intervals that may want to be estimated. The **prediction of a new observation** given a feature vector $x$, and the **prediction of the mean response** given a feature vector $x$.

This stack exchange [answer](https://stats.stackexchange.com/questions/16493/difference-between-confidence-intervals-and-prediction-intervals) explains the difference. 


***

**predicting a new response**:

When predicting a new response we need to take into account the variance associated with estimating $\beta$ and then the variance the error $\epsilon$ in our model. And we assume that the error is independent of $\hat{\beta}$, that is can think of getting our expected response:

$$
\begin{align*}
\hat{\beta}^T x
\end{align*}
$$

and then the response that we do not observe will be: 

$$
\begin{align*}
\tilde{y} = \hat{\beta}^T x + \epsilon
\end{align*}
$$

for some additional independent error.

We therefore have that:

$$
\begin{align*}
\tilde{y} \sim N({\beta}^T x \, , \sigma^2(1 + x^T(\mathbf{X}^T\mathbf{X})^{-1}x) \, )
\end{align*}
$$

and similart the t-statistic for the coefficents, we have the following t-statistic for the prediction of a **new response**:

$$
\begin{align*}
\frac{\tilde{y} - \hat{\beta}^T x}{\hat{\sigma}\sqrt{1 + x^T(\mathbf{X}^T\mathbf{X})^{-1}x}} \sim t_{n-p}
\end{align*}
$$

hence we can construct the following prediction interval:

$$
\begin{align*}
x^T\hat{\beta} \pm t_{n-p}(\alpha) \hat{\sigma}\sqrt{1 + x^T(\mathbf{X}^T\mathbf{X})^{-1}x}
\end{align*}
$$

Then for the mean response confidence interval we just remove the plus 1 that appears in the variance.


