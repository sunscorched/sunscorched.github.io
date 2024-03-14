---
title: 'Phase Portraits of Some Nonlinear Systems and Periodic Solutions'
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

Here, I've picked some solutions for the applet to plot; we can see that there are two general behaviors occurring. We have spiraling behavior at some equilibrium points, namely those for $n \equiv 1 \pmod{4}$ and what look like saddle points when $n \equiv 3 \pmod{4}$. If you draw the vertical lines $x=n \pi/2$ for odd $n$, you'll find that they intersect the solution curves at points whose tangent lines are horizontal, confirming that these lines are the $y$-nullclines. We may further understand this behavior by now doing our second step: **linearization at the equilibria.**

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

I don't know about you but the phase portrait above reminds me of vortices that appear when studying fluid dynamics such as smoke in turbulent air.

### Another Example: 1-Parameter Family of Nonlinear Systems

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

Because $\mu < 1$, the first term is positive. The term under the square root becomes $9\mu^2 -10\mu + 1$ which is concave up and has roots $\mu = 1/9, 1$. For $1/9 < \mu < 1$, the term is negative so we would have complex eigenvalues with positive real part. So in the language of ODEs, $\mu =1/9,1$ are **bifurcation points** for our 1-parameter family. We'll now look at some phase portraits for specified values of $\mu$.

In the one below, we have $\mu = 5$ and so there is only one equilibrium point. Note that it looks as if the solutions are periodic and ellipses but this is because the $x^3$ is contributing a very small amount when $x$ is small. Since it only contributes to $x'(t)$ and is symmetric with respect to the $y$-axis, we do expect some kind of symmetry in all of the $\mu$-portraits. Indeed, this symmetry is consistent with us having the same matrix at the two non-origin equilibria. If we make the coordinate change $(x,y) \mapsto (-x,-y)$, the equations stay exactly the same since the LHS would then have $-x'(t)$ and $-y'(t)$ and the RHS would have every sign flipped as well.

Anyways, despite $x^3$ contributing little when $x$ is very small, it is still a nonzero amount and so the solutions never fully come back to themselves. There is an interesting map called the Poincaré return map which studies these kinds of behaviors. One use for the map is to address the question of whether there is at least a single periodic orbit in this region even if most solutions are not periodic.

![label](/files/nl6.jpg)

This next one is with $\mu = \frac{1}{2}$; there are 3 equilibria where the origin is a saddle point and the other two are spiral sources.

![label](/files/nl5.jpg)

Here, $\mu = −2$ and $(0,0)$ is a saddle point. The other two are sources; it’s a bit difficult to tell where they are located in the phase portrait but you can see there is sort of a line that, in the linearization, comes from eigenvectors. The solutions asymptote to this line. One can determine what the line is by studying looking for the larger eigenvalue since it will give the dominating exponential term.

![label](/files/nl7.jpg)

### Ruling Out Periodic Orbits

Let's suppose we just change the original system (2) slightly by flipping the sign of the $y$ in the second equation.
$$\begin{cases}
x'(t) = −x + x^3 + y \\
y'(t) = -\nu x - y, \nu \in \mathbb{R}
\end{cases}$$

Below, we have the phase portrait for $\nu = 5$ which has 3 equilibria. But one interesting thing to note is that the solutions around the origin are not nearly as elliptical as the $\mu =5$ case above and we do see some evident spiraling into the origin.

![label](/files/nl8.jpg)

Once again, one might wonder if there is a periodic orbit because there appears to be a transition between solutions asymptoting towards curves that approximately come from eigenvectors and the inward spirals. One reason to be interested in periodic solutions is because they represent repeating behavior. For example, if the system of equations represent celestial bodies and a point on the periodic orbit represents a solar eclipse, then this would mean that we could predict the next solar eclipse. Or if the system represents a simple model for two species competing for resources in an ecosystem, a periodic orbit means that the populations could fluctuate but return to how they were after some time (in reality, these two systems should be a lot more complex).

This question of proving the existence of periodic orbits is rather subtle and finding specific ones is even more difficult. However, there are rather straightforward criteria for ruling out the existence of periodic solutions. For example, if we take the vector field defined by the system, we can assign indices to equilibria by using the **winding number.** A closed loop (not necessarily a solution) can then be assigned an index as well by essentially summing up the indices of all the equilibria it encloses. Moreover, deforming the loop does not change the index unless we cross over equilibria. Thus, we see the winding number is a **topological invariant.** A periodic solution would give a simple loop which is tangent to the vector field at every point. From a different perspective, the vectors on the loop have to wind around once. Thus, one finds that a periodic solution must then enclose equilibria whose total index is nonzero. So for example, if we have two equilibria with indices $+1$ and $-1$, there cannot be any periodic solution which encloses exactly both of them and no others. Here are some other situations; the picture is taken from John Milnor's classic _Topology from a Differential Viewpoint._

