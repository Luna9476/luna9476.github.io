---
title: CPSC340 Outlier Detection
layout: post
tag: ["machine learning", "cpsc340", "ubc"]
mathjax: true
---

# Methods
1. Model-based 
2. Graphical 
3. Cluster-Based
4. Distance-Based
5. Supervised

## Model-Based Outlier Detection
We can fit a probabilistic model, outliers are those with low probability.

Assume data follows normal distribution, z-score:\
$z_i = \frac{X_i - \mu}{\theta}$, where $\mu = \frac{1}{n}\sum_{i=1}^nX_i$ and $\theta = \sqrt{\frac{1}{n}\sum_{i=1}^n(X_i-\mu)^2}$

However, the mean and variance are sensitive to outliers. And the data may not concentrate around the mean.

## Graphical Outlier Detection
Draw plot of the data, and identify the outlier by human

## Cluster-Based Outlier Detection
1. cluster data
2. find points don't belong to the clusters


## Distance-Based Outlier Detection
Skip the model/plot/cluster step, just measure distances.

### Global Distance-Based Outlier Detection - KNN
- For each point, compute the average distance to its KNN
- Choose points with biggest values (outliers are far away from their KNNs)
  
### Local Distance-Based Outlier Detection
Outlierness Ratio  = $\frac{average \space distance\space of\space 'i'\space to\space its\space KNNs}{average \space distance \space of \space neighbours\space of \space 'i' \space to \space their \space KNNs}$

If outlinerness ratio > 1, $x_i$ is further away from neighbours than expected

## Supervised Outlier Detection
- $y_i = 1$ if $x_i$ is an outlier
- $y_i = 0$ if $x_i$ is a regular point

But we need to know what outliers look like, and we may not detect new types of outliers.