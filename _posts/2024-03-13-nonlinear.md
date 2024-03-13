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

One may use the nullclines to partition the $xy$-plane into pieces and then study the qualitative behavior of solutions. For example, let's have $f(x,y) = y-x$ and $g(x,y) = \cos(x)$. Then the $x$-nullclines form the diagonal line $y=x$ and the $y$-nullclines form a series of vertical lines $x = n \pi/2$ where $n$ is an odd integer since $\cos(n \pi/2) = 0$ in those cases. Now, if we plot out the phase portrait for this system using, for example, the excellent free [applet](https://aeb019.hosted.uark.edu/pplane.html), we'll find the following:

![label](/files/nl9.jpg)

Here, I've picked some solutions for the applet to plot; we can see that there are two general behaviors occurring. We have spiraling behavior at some equilibrium points, namely those for $n \equiv 1 \pmod{4}$ and what look like saddle points when $n \equiv 3 \pmod{4}$. We may explain this behavior by now doing our second step: **linearization at the equilibria.**

The first equation above is linear already but the second one is not. However, we know that the Taylor series of a smooth function $f(x)$ at a point $a$ is $\sum^\infty_{k=0} \frac{f^{(k)}(a)}{k!}(x-a)^k$. For cosine, the first two terms when centered at $a$ is $\cos(a)−\sin(a)(x−a)$. When $a$ is one of the equilibrium points, the first term vanishes. If $n \equiv 1 \pmod{4}$, then
we have $-(x - n\pi/2)$. If $n \equiv 3 \pmod{4}$, then it is $+(x - n\pi/2)$. So the linear systems we get have matrices:
$$\begin{pmatrix}
-1 & 1 \\
-1 & 0 
\end{pmatrix},
\begin{pmatrix}
-1 & 1 \\
1 & 0 
\end{pmatrix}$$

The first has eigenvalues $(-1\pm i\sqrt{3})/2$ and the latter has $(-1 \pm \sqrt{5})/2$. Thus, in the first case, we have complex eigenvalues; the negative real part means we have **spiral sources.** For the other case, since $\sqrt{5}>1$, we have a pair of eigenvalues of opposite parity and thus, get **saddle points.**

### Another Example: 1-Paramater Family of Nonlinear Systems

Let's take another example

$$\begin{cases}
x'(t) = −x + x^3 + y \\
y'(t) = -\mu x + y, \mu \in \mathbb{R}
\end{cases}$$

The $x$-nullclines lie on the curve $y = x -x^3$ and the $y$-nullclines on $y = \mu x$. The equilibria come from the intersections of the nullcline sets. Setting $\mu x = x -x^3$, we rearrange to get $x^3 + (\mu - 1)x = 0$. This has 3 solutions when $\mu < 1$, giving us 3 equilibria, and only 1 solution when $\mu > 1$. When $\mu > 1$, the only equilibria is $(0, 0)$. When $\mu < 1$, the equilibria are
$(0, 0),(\sqrt{1 -\mu}, \mu\sqrt{1 -\mu}),(-\sqrt{1 -\mu},-\mu\sqrt{1 -\mu})$.

Linearizing at $(0,0)$, we just throw out the $x^3$ term so we get a linear system with matrix 
$$\begin{pmatrix}
-1 & 1 \\
-\mu & 1 
\end{pmatrix}.$$

The characteristic polynomial is $\lambda^2 - (1 + \mu)$ whose roots are $\pm(\sqrt{\mu- 1})/2$. So we see that when $\mu > 1$, we have real eigenvalues of opposite parity; i.e. a saddle point. When $\mu < 1$, we have purely imaginary eigenvalues and this suggests we have a center.
But we have to be careful, remembering that the $x^3$ term may actually contribute something to perturb the behavior from periodic solutions.

We may also linearize at the other equilibria when $\mu < 1$. It turns out the system in either case has matrix 
$$\begin{pmatrix}
2-3\mu & 1 \\
-\mu & 1 
\end{pmatrix}$$

and characteristic polynomial $\lambda^2 -(3 -3\mu)\lambda + (2 -2\mu)$. The roots are then 
$$((3 − 3\mu) \pm \sqrt{(3 − 3\mu)^2 − 4(2 − 2\mu)})/2.$$

Because $\mu < 1$, the first term is positive. The term under the square root becomes $9\mu^2 -10\mu + 1$ which is concave up and has roots $\mu = 1/9, 1$. For $1/9 < \mu < 1$, the term is negative so we would have complex eigenvalues with positive real part. Here are some phase portraits for different $\mu$.

![label](/files/nl6.jpg)

In this one above, we have $\mu = 5$ and so there is only one equilibrium point. Note that it looks as if the solutions are periodic and ellipses but this is because the $x^3$ is contributing a very small amount when $x$ is small. However, it is still a nonzero amount and so the solutions never fully come back to themselves. There is an interesting map called the Poincar\'e return map which studies these kinds of behaviors.

![label](/files/nl5.jpg)

This next one is with $\mu = \frac{1}{2}$; there are 3 equilibria where the origin is a saddle point and the other two are spiral sources.

![label](/files/nl7.jpg)

Here, $\mu = −2$ and $(0,0)$ is a saddle point. The other two are sources; it’s a bit difficult to tell where they are located in the phase portrait but you can see there is sort of a line that, in the linearization, comes from eigenvectors. The solutions asymptote to this line. One can determine what the line is by studying looking for the larger eigenvalue since it will give the dominating exponential term.

Lastly, let's suppose we just change the original system slightly by flipping the sign of the $y$ in the second equation.
$$\begin{cases}
x'(t) = −x + x^3 + y \\
y'(t) = -\nu x - y, \nu \in \mathbb{R}
\end{cases}$$

Below, we have the phase portrait for $\nu = 5$ which has 3 equilibria. But one interesting thing to note is that the solutions around the origin are not nearly as elliptical as the $\mu =5$ case above.

![label](/files/nl8.jpg)

### Ending Thoughts

In writing this post, I was thinking of a sort of philosophical point. For these systems, instead of using $x'(t),y'(t)$, just form a vector field that is described by $f,g$. Since these are both functions only depending on $x,y$, the whole discussion is based on spatial coordinates. But out of it, we get time-dependent solutions. One perspective is simply taking everything to exist in totality while in the other, there is something happening in time. Frank Wilczek describes these as the Euler and Lagrange perspectives, respectively. The Lagrange perspective favors the intrinsic experience of something whose evolution depends on the equations.

Credit for all images: "Images are generated by the phase plane plotter at aeb019.hosted.uark.edu/pplane.html by Ariel Barton."
