---
title: 'Existence and Uniqueness of Solutions to 1st Order ODEs and the Central Limit Theorem'
date: 2024-01-04
permalink: /posts/2024/01/statsdiffeq/
tags:
  - topology
  - differential equations
  - statistics
---

I'll be teaching a class on differential equations and another on statistics this coming Spring 2024. I've been wondering what similarities or relations there are between the two classes. One of the important theorems of differential equations is that given a 1st order differential equation $\frac{dy}{dt} = f(y,t)$ where $f$ is continuous and has some initial conditions, there exists a unique solution on a small neighborhood of the initial condition. One of the important theorems of statistics is the Central Limit Theorem which, in a very weak form, says: Suppose that $X_i$ are independent, identically distributed random variables with zero mean and variance $\sigma^2$. Then $\frac{1}{\sqrt{N}}\sum^N_{i=1}X_i \to \mathcal{N}(0,\sigma^2)$ as $N \to \infty$. Here, $\mathcal{N}(0,\sigma^2)$ means a normal distribution with mean $\mu = 0$ and variance $\sigma^2$.

$\frac{dy}{dt} = f(y,t)$ with initial condition $y(0) = y_0$ has a solution on a small neighborhood of $(y_0,0)$. Moreover, this solution is unique. The
