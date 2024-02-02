---
layout: post
title: Model Performance
date: 2024-02-02 13:31 +0000
categories: [Statistics, Machine Learning]
math: true
---

**Main references**:
  - Classifaction metric - [blog posts](https://www.evidentlyai.com/classification-metrics)

# Model Performance

## Accuracy 

Accuracy is the most common metric for classification problems. It is the ratio of correctly predicted observation to the total observations.

$$Accuracy = \frac{TP+TN}{TP+TN+FP+FN}$$

However, for imbalanced datasets accuracy can give a false sense of achieving high performance.

The classical example, is the case of predicting the dominant hand in a population. By just predicting right hand for the entire population, the model will achieve a high accuracy (90% on average). 

## Precision

If we let the positive class be the class with very few observations, left hand in the previous example. Then precision tells us how well we are predicting that class.

$$Precision = \frac{TP}{TP+FP}$$

The formula, is the proportion of correct predictions for that class divided by the total number of predictions for that class.

So in the previous example, we would have a precision of 0.