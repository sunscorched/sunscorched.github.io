---
title: 'The Divergence Theorem and Gravity'
date: 2023-11-29
permalink: /posts/2023/11/divergence/
tags:
  - physics
  - differential topology
---
In this post, we'll consider an example related to the Divergence Theorem and gravity. I think it's a nice example to show students taking multivariable/vector calculus (which I'm teaching this semester). Let's first recall the statement of the Divergence Theorem. Let $W \subset \mathbb{R}^3$ be a 3-dim region with boundary being a piecewise smooth, closed surface $S$. It's a somewhat nontrivial fact that all closed hypersurfaces of $\mathbb{R}^n$ are orientable but in this case, one can use the cross product on $\mathbb{R}^3$ to produce an orientation on a closed surface. Note the closedness is essential; the Möbius band is a nonorientable surface in $\mathbb{R}^3$ but it is not closed. Moreover, in $\mathbb{R}^3$, having a unit normal vector field on $S$ induces an orientation on $S$. So let's suppose that $W$ is oriented and $S$ has the induced orientation from $W$. If $F$ is a vector field defined on a neighborhood of $W$, we may find the divergence of $F$ which is a scalar function that intuitively, measures the net flow of $F$ at a given point.

Now, if we were to integrate the divergence over $W$, then we see that on the interior, if a point has positive net flow, then some of the flow would be going into some other nearby point. This contributes a negative flow to that nearby point. So in this hand-wavy way, the integration of the divergence has a bunch of cancellation on the interior. It is only when we make it to the boundary that there isn't anything left to cancel since there is nothing beyond the boundary that is taken into account. So the integration reduces to studying how $F$ transfers the flow through the boundary $S$; that is exactly what a flux integral is once you take into account a unit normal vector field $\hat{n}$ on $S$. Thus, to summarize this discussion in symbols, the Divergence Theorem says:
$\iiint_W \text{div}(F) \\, dV = \iint_S (F\cdot \hat{n})\\, dA$.

Let's now turn to the gravitation example. Let $e_r$ be the radial vector field on $\mathbb{R}^3$ of unit length (it is a unit normal vector field to any sphere centered at the origin). Explicitly, 
$e_r(x,y,z) = \frac{1}{\sqrt{x^2+y^2+z^2}}\langle x,y,z\rangle.$

We'll then have $g = -\frac{GM}{\|r\|^2} e_r$ where $\|r\|^2 = x^2+y^2+z^2$ is the distance squared from the origin. This $g$ can be viewed as a gravitational vector field and so $G,M$ are constants with physical meaning. $G$ is the universal gravitational constant and $M$ is the mass of the gravitating object. As we get closer to the object, the distance decreases and so dividing by that distance squared increases the strength of the vector field. The math here would work equally well if we wanted to model Coloumbic forces instead. Anyways, if $S$ is a sphere of radius $R$ centered at the origin with outward pointing normal vector field $\hat{n} = e_r$, then
$\iint_S g\cdot \hat{n}\\, dA = -GM \iint_S \frac{1}{\|r\|^2} dA = -\frac{GM}{R^2} \iint_S dA = -4 \pi GM \frac{R^2}{R^2} = -4\pi GM$.

The second equality comes from the fact that this is the radius $R$ sphere and so the distance of any point on it to the origin is always $R$. Then, we can compute the integral easily by just knowing the surface area of the sphere to be $4 \pi R^2$ (or use spherical coordinates). On the other hand, the radius $R$ sphere bounds the radius $R$ ball $B$ and hence, the divergence theorem tells us that the integral above equals
$\iiint_B \text{div}(g)\, dV = -4 \pi GM$.

We might notice something odd about this. The gravitational vector field is not defined at the origin but that's not a problem when we restrict our attention to a sphere $S$ since it doesn't contain the origin. But what is $\text{div}(g)$? Since we'll integrate it over $B$ which contains the origin, we might want to see what's going on. Let's forget about the constants for now; then $g$ is just $(x^2+y^2+z^2)^{-3/2}\langle x,y,z \rangle$. Using the quotient rule, we have:

$\partial_x \left(\frac{x}{(x^2+y^2+z^2)^{3/2}} \right) = \frac{(x^2+y^2+z^2)^{3/2} - 3x^2((x^2+y^2+z^2)^{1/2}}{(x^2+y^2+z^2)^3}$.

The partial derivatives in $y,z$ are similar and when we add them all up to compute the divergence, we have:
$\text{div}(g) = \frac{3(x^2+y^2+z^2)^{3/2} - 3(x^2+y^2+z^2)(x^2+y^2+z^2)^{1/2}}{(x^2+y^2+z^2)^3} =0$!

So shouldn't the integral be 0, not $-4\pi GM$? But note that this differentiation only makes sense away from the origin. So the divergence of $g$ is 0 everywhere on $B$ but at the origin, it contributes $-4\pi GM$ to the final answer. This is much like the situation of line integrals where we integrate $\nabla \theta$, a conservative vector field on a loop or alternatively by Green's Theorem, we integrate its curl on a disk containing the origin. The curl is 0 everywhere except at the origin where it's not defined. But the line integration shows that the origin should contribute $2\pi$ and what we find is that the integrals detect the non-simply connectedness of the punctured plane. Or in the context of complex analysis, this is an example of the **Cauchy Residue Theorem**. Here, with this divergence situation, we're detecting the failure for $\mathbb{R}^3 \setminus 0$ to be 2-connected. That is; there is a 2-sphere which does not contract to a point. 

Now, back to gravity. The fact that the divergence of $g$ is concentrated just at a point should remind us that in Newtonian physics, we do assume that everything is a point mass; all the mass is concentrated just in a point. We may write the mass $M = \iiint_B \rho \\, dV$ where $\rho$ is a function describing the density of $B$. So we have the following:
$\iiint_B \text{div}(g) \\, dV = -4 \pi G \iiint_B \rho \\, dV$.

We may be tempted to say that $\text{div}(g) = -4\pi G\rho$ because they integrate to the same value. Of course, this is in general, false. For example, $\int^{2\pi}_0 \cos x\,dx = \int^{2\pi}_0 0 \,dx = 0$ but $\cos x$ is not the zero function. But in our case, the divergence is 0 everywhere except at one point and our point mass assumption tells us that the density must be concentrated in a point. So we have $\text{div}(g) = -4\pi G\rho$.

Now, the gravitational vector field $g = -\nabla \phi$ is actually conservative; there is a gravitational potential function $\phi(x,y,z) = -4GM(x^2+y^2+z^2)^{-1/2}$. Then, the divergence is equal to $\text{div}(-\text{grad}\, \phi)$. Note that this isn't necessarily zero; it's only the divergence of the curl which is 0. In different symbols, we have $\nabla \cdot \nabla \phi$ which is sometimes written as $\nabla^2 \phi$. This operator is called the **Laplacian** and when $\nabla^2 \phi = 0$, we say that $\phi$ is a harmonic function. Well, our $\phi$ is harmonic on $\mathbb{R}^3 \setminus 0$.

Then, the elliptic equation $\nabla^2 \phi = 4 \pi G\rho$ is called the **Poisson equation.** It provides the essential summary of Newtonian gravitation in terms of a differential equation. It is entirely equivalent to Newton's inverse square law but has the advantage that it is a differential equation for a scalar quantity that may be easier to solve. There is a lot more that can be said of Poisson equations when you allow $\rho$ to be any function, not necessarily the density for mass. I'll end by saying that this whole discussion works just as well for other contexts such as electromagnetism.