![label](/files/milnor.jpg)

One certainly doesn't need to mention topology but I cannot resist pointing out that the winding number is obtained from forming a self-map on the circle $S^1 \to S^1$ and seeing what its homotopy class is. In particular, it induces an endomorphism on the **fundamental group** $\pi_1(S^1) \cong \mathbb{Z}$ and the winding number is equal to the image of the positive generator in $\mathbb{Z}$. This is a nice perspective because if we were to increase the number of our equations in the system to $n$, then we can still define an index for vector fields in these higher dimensions based on **wrapping numbers** or the **degree** of maps $S^{n-1} \to S^{n-1}$ which is again obtained from looking at the induced endomorphism on $\pi_{n-1}(S^{n-1}) \cong \mathbb{Z}$.

Back to our equations from the start of this section, linearizing at the origin, we find a matrix
$$\begin{pmatrix}
-1 & 1 \\
-5 & -1 
\end{pmatrix}$$
with eigenvalues having negative real part and nonzero imaginary part. So we have a spiral sink and its index is $+1$. If we linearize at the other two points, we get the same matrix for both:
$$\begin{pmatrix}
17 & 1 \\
-5 & -1 
\end{pmatrix}$$
whose eigenvalues are real and have opposite parody. So we have saddle points whose indices are $-1$. Thus, a periodic orbit would have to either enclose only the origin or all three equilibria but cannot enclose only two of them where one is the origin.

Let's give one more criterion for ruling out periodic orbits. Once again, let $V =\langle f,g \rangle$ be a differentiable vector and suppose $\gamma$ is a solution, not necessarily one that closes up. This means that if we parametrize $\gamma(t) = (x(t),y(t))$, it satisfies $\frac{dx}{dt} = f, \frac{dy}{dt} =g$. Then, by somewhat nonrigorous reasoning, $\frac{dy}{dx} = \frac{g}{f}$ which allows us to produce the differential form equation $f \, dy - g\, dx = 0$. So integrating this differential 1-form along $\gamma$ gives 0. **Caution:** $V$ is not necessarily a conservative vector field. 

Now, if $\gamma$ is _additionally_ a closed solution (hence, periodic), it encloses a region $D$ and Green's Theorem tells us:
$$0=\oint_\gamma  f \, dy - g\, dx= \iint_D \left(\frac{\partial f}{\partial x} + \frac{\partial g}{\partial y }\right)\, dx\, dy.$$

So in order for $\gamma$ to be a periodic solution, the RHS integral over $D$ has to be 0. Thus, if we find regions where $\frac{\partial f}{\partial x} + \frac{\partial g}{\partial y }$ is always positive or always negative, we cannot have periodic solutions contained in those regions. This is known as **Bendixson's Criterion.** Let's apply this to the so-called van der Pol system.

$$\begin{cases}
\frac{dx}{dt} &= y \\
\frac{dy}{dt} &= -x+(1-x^2)y
\end{cases}$$

We find that $\frac{\partial f}{\partial x} + \frac{\partial g}{\partial y } = 1-x^2$. When $\|x\|>1$, this is always negative and when $\|x\|<1$, then this is always positive. In other words, we cannot have any periodic orbits contained just in the strip defined by $\|x\|<1$ nor any contained just in its complement. Any periodic solution necessarily must cross over both regions. Let's see the phase portrait:

![label](/files/vdp.jpg)

Indeed, any of the potential periodic orbits must travel in both regions (the vertical lines $x=\pm 1$ are part of the lightly colored grid). However, we're still unsure if there are actually any orbits; the solutions could just be coming back nearly to itself without actually closing up and we're unable to tell because we can't zoom in far enough. So detecting orbits is a much more subtle matter. In the future, I may write a post on that subject.

### Ending Thoughts

In writing this post, I was thinking of a sort of philosophical point. For these systems, instead of using $x'(t),y'(t)$, just form a vector field that is described by $f,g$. Since these are both functions only depending on $x,y$, the whole discussion is based on spatial coordinates. We can think of the vector field as representing velocities of particles but the velocities don't need to be changing with respect to time. But out of this, we get time-dependent solutions if we follow the movement of an individual particle. One perspective is simply taking everything to exist in totality while in the other, there is something happening in time. Physicist Frank Wilczek describes these as the Euler and Lagrange perspectives, respectively. The Lagrange perspective favors the intrinsic experience of something whose evolution depends on the equations.

Credit for the phase portraits: "Images are generated by the phase plane plotter at aeb019.hosted.uark.edu/pplane.html by Ariel Barton."
