---
title: CPSC 340 Robust Regression
layout: post
tags: ["machine learning", "cpsc340", "ubc"]
mathjax: true
---

## Robust Regression

Robust regression focus less on **large errors**. Instead of minimizing L2-norm, minimizes L1-norm of residuals.

$f(w) = \|\|Xw-y\|\|$ -- it's harder to minimize the absolute error, we don't have normal equations for it, and it's non-differentiable at 0.

So we use a smooth approximation - Huber Loss.

$f(w) = \sum_{i=1}^nh(w^Tx_i-y_i)$

$h(r_i) = \frac{1}{2}r_i^2$ if $|r_i| \leq \epsilon$ otherwise $\epsilon(|r_i| - \frac{1}{2}\epsilon)$

we can minimize the huber loss using gradient descent.


## Brittle Regression

If we care about the outliers, we should minimize the worst error.

$f(w) = \|Xw-y\|_\infty$

smooth apprixmation: log-sum-exp

$max_i\{z_i\} \approx log(\sum_iexp(z_i))$

## Complexity Penalties

$score(p) = \frac{1}{2}\|Z_pv - y\|^2 + \lambda k$

k is the number of estimated parameters, for polynomial basis, we have k = p + 1

AIC: $\lambda = 1$