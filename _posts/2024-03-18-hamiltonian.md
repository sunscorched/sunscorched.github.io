---
title: 'Hamiltonian Dynamics and Periodic Solutions'
date: 2024-03-18
permalink: /posts/2024/03/hamiltonian/
tags:
  - differential equations
  - symplectic geometry
---

Consider the following system of nonlinear ODEs.
$$\begin{cases} \frac{dx}{dt} = 2-x-y \\
\frac{dy}{dt} = y-x^2 \end{cases}$$

We may think of the equations as describing a vector field $X_H$ for us. Here's a phase portrait (the length of the vectors has been normalized but their lengths should really be varying):

![label](/files/phase_ham.png)

First of all, by setting the equations above to zero, we can find the equilibrium points of this system. We'll eventually get the equation $2-x = x^2$ and then using $y=x^2$, we have $(-2,4)$ and $(1,1)$ as equilibria (or in other terminology, fixed points of $X_H$). We may linearize the equations at the fixed points by using coordinate changes and then dropping all nonlinear terms.

For $(-2,4)$: We let $u = x+2,v=y-4$ as our coordinate change. Then $(-2,4)\mapsto (0,0)$. Our equations become
$$\begin{cases}u' = 2-(u-2)-(v+4) = -u-v \\ 
v' = (v+4)-(u-2)^2 = -u^2+4u+v \end{cases}$$

To linerize, we only take the linear terms which means we just drop the $-u^2$ so the matrix for this linear system is then 
$$\begin{pmatrix}
-1 & -1 \\
4 & 1 \end{pmatrix}$$

and its characteristic equation is $\lambda^2 + 3$ which has roots $\pm i \sqrt{3}$. So the equilibrium point is a **center** and we expect to see solutions that are approximately periodic (if not actually periodic).

For $(1,1)$: We let $u=x-1,v=y-1$ and the equations become
$$\begin{cases} u' = 2-(u+1)-(v+1) = -u-v \\
v' = (v+1)-(u+1)^2 = -u^2-2u+v \end{cases}$$

To linearize, we again drop the $-u^2$ term and the matrix for the linear system is then 
$$\begin{pmatrix}
-1 & -1 \\
-2 & 1 \end{pmatrix}$$

and its characteristic equation is $\lambda^2 - 3$ which has roots $\pm \sqrt{3}$. So the equilibrium point is a **saddle point** since these are real eigenvalues of opposite parity.

The **separatrices** are the solution curves which tend to the saddle point when $t \to \pm \infty$. Note that they look like a nodal cubic (algebraic variety) defined by, say, $y^2 = x(x-1)^2$, albeit with a bit of distortion.

