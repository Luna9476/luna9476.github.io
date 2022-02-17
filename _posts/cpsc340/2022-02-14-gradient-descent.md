---
title: CPSC 340 Gradient Descent
layout: post
tags: ["machine learning", "cpsc340", "ubc"]
mathjax: true
---

## Gradient Descent
- starts with a guess $w_0$
- use the gradient $\nabla f(w^0)$ to generate a better $w^1$
- ...
- the limit of $w^t$ goes to $\infty$ has $\nabla f(w^t) = 0$
  
It converges to a global optimum if f is convex.
More details [Gradient Descent](https://github.com/Luna9476/CPSC340-2021W2/blob/main/lectures/L13.pdf)

## Gradient Descent for Least Squares
$f(w) = \frac{1}{2} \|\|Xw-y\|\|^2$

$\nabla f(w) = X^T(Xw-y)$

$w^{t+1} = w^t - \alpha^tX^T(Xw-y)$

Cost of each iteration is $O(nd)$, t iterations.

## How to Know a Convex Function
![](/img/cpsc340/convex.png)