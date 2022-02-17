---
title: CPSC 340 Feature Selection
layout: post
tags: ["machine learning", "cpsc340", "ubc"]
mathjax: true
---

We need to find the features that are important for predicting y.

- Association approach - for each feature j, compute correlation between feature $x^j$ and $y$ (however it ignores variable interactions)
- Regression Weight approach - fit 'w' based on all features, take features where $w_j$ is large
  - has major problem with collinearity: two copies of irrelevant feature or the relevant feature have the same value (L15. p.13)
- Search and Score

## Search and Score
1. Define score function f(S)
2. Search for the variables 'S' with the best score

### Score Function

The score shouldn't be training error - train error goes down as you add features

Validation error? Yes!

#### "Number of Features" Penalties


$score(S) = \frac{1}{2}\sum_{i=1}^n(w_x^Tx_{is} - y_i)^2 + size(s)$

We can use L0-Norm to replace size(s)
$score(S) = \frac{1}{2}\sum_{i=1}^n(w_x^Tx_{is} - y_i)^2 + \lambda\|w\|_0$

### How to handle too many choices for $S$ - Forward Selection

1. Start with empty set {}
2. Compute score for each feature
3. Add from the best score
4. Combine every other feature with the best feature to find the best
5. Check if the combination improves the score
6. If yes, go back to step 2, else stop.