Another thing to notice is that there seems to be a whole infinite family of periodic orbits here; if we connect the two equilibria by a red line segment as shown in the phase portrait, there is a distinct periodic orbit passing through every point on the line segment (including the endpoint equilibria which can be thought of as periodic orbits with period 0 since they're constant).

Note that if we let $H(x,y) = \frac{x^3}{3}-xy+2y-\frac{y^2}{2}$, then $x'(t) = \partial_y H, y'(t) = -\partial_x H$. So the dynamical system is **Hamiltonian.** Recall this is in the setting where our symplectic form is $\omega = dx\wedge dy$ and we want $\iota_{X_H} \omega = dH = \partial_x H\, dx + \partial_y H \, dy$. The former thing is contraction with the vector field and writing $X_H = x'(t) \, \partial_x + y'(t) \partial_y$, the equations we want to satisfy are $x'(t) = \partial_y H, y'(t) = -\partial_x H$. Then, the integral curves for $X_H$ shown above are the (energy) level sets of $H$. 

Note that $H$ is also a Morse function. Its critical points are exactly the equilibria and its Hessian is
$$\begin{pmatrix}
2x & -1 \\
-1 & -1 \end{pmatrix}.$$

For $x=-2, 1$, the norm of the Hessian is smaller than $2\pi$ so I believe $H$ is considered to be $C^2$-small which means that the notion of nondegeneracy of critical points in the Morse theoretic sense (where $dH=0$) coincides with the notion of nondegeneracy for periodic orbits in the Floer theoretic sense. The latter sense is where we take the time $T$-flow $\psi_T$ and find its fixed points; these correspond to orbits with period $T$. For an orbit $\gamma$ to be nondegenerate, we require the linearization $D_{\gamma(t)}\psi_T$ to not have $+1$ as an eigenvalue.

The critical point $(-2,4)$ has index 2: i.e. is a local maximum. At $(1,1)$, the critical point has index 1 as we know since it's a saddle. Here is a graph of $H$; we can see the shape of it fits well with the level sets.

![label](/files/level_set_ham.png)

So some of these level sets will roughly appear as:

![label](/files/elliptic_curve1.png)

These previous ones have lower energy than these next ones:
![label](/files/elliptic_curve2.png)

For these, note we'll have a periodic orbit as well as a nonclosed trajectory in the same energy level. Lastly, these nonclosed trajectories have the highest energy.
![label](/files/elliptic_curve3.png)

But also, $H$ is an autonomous Hamiltonian which means that any **nonconstant** periodic orbit is automatically **degenerate**. This fits with our situation: the nondegenerate orbits should be isolated and here, the nonconstant periodic orbits are not isolated and hence, must be degenerate. For this reason, the example is not immediately ammenable to the standard Floer theory that Floer himself developed since for that, we usually take Hamiltonians with only nondegenerate periodic orbits. We would need to do a kind of Morse-Bott version which has been developed in various settings. Since the line segment is a manifold-with-boundary but is contractible, I think the Morse-Bott type Hamiltonian Floer homology with $R$ coefficients will just have $C_\*([0,1]) \cong R$ contributing and in the end, we just recover that $H_*(\mathbb{R}^2,R) \cong R$. So the Floer theory can, in the end tell us of the existence of an orbit though perhaps we would want a way to do this without the need for such advanced machinery.

Now, the periods of all these orbits are not the same. To discuss this, we define the action of an orbit $\gamma$ and we'll show it is related to its period. First, we can pick a 1-form $\lambda =x\,dy$ which is a primitive for $\omega = d\lambda$. 

The claim is that there is a function $\alpha:\mathbb{R} \to \mathbb{R}$ such that $\alpha \circ H$ has the same geometric periodic orbits as $H$ (it may change some of the nonclosed trajectories) but makes all the periodic orbits have period $2\pi$ (see Ch. 1 of Jonny Evans' book _Lectures on Lagrangian Torus Fibrations_).

**Theorem 1.6 (Evans' book):** In a 1-parameter family of orbits $\gamma_b$ where $b \in \mathbb{R}$, we have a function $f:\mathbb{R} \to \mathbb{R}$ given by $f(b) :=\int_{\gamma_b} x \,dy$. Then the **period** of $\gamma_a$ is given by $f'(a)$.

So the function $\alpha$ above can be written as $\alpha(b)=\frac{1}{2\pi}f(b) = \frac{1}{2\pi}\int_{\gamma_b}x \, dy$. Depending on conventions, one might call $\alpha$ the **action** or perhaps $f$ is the action; they only differ by a factor of $2\pi$. Note that $\alpha(b)-\alpha(b_0) = \frac{1}{2\pi}\int_{\gamma_b-\gamma_{b_0}}x \, dy = \frac{1}{2\pi}\int_{C_b} dx \wedge dy$ where $C_b$ is the cylinder made from the orbits that connect $\gamma_b$ and $\gamma_{b_0}$. If we choose $\alpha(b_0)=0$, then the function $\alpha(b)$ just gives the area of the cylinder connecting $\gamma_b$ and $\gamma_{b_0}$, divided by $2\pi$.

In this way, we see the periodic orbits really do have different periods. The Mean Value Theorem says that there exists a $c \in [b_0,b]$ such that $f'(c) = \frac{f(b)-f(b_0)}{b-b_0}$; and we'd set $f(b_0)=0$ earlier so then it's just $f'(c) = \frac{f(b)}{b-b_0}$ which is the area of the cylinder $C_b$ divided by $b-b_0$.
