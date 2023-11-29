---
title: 'The Divergence Theorem and Gravity'
date: 2023-07-04
permalink: /posts/2023/11/divergence/
tags:
  - physics
  - differential topology
---
Let $e_r$ be the radial vector field on $\mathbb{R}^3$ of unit length (it is a unit normal vector field to any sphere centered at the origin). Explicitly, 
$e_r(x,y,z) = \frac{1}{\sqrt{x^2+y^2+z^2}}\langle x,y,z\rangle.$

We'll then have $g = -\frac{GM}{|r|^2} e_r$ where $|r|^2 = x^2+y^2+z^2$ is the distance squared from the origin. This $g$ can be viewed as a gravitational vector field and so $G,M$ are constants with physical meaning. $G$ is the universal gravitational constant and $M$ is the mass of the gravitating object. As we get closer to the object, the distance decreases and so dividing by that distance squared increases the strength of the vector field. The math here would work equally well if we wanted to model Coloumbic forces instead. Anyways, if $S$ is a sphere of radius $R$ centered at the origin with outward pointing normal vector field $\hat{n} = e_r$, then
$\iint_S g\cdot \hat{n}\\, dA = -GM \iint_S \frac{1}{|r|^2} dA = -\frac{GM}{R^2} \iint_S dA = -4 \pi GM \frac{R^2}{R^2} = -4\pi GM$.

The second equality comes from the fact that this is the radius $R$ sphere and so the distance of any point on it to the origin is always $R$. Then, we can compute the integral easily by just knowing the surface area of the sphere to be $4 \pi R^2$ (or use spherical coordinates). On the other hand, the radius $R$ sphere bounds the radius $R$ ball $B$ and hence, the divergence theorem tells us that the integral above equals
$\iiint_B \text{div}(g)\, dV = -4 \pi GM$.

We might notice something odd about this. The gravitational vector field is not defined at the origin but that's not a problem when we restrict our attention to a sphere $S$ since it doesn't contain the origin. But what is $\text{div}(g)$? Since we'll integrate it over $B$ which contains the origin, we might want to see what's going on. Let's forget about the constants; then $g$ is just $(x^2+y^2+z^2)^{-3/2}\langle x,y,z \rangle$. Using the quotient rule, we have:

$\partial_x \left(\frac{x}{(x^2+y^2+z^2)^{3/2}} \right) = \frac{(x^2+y^2+z^2)^{3/2} - 3x^2((x^2+y^2+z^2)^{1/2}}{(x^2+y^2+z^2)^3}$.

The partial derivatives in $y,z$ are similar and when we add them all up to compute the divergence, we have:
$\text{div}(g) = \frac{3(x^2+y^2+z^2)^{3/2} - 3(x^2+y^2+z^2)(x^2+y^2+z^2)^{1/2}}{(x^2+y^2+z^2)^3} =0$!

So shouldn't the integral be 0, not $-4\pi GM$? But note that this differentiation only makes sense away from the origin. So the divergence of $g$ is 0 everywhere on $B$ but at the origin, it contributes $-4\pi GM$ to the final answer. This is much like the situation from the line integrals section where we integrated $\nabla \theta$, a conservative vector field on a loop or alternatively by Green's Theorem, we integrated its curl on a disk containing the origin. The curl is 0 everywhere except at the origin where it's not defined. But the integration shows that it contributes $2\pi$. In that case, we were able to detect non-simply connectedness. Here, with this situation, we're detecting the failure to be 2-connected. That is; there is a 2-sphere which does not contract to a point. This generalizes simply connectedness since loops are circles, also known as 1-spheres. In physics terms, this idea can be used to detect theoretical monopoles. Moreover, we can push these ideas to define $n$-connectedness and use integration to detect the failure of say, $\mathbb{R}^{n+1} \setminus 0$ to be $n$-connected.

Now, back to gravity. We may write the mass $M = \iiint_B \rho \\, dV$ where $\rho$ is a function describing the density of $B$. So we have the following:
$\iiint_B \text{div}(g) \\, dV = -4 \pi G \iiint_B \rho \\, dV$.

We may be tempted to say that $\text{div}(g) = -4\pi G\rho$ because they integrate to the same value. Of course, this is in general, false. For example, $\int^{2\pi}_0 \cos x\,dx = \int^{2\pi}_0 0 \,dx = 0$ but $\cos x$ is not the zero function. But in our case, the divergence is 0 everywhere except at one point so the density must be concentrated and we have $\text{div}(g) = -4\pi G\rho$. The proper notion of the concentration is to use the Dirac delta distribution. If you know a little bit about black holes, you'll known that the Schwarzschild metric is a vacuum solution in the sense that there is only vacuum, no mass, away from the singularity. All the energy (equivalently, mass), is concentrated at the singularity.

Now, the gravitational vector field $g = -\nabla \phi$ is actually conservative; there is a gravitational potential function $\phi(x,y,z) = -4GM(x^2+y^2+z^2)^{-1/2}$. Then, the divergence is equal to $\text{div}(-\text{grad}\, \phi)$. Note that this isn't necessarily zero; it's only the divergence of the curl which is 0. In different symbols, we have $\nabla \cdot \nabla \phi$ which is sometimes written as $\nabla^2 \phi$ or $\Delta \phi$. In either case, it is called the Laplacian of $\phi$. Then, the equation $\nabla^2 \phi = 4 \pi G\rho$ is called the **Poisson equation.** It provides the essential summary of Newtonian gravitation in terms of a differential equation. It is entirely equivalent to Newton's inverse square law but has the advantage that it is a differential equation for a scalar quantity that may be straightforward to solve.
