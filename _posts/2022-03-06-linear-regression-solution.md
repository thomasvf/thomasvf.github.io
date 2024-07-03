---
title: 'Exercise: linear regression with a mean-squared error'
date: 2022-03-06
permalink: /posts/2022/03/linear-regression-solution/
tags:
  - exercise
  - linear-regression
  - mean-squared-error
  - vector-calculus
  - mathematics-for-ml
---

Consider a dataset consisting of $\mathbf{X} \in \mathbb{R}^{n \times p}$ and $\mathbf{y} \in \mathbb{R}^{n}$, where $n$ and $p$ are the number of examples and the number of features, respectively.

A linear regression model for this data could be

$$
\hat{y} = \mathbf{w^T}\mathbf{x} + b, 
$$

where $b$ is a scalar and $\mathbf{w}, \mathbf{x} \in \mathbb{R}^p$. We can take all the examples in the dataset at once by writing

$$
\mathbf{\hat{y}} = \mathbf{X} \mathbf{w} + b.
$$

One way of finding values for $\mathbf{w}$ and $b$ is to minimize the sum of squared errors,

$$
e = \|\mathbf{y} - \mathbf{\hat{y}} \|^2.
$$

An important step in doing this is to find the derivative of $e$ with respect to $\mathbf{w}$. Use the chain rule to show that

$$
\frac{\partial e}{\partial \mathbf{w}} = -2(\mathbf{y} - \mathbf{\hat{y}})^\mathbf{T} \mathbf{X} = -2(\mathbf{y} - (\mathbf{X}\mathbf{w} + \mathbf{b}))^\mathbf{T} \mathbf{X} \in \mathbb{R}^{1\times p}
$$

## Solution
According to the chain rule, we have

$$
\frac{\partial e}{\partial \mathbf{w}} = \frac{\partial e}{\partial \mathbf{\hat{y}}} \frac{\partial \mathbf{\hat{y}}}{\partial \mathbf{w}}.
$$

The first part of the right-hand side is the gradient of $e$. To find it, it is easier to expand the norm function

$$
e = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 \rightarrow \frac{\partial e}{\partial \hat{y}_i} = -2(y_i - \hat{y}_i).
$$

Therefore, 

$$
\frac{\partial e}{\partial \mathbf{\hat{y}}}
 = -2(\mathbf{y} - \mathbf{\hat{y}})^\mathbf{T},
$$

where we use the transpose because the gradient is by definition a row vector (in the numerator layout).

The second part of the right-hand side is the Jacobian with dimensions $n\times p$,

$$
J_{ij} = \frac{\partial \hat{y}_i}{\partial w_j} =  X_{ij} \rightarrow \frac{\partial \mathbf{\hat{y}}}{\partial \mathbf{w}} = \mathbf{X}
$$

Therefore,

$$
\frac{\partial e}{\partial \mathbf{w}} = -2(\mathbf{y} - \mathbf{\hat{y}})^\mathbf{T} \mathbf{X}.
$$