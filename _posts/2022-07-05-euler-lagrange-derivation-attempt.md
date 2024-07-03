---
title: 'An Attempt to Derive the Euler-Lagrange Equation using an Infinite Sum'
date: 2022-07-05
permalink: /posts/2022/07/euler-lagrange-with-infinite-sum/
tags:
  - calculus-of-variations
  - infinite-sum
---

Consider the functional 

$$
S[y] = \int_a^bF(y, y', x)\ dx.
$$

where $y(a) = A$ and $y(b) = B$. The Euler-Lagrange equation for finding the function $y(x)$ that makes the functional stationary is

$$
\frac{\partial F}{\partial y} - \frac{d}{dx}\left( \frac{\partial F}{\partial y'} \right) = 0.
$$

I was curious to find whether we can deduce Euler-Lagrange equation by writing y as an infinite sum, $y(x) = \sum_{k=0}^{\infty} a_k x^k$ and then deriving $S$ with respect to the parameters $a_k$.

My attempt has given me

$$
\frac{\partial S}{\partial a_k}  =  \int_a^b \frac{\partial F(y, y', x)}{\partial a_k} \ dx = \int_a^b \frac{\partial F}{\partial y} \frac{\partial y}{\partial a_k} + \frac{\partial F}{\partial y'} \frac{\partial y'}{\partial a_k} = 0,
$$

for all $k \geq 0$. Using the infinite sum, we find that

$$
\frac{\partial y}{\partial a_k} = x^k.
$$

And

$$
y'(x) = \sum_{k=1}^{\infty} a_k  k x^{k-1} \rightarrow \frac{\partial y'}{\partial a_k} = k x^{k-1}
$$

for $k  \gt 0$. For $k = 0$, $\frac{\partial y'}{\partial a_0} = 0$.

This gives the set of equations

$$
\int_a^b \frac{\partial F}{\partial y} dx = 0,
$$

for $k=0$ and, for $k > 0$,

$$
\int_a^b \left( \frac{\partial F}{\partial y} x^k + \frac{\partial F}{\partial y'} k x^{k-1} \right)dx = 0.
$$

I have then attempted to use the integration by parts trick on the second term of the left-hand side, which gives

$$
\int_a^b \frac{\partial F}{\partial y'} k x^{k-1} dx = \left [\frac{\partial F}{\partial y'} x^{k} \right]_a^b - \int_a^b \frac{d}{dx} \left[ \frac{\partial F}{\partial y'} \right] x^k dx .
$$

Therefore,

$$
\int_a^b \left(  \frac{\partial F}{\partial y} x^k - \frac{d}{dx} \left[ \frac{\partial F}{\partial y'} \right] x^k \right) dx  = -\left [\frac{\partial F}{\partial y'} x^{k} \right]_a^b
$$

From this point on I don’t know how to proceed.

Ideally, we would have

$$
-\left [\frac{\partial F}{\partial y'} x^{k} \right]_a^b = 0
$$

so that we could write

$$
\int_a^b \left(  \frac{\partial F}{\partial y} x^k - \frac{d}{dx} \left[ \frac{\partial F}{\partial y'} \right] x^k \right) dx = \int_a^b \left(  \frac{\partial F}{\partial y} - \frac{d}{dx} \left[ \frac{\partial F}{\partial y'} \right] \right) x^k dx = 0, 
$$

which would maybe imply that it must be true that

$$
\left(  \frac{\partial F}{\partial y} - \frac{d}{dx} \left[ \frac{\partial F}{\partial y'} \right] \right) = 0,
$$

the Euler-Lagrange equation.

> **Note**: I've posted [this derivation](https://math.stackexchange.com/questions/4487054/derivation-of-the-euler-lagrange-equation-using-an-infinite-sum) in Math Stackexchange and a user has pointed out that the $a_k$ parameters are not independent, because of the conditions $y(a) = A$ and $y(b) = B$. These conditions could be dealt with by adding the corresponding Lagrange multipliers. 