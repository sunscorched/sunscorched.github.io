---
title: 'Phase Portraits of Some Nonlinear Systems'
date: 2024-03-13
permalink: /posts/2024/03/nonlinear/
tags:
  - differential equations
---

Another topic I've introduced in my differential equations class regards nonlinear systems. Let's consider just systems of two equations of the following form:

$$\begin{cases}
x'(t) = f(x,y) \\
y'(t) = g(x,y)
\end{cases}$$

Since $f,g$ can be any kinds of functions, they can be, in particular, nonlinear. However, one of the lessons of differential calculus is that we may, as a first pass, approximate behavior by linearizing. For example, the 1st derivative of a single-variable differentiable function is used to define a tangent line which, locally, is hopefully a good approximation of the function.

So we'll do our analysis in two stages. First, we will find the **nullclines** for this system and then linearize at the **equilibrium points.**

The **$x$-nullclines** are the points in the $xy$-plane such that $f(x,y) = 0$. At these points, $x'(t) = 0$ and hence, the vector field described by the system of equations is pointing vertically (or is 0). Similarly, the **$y$-nullclines** are the points where $g(x,y) = 0$. At these points, the vector field is pointing horizontally (or is 0). The intersection of these two sets then gives all the points where the vector field is 0; i.e. the equilibria.


Philosophy: vector field described by just spatial positions but out of it, we get time-dependent solutions.
