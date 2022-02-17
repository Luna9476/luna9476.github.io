---
title: CPSC 340 Linear Regression
layout: post
tags: ["machine learning", "cpsc340", "ubc"]
mathjax: true
---

We want to discover relationship between numerical variables.

## Linear Regression in 1-D dimension
Assume we have only 1 feature (d = 1), linear regression make prediction $\hat{y_i}$ using a linear function of $x_i$:

$\hat{y_i} = wx_i$

Instead of  "exact $y_i$", we evaluate the size of the error in prediction:

$f(w) = \frac{1}{2}\sum_{i=1}^n(wx_i-y_i)^2$

We want to minimize this function by following steps:
1. Take the derivative of 'f'
2. Find points 'w' where the derivative $f'(w)$ is equal to 0
3. Choose the smallest one and check $f''(w)$ is positive

$f(w) = \frac{1}{2}(\sum_{i=1}^n(w^2x_i^2 - 2wx_iy_i + y_i ^2)) = \frac{w^2}{2}\sum_{i=1}^nx_i^2 - w \sum_{i=1}^nx_iy_i + \frac{1}{2}\sum_{i=1}^ny_i^2$

$f'(w) = \sum_{i=1}^n x_i^2 w - \sum_{i=1}^n x_iy_i = 0$

$w = \frac{\sum_{i=1}^n x_iy_i}{\sum_{i=1}^n x_i^2}$

## 2-D dimension and d-D dimension

For 2-D:   $\hat{y_i} = w_1x_{i1} + w_2x_{i2}$

For d-D: $\hat{y_i} = \sum_{j=1}^dw_jx_{ij} = w^Tx_i (w, x_i$ are column vectors) 

Then the linear square model is $f(w) = \frac{1}{2}(w^Tx_i-y_i)^2$ -> How do we find the best w in d dimensions?

### Partial Derivative
For 1 example:
 
$f(w_1,w_2,\dots, w_d) = \frac{1}{2}(\sum_{j=1}^dw_jx_{ij})^2 + \sum_{j=1}^dw_jx_{ij}y_i + \frac{1}{2}y_i^2$

$\frac{\partial f(w_1,w_2,\dots, w_d)}{\partial w_1} = (\sum_{j=1}^dw_jx_{ij})x_{i1} - y_ix_{i1} = (w^Tx_i-y_i)x_{i1}$ 


For a genric example:

$\frac{\partial f(w_1,w_2,\dots,w_n)}{\partial w_j} = (w^Tx_i-y_i)x_{ij}$

For n examples, sum over all n examples:
$\frac{\partial f(w_1,w_2,\dots,w_n)}{\partial w_j} = \sum_{i=1}^n(w^Tx_i-y_i)x_{ij}$

The partial derivative for $w_j$ depends on all ${w_1, w_2, \dots, w_d}$, we cannot set equal to 0 to solve for $w_j$

### Gradient in d-Dimensions
Generalizing "set the derivative to 0 and solve" in d-dimensions to:

Find 'w' where the **gradient vector** equals the zero vector.

gradient vector:

$$

\nabla f(w)=\begin{bmatrix}
\dfrac{\partial f}{\partial w_1}\\
\dfrac{\partial f}{\partial w_2}\\
\vdots\\
\dfrac{\partial f}{\partial w_d}
\end{bmatrix}  


$$

For linear least squares:
$$
\nabla f(w) = \begin{bmatrix}
    \sum_{i=1}^n(w^Tx_i-y_i)x_{i1} \\
    \sum_{i=1}^n(w^Tx_i-y_i)x_{i2} \\
    \vdots\\
    \sum_{i=1}^n(w^Tx_i-y_i)x_{id} \\
\end{bmatrix}
$$
And $\nabla f(w) = 0$ for linear least squares can be solved by linear equations.

## Matrix/Norm Notaition
- prediction for example 'i' is given by the scalar $w^Tx_i$
- prediction for all 'is' is the matrix-vector product $Xw$
- residual vector $r = \hat{y} - y$

$f(w) = \sum_{i=1}^n(r_i)^2 = \sum_{i=1}^nr_ir_i = r^T r = \|\|r\|\|^2 = \|\|Xw-y\|\|^2$

$f(w) = \frac{1}{2}\|\|Xw-y\|\|^2 = \frac{1}{2}(Xw-y)^T(Xw-y) \\
= \frac{1}{2}w^TX^TXw - w^TX^Ty+ \frac{1}{2}y^Ty \\
= \frac{1}{2}w^TAw - w^Tb + c$ 

$\nabla[\frac{1}{2}w^TAw] = Aw(if \space A \space is \space symmetric)$

$\nabla f(w) = Aw - b = 0 \Rightarrow X^TXw - X^Ty = 0\Rightarrow X^TXw = X^Ty$

### Least Squares Cost - solve $X^TXw=X^Ty$
- Form $X^TY$: $O(nd)$ - it has d elements, each is an inner product between n numbers
- Form $X^TX$: $O(nd^2)$ - it has d**2 elements, each is an inner product between n numbers
- Solve d*d equation $O(d^3)$
- Overall $O(nd^2) + O(d^3)$
  
## y-Intercept

$$X = \begin{bmatrix}
    -0.1\\
    0.3\\
    0.2\\
\end{bmatrix}$$

$$Z = \begin{bmatrix}
    1 & -0.1\\
    1 &0.3\\
    1 & 0.2\\
\end{bmatrix}$$

## Change of Basis
Like polynomial basis, replace $$X=\begin{bmatrix}
    x_1\\ x_2\\ \vdots x_n
\end{bmatrix}$$ with $$Z = \begin{bmatrix}
    1 & x_1 & x_1^2 \dots & x_1^p \\
    1 & x_2 & x_2^2 \dots & x_2^p \\
    \vdots & \vdots & \dots & \vdots\\
    1 & x_n & x_n^2 \dots & x_n^p \\
\end{bmatrix}$$








