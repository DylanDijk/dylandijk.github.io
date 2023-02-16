---
layout: post
title: Why do we need Measure Theory
date: 2023-02-10 11:14 +0000
math: true
---

In this post I describe the motivation for why we need to use measure theory in probability.

***

In the ideal case, for some arbitrary sample space $\Omega$ we would like to be able to define a function that outputs probabilities for any choice of subset of $\Omega$. 

We want this function to behave in a certain way so we restrict it to follow the axioms of a probability measure.

However, it turns out that for certain sample spaces if we want a measure to satisfy the axioms and work with all possible subsets then it is possible to construct contradictions. Therefore, we cannot just define a probability measure on all possible subsets but need choose a selection of subsets such that the axioms hold.

We want this collection of subsets/events to be as large enough so that it is useful but also small enough so that the properties hold.

***

Using $\sigma$-algebras does just this, it gives as a set of sets/events that we would naturally want to assign probability to, whilst restricting problematic sets that would give contradictions if we tried to assign a probability to them.