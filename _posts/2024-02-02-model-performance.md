---
layout: post
title: Model Performance
date: 2024-02-02 13:31 +0000
math: true
categories: [Statistics, Machine Learning]
---

**Main references**:
  - Classifaction metric - [blog posts](https://www.evidentlyai.com/classification-metrics)

# Model Performance

## Accuracy 

Accuracy is the most common metric for classification problems. It is the ratio of correctly predicted observation to the total observations.

$$
\begin{align*}
Accuracy &= \frac{\text{Correct predictions}}{\text{Total predictions}} \\[1em]
 &= \frac{TP+TN}{TP+TN+FP+FN}
\end{align*}
$$


However, for imbalanced datasets accuracy can give a false sense of achieving high performance.

The classical example, is the case of predicting the dominant hand in a population. By just predicting right hand for the entire population, the model will achieve a high accuracy (90% on average). 

## Precision

Precision tells us the precision of our predictions for a certain class. This is useful when we have an imbalanced dataset.

For example, if we let the positive class be the class with very few observations, left hand in the previous example. Then if you predict everyone as right handed, this will give a precision of 0.

$$
\begin{align*}
Precision &= \frac{\text{Correct predictions for the postive class}}{\text{Total positive class predictions}} \\[1em]
 &= \frac{TP}{TP+FP}
\end{align*}
$$

$$$$

We can think of Precision as accuracy resticted to observations from the positive class.

The formula, is the proportion of correct predictions for that class divided by the total number of predictions for that class.

## Recall

Recall then tells us the ability of our model to predict a class. 

$$
\begin{align*}
Recall &= \frac{\text{Correct predictions for the postive class}}{\text{Total actual positive class observations}} \\[1em]
 &= \frac{TP}{TP+FN}
\end{align*}

