---
title: 'Undamped Forced Harmonic Oscillators and Resonance'
date: 2024-03-12
permalink: /posts/2024/03/resonance/
tags:
  - differential equations
---

I'm teaching an introductory differential equations class this semester and one of the topics is about studying harmonic oscillators in various settings. They're a great source of 2nd order ODEs and the general form they take is $x'' + p x' + qx = f(t)$ where the LHS of the equation comes from Hooke's Law. For a moment, suppose $f(t)=0$ and $p,q > 0$. Then we have $x'' =  -px' -qx$; if we think of $x(t)$ as describing the position of some object along a line on a spring with mass normalized to 1, then the $-qx$ term tells us that the force of the spring is always towards the equilibrium position. If $x(t)>0$, this means the spring is stretched and the force wants to pull it back. If $x(t) < 0$, then the spring is compressed and wants to push. Thus, $q$ is called the **spring constant.** The other constant is related to factors that depend on the velocity. For example, if the object moves quickly, then it may experience greater forces related to friction. Thus, the constant $p$ is called the **damping coefficient.** When $f(t) \neq 0$, we view it as an extra term telling us how the forces are affected. So we'll call it a **forcing term**; note that we're only asking it to depend on time so it's an external force that doesn't care about the position of the object.

To solve the equation, we can do a trick that's maybe due to Hamilton: introduce another variable $v = x'(t)$. We then find that when $f(t) = 0$, we have on our hands a system of linear equations: 
$$\begin{pmatrix}
x'(t) \\ 
v'(t)\end{pmatrix} = 
\begin{pmatrix}
0 & 1 \\
-q & -p \end{pmatrix} 
\begin{pmatrix}
x(t) \\ 
v(t) \end{pmatrix}.$$

The characteristic equation of this matrix is $\lambda^2 + p \lambda + q =0$ which looks a lot like the original ODE; we've just traded derivatives for powers of $\lambda$. This is no coincidence, of course. From here, we may find the eigenvalues and eigenvectors and then give a description of the **homogeneous solutions** to the original ODE. When $f(t) \neq 0$, we then find a particular solution to add to our homogeneous solutions. 

### Undamped Harmonic Oscillator with Sinusoidal Damping

Let's make the simplifying assumptions that there is no damping and that $f(t)$ is sinusoidal. We could then  

[here](https://www.desmos.com/calculator/uwbgim1ko8)
