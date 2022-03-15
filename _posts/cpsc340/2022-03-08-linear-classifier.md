---
title: CPSC 340 18，19  Linear Classification
author: Luna
layout: post
mathjax: true
tag: ["machine learning", "cpsc340", "ubc"]
---

We can use linear regression to do the classification.
## Binary Classification - classify into {-1, 1}
Loss function
- we cannot use least square, because it will penalize the too-right prediction
- we can use 0-1 loss, but it's not smooth and convex
- we can use **Hinge Loss**  

### Hinge Loss
If $y_i = + 1$, we get the label right if $w^Tx_i > 0$; If $y_i = - 1$, we get the label right if $w^Tx_i > 0$

Which means, if $y_iw^Tx_i > 0$, then the error is 0; if $y_iw^Tx_i < 0$, then the error is $-y_iw^Tx_i$

So the error is $max(0, -y_iw^Tx_i)$

However, it has a degenerate problem - w = 0 always give a lowest value.

$max(0, -y_iw^Tx_i)$ => $\max(0, 1-y_iw^Tx_i)$

SVM is hinge loss with L2-regularization. 
$f(w) = \max \{0, 1-y_iw^Tx_i\} + \frac{\lambda}{2}||w||^2$


### Logistic Loss
We can smooth max the degenerate loss with log-sum-exp.
$max{0, -y_iw^Tx_i} \approx \log(\exp(0) + \exp(-y_iw^Tx_i))$

### Probability - Sigmoid
For prediction, we use "sign" to map the result to {-1, 1};

For probability, we want to map the $w^Tx_i$ to range [0, 1] - sigmoid function.


## Multi-class Linear Classification
One-vs-All classification can turn binary classification into mutliclass classification.

- Training phase: for each class 'c', train binary classifier to predict whether example is a 'c'
- Prediction phase: apply the classifiers to get a score of each class 'c', preict with the highest score.

![](/img/cpsc340/multiclassification.png)