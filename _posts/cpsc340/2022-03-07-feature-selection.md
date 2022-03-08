---
title: CPSC 340 Feature Selection
author: Luna
layout: post
mathjax: true
tag: ["machine learning", "cpsc340", "ubc"]
---

# Feature Selection
General feature selection problem: Find the features (columns) of ‘X’ that are important for predicting ‘y’.

- Association Approach: For each feature ‘j’, compute correlation between feature values xj and ‘y’.
  - a simple way
  - but ignores the variable interactions
- Regression Weight Approach: Fit with all features, take feature where $w_j$ larger that threshold.
  - major problem: collinearity, if the irrelevant variable always in line with the relevant featue.
- Search and Score, the most common approach
  - Define score function f(s)
  - search for the "s" with the best score


# Search and Score
## Score function
- training error? - end with selecting all features
- validation error?  - this is what we want, however some problems:
  - 'd' variables means $2^d$ set of variables
  - false positives: some irrelevant variable might help
  
## Number of Feature Penalties - $L_0$ norm

The L0“norm” is the number of non-zero value (($||w||_0=size(S))$)

$f(w) = \frac{1}{2}||Xw-y||^2 + \lambda||w||_0$

## Forward Selection
1. Start with an empty set of features, S = [ ]. 
2. For each possible feature ‘j’: 
   1.  Compute scores of features in ‘S’ combined with feature ‘j’.
3. Find the ‘j’ that has the best score when added to ‘S’.
4. Check if {S ∪ j} improves on the best score found so far.
5. Add ‘j’ to ‘S’ and go back to Step 2.
   - A variation is to stop if no ‘j’ improves the score over just using ‘S’.