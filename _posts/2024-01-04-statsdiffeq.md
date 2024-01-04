---
title: 'Existence and Uniqueness of Solutions to 1st Order ODEs and the Central Limit Theorem'
date: 2024-01-04
permalink: /posts/2024/01/statsdiffeq/
tags:
  - topology
  - differential equations
  - statistics
---

I'll be teaching a class on differential equations and another on statistics this coming Spring 2024. I've been wondering what similarities or relations there are between the two classes. One of the important theorems of differential equations is that given a 1st order differential equation $\frac{dy}{dt} = f(t,y)$ where $f$ and $\partial_y f$ are continuous and has some initial conditions, there exists a unique solution on a small neighborhood of the initial condition. One of the important theorems of statistics is the Central Limit Theorem which, in a very weak form, says: Suppose that $X_i$ are independent, identically distributed random variables with zero mean and variance $\sigma^2$. Then $\frac{1}{\sqrt{N}}\sum^N_{i=1}X_i \to \mathcal{N}(0,\sigma^2)$ as $N \to \infty$. Here, $\mathcal{N}(0,\sigma^2)$ means a normal distribution with mean $\mu = 0$ and variance $\sigma^2$. It's not so obvious but there is some similarities between these two theorems in that there are proofs for them which involve the notion of a fix point. The goal of this post is to spell this out a bit more (though not fully rigorously).

Let's begin with differential equations. The existence and uniqueness theorem is more precisely as follows. Let $f(t,y)$ be a continuous function on $(a,b) \times (c,d)$, an open rectangle in the $ty$-plane. If $(t_0,y_0)$ is a point in this rectangle, there exists an $\epsilon > 0$ and function $y(t)$ defined for $t$ such that $|t-t_0|<\epsilon$ that solves the initial value problem $\frac{dy}{dt} = f(y,t)$ with initial condition $y(t_0) = y_0$. Furthermore, if $\partial_y f$ is also continuous on the rectangle and $y_1$ and $y_2$ are solutions to the above initial value problem for $t$ satisfying $|t-t_0|<\epsilon$, then $y_1(t) = y_2(t)$ on this domain.
