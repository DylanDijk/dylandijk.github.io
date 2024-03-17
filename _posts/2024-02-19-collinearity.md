---
layout: post
title: Collinearity and Confounding
date: 2024-02-19 09:17 +0000
math: true
categories: [Statistics, Regression]
tags: [Statistics, Linear Regression]
---

# Confounding variables

A classical example of a confounding variable, and that correlation does not imply causation, is the incorrect assumption that an increase in ice cream sales causes an increase in drowning incidents. The ground truth in reality, is that good weather causes both, which leads to the correlation between the two. 

This is an example of a confounding variable possible leading us to believe there is some causal relationship between variables when there is not.

Another issue of confounding variables, is that if we would like to measure the effect of a predictor on an outcome variable, not including the hidden variable will lead to an inccorrect estimation of the effect size. For example, if we generate variable $h$ and $x$ that correlated 

```r
library(MASS) 
V <- matrix(c(1,.95,.95,1),2,2) 
n <- 1000 
X <- mvrnorm(n,rep(0,2),Sigma = V)
x <- X[,1];h <- X[,2]
```

and generate an outcome variable as a combination of the two predictors. 

```r
y <- x + h + rnorm(n)
```

If we then only include one of the predictors
```r
summary(lm(y ~ x ))
```
we retrieve the following output, which shows that the effect of $x$ has been overestimated. Due to the fact that $x$ is positive correlated with $h$.
```r
Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.02875    0.03429   0.838    0.402    
x            1.96329    0.03389  57.929   <2e-16 ***
```

## Randomised trials

We can now think or a real life experiment where this issue will exist. Lets say we want to measure the impact of amount of exercise a person performs and their fat mass. Well there will exist a large amount of confounders, e.g the wealth of an individual. If a person is wealthy, they are likely to have more time to exercise, or afford a PT, but also likely to have a higher quality of life and therefore affecting there levels of fat mass. That is, it is a variable that is associated to both the outcome of interest and the predictor of interest.
And it is the relationship between the two variables, wealth and exercise amount, that will cause the estimated effect of exercise to be incorrect. The common way to solve this problem, would be to use a randomised trial. That is randomly assign participants to different exercise regimes. The fact that it is now randomly assigned, removes the association between other variable contributing to fat mass and the predictor of interest.

### Mathematical justification 

Conside that our outcome $y$ is generatd from a linear model, with the design matrix $X'$ consisting of matrices $X'= (X, H)$.

If $H$ is **not included** in the model then our estimate is:

$$
\hat{\boldsymbol{\beta}}_x = (\mathbf{X}^{\mathrm{T}} \mathbf{X})^{-1} \mathbf{X}^{\mathrm{T}} \mathbf{y} .
$$

If $H$ is **included** in the model then our estimate is:

$$
\left[\begin{array}{l}
\hat{\boldsymbol{\beta}}_x \\
\hat{\boldsymbol{\beta}}_h
\end{array}\right]=\left[\begin{array}{ll}
\mathbf{X}^{\mathrm{T}} \mathbf{X} & \mathbf{X}^{\mathrm{T}} \mathbf{H} \\
\mathbf{H}^{\mathrm{T}} \mathbf{X} & \mathbf{H}^{\mathrm{T}} \mathbf{H}
\end{array}\right]^{-1}\left[\begin{array}{l}
\mathbf{X}^{\mathrm{T}} \\
\mathbf{H}^{\mathrm{T}}
\end{array}\right] \mathbf{y} .
$$

Clearly if $\mathbf{X}^{\mathrm{T}} \mathbf{H} \neq \mathbf{0}$ then $\tilde{\boldsymbol{\beta}}_x \neq \hat{\boldsymbol{\beta}}_x$, that is the missing confounders in $\mathbf{H}$ interfere with the estimation of $\boldsymbol{\beta}_x$. However if the confounders are independent of $\mathbf{X}$, then at least in the large sample limit, $\mathbf{X}^{\mathrm{T}} \mathbf{H}=\mathbf{0}$, so that

$$
\left[\begin{array}{l}
\hat{\boldsymbol{\beta}}_x \\
\hat{\boldsymbol{\beta}}_h
\end{array}\right]=\left[\begin{array}{cc}
\mathbf{X}^{\mathrm{T}} \mathbf{X} & \mathbf{0} \\
\mathbf{0} & \mathbf{H}^{\mathrm{T}} \mathbf{H}
\end{array}\right]^{-1}\left[\begin{array}{l}
\mathbf{X}^{\mathrm{T}} \\
\mathbf{H}^{\mathrm{T}}
\end{array}\right] \mathbf{y}=\left[\begin{array}{cc}
\left(\mathbf{X}^{\mathrm{T}} \mathbf{X}\right)^{-1} & \mathbf{0} \\
\mathbf{0} & \left(\mathbf{H}^{\mathrm{T}} \mathbf{H}\right)^{-1}
\end{array}\right]\left[\begin{array}{l}
\mathbf{X}^{\mathrm{T}} \\
\mathbf{H}^{\mathrm{T}}
\end{array}\right] \mathbf{y} .
$$

This shows that if $\mathbf{X}^{\mathrm{T}} \mathbf{H}=\mathbf{0}$, i.e the confounders are independent of the predictors, then including the hidden variables or not does not affect the estimate of predictors of interest.
