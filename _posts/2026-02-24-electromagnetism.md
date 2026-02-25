---
title: "Electromagnetism"
date: 2026-02-24
permalink: /posts/2026/02/electromagnetism/
tags:
  - physics
  - differential geometry
---

Let $M:=(\mathbb{R}^4,g)$ be the usual Minkowski space where the Lorentzian metric $g=-dt^2 + dx^2 + dy^2+dz^2$ has signature $(-+++)$ with a special time direction. Being a contractible space, there is only one principal $U(1)$-bundle (up to isomorphism) on $M$ and we may equip the bundle with a $U(1)$ connection $A$ which in physical terms, is a **potential.** The curvature is $F = dA + \dfrac{1}{2}[A,A]$ where $[A,A]$ is the Lie bracket but since $U(1)$ is abelian, this part is 0 and we only have the usual exterior derivative. This 2-form $F$ is called the **Faraday 2-form** and we should think of it as being the fundamental object from which we'll observe electric and magnetic fields. We'll also need to discuss some structure coming from the metric. The metric can be extended to other tensors and of interest, to differential forms. Let $\eta = dt\wedge dx\wedge dy\wedge dz$ be the volume form. The Hodge star operator on differential forms is written as $\*\beta$ where $\beta$ is any differential $k$-form and $\*\beta$ is a $(n-k)$-form, $n$ being the dimension of the manifold. Let $\alpha,\beta$ be two $k$-forms. This operator is defined by $\alpha \wedge \*\beta = g(\alpha,\beta) \eta$. Since $g$ is symmetric, then this also equals $\beta \wedge \*\alpha$. For example, $\*dt$ is defined by $dt \wedge \*dt = g(dt,dt)\eta = -\eta$. So $\*dt = -dx\wedge dy \wedge dz$.

We can write Maxwell's equations succinctly in terms of these objects. First, we have the equation which is always true mathematically:
1. $dF = 0$ because $d^2 = 0$.
2. $d\*F = J$ where $J$ represents a current density, often depicted as $J = j\wedge dt + \rho$.

In a vacuum, we would set $J=0$. If we apply $d$ to both sides, we get $dJ = d^2\*F = 0$ which is equivalent to $\partial_t \rho + \nabla \cdot j = 0$. This is the **continuity equation** which represents conservation of charge since if we integrate over **any** oriented 3D domain in $\mathbb{R}^3_{xyz}$ with boundary, we’d get that the change in total charge can only occur continuously via charged particles moving past the boundary of that domain.


## Observed Electric and Magnetic Fields Depend on Frame of Reference

Now, let's consider the vector field $V = \partial_t$. Since it has no spatial components, we can imagine that it's a "stationary-in-space" vector field and it is orthogonal to the hypersurfaces defined by setting $t$ to a constant. Let $\phi:S \hookrightarrow M$ be one of these 3D hypersurfaces and define $F = B_0 dx \wedge dy$. We'll interpret this as a uniform magnetic field in the $z$-direction. So then, we have these general definitions $E:=\iota_V F$ and $B:=\phi^\* F$ for the electric and magnetic fields on $S \cong \mathbb{R}^3\_{xyz}$. That is, we use the **interior derivative** which is contraction with a vector field $V$ and also the pullback of $F$. Note that we can decompose $F = E \wedge dt + B$ because of our simple choices. Also, observe that $E = B_0 \iota_{\partial_t}dx \wedge dy = 0$ so there is actually no electric field here.

However, if we choose $V = \gamma(\partial_t + v \partial_x)$ instead where $\gamma = (1-v^2)^{-1/2}$, and $v$ is the speed of movement in the $x$-direction, we're no longer in a stationary frame of reference and we get a corresponding "slanted" hypersurface $S \subset M$. In this case, $E = B_0\iota_V(dx \wedge dy) = \gamma v B_0 dy \neq 0$ so in this moving frame of reference, we observe a nonzero electric field.

Any frame of reference—which I'll think of as this 3D submanifold $\phi:S \hookrightarrow M$ as defined by a vector field $V$—inherits the pullback metric $\phi^\*g$ and hence, a Hodge star as well. For $V=\partial_t$, the Hodge star on $M$ decomposes simply with the Hodge star on $S$: $\*_M F = \*_S E - \*_S B \wedge dt$; I've written subscripts to make it clear which Hodge star I mean. So interestingly, $\*F$ sort of exchanged the electric and magnetic forms in the sense of what is paired with $dt$. These forms have special meaning as well: $D=\*_S E$ is the electric displacement 2-form and $H = \*_SB$ is the magnetic intensity 1-form.

_Non sequitur:_ I was using em dashes before ChatGPT came on the scene.

Now, I've been using $M = (\mathbb{R}^4,g)$ but we can replace $M$ with any Lorentzian 4-manifold and since $d$ is independent of the metric, all of the information is hidden in the Hodge star operator but the form of Maxwell's equations does not change at all. For example, we'll still always have $dF = 0$ for free. Since locally, $M$ is simply the Minkowski space, then we can still consider local hypersurfaces defined by a vector field. We can still try to define a global hypersurface using a vector field but we should keep in mind we do not have a globally defined time direction we should be cautious about how to interpret this $S$. Or we can just pick a "space-like" hypersurface $S$.


## d'Alembert Wave Operator

So in Riemannian geometry, if we have a $k$-form $\alpha$, then $\*\*\alpha = (-1)^{n(n-k)}\alpha$. If we applied such a Hodge star twice to a 2-form $F$ on a 4-manifold, we'd get $F$ back. But the signature of a Lorentzian metric is such that $\*^2 F = -F$. This is important for the following reason.
Consider the operator $\delta = \*d\*$ which can be defined on any Riemannian/Lorentzian manifold. Then if $\alpha$ is a $k$-form, $\*\alpha$ is a $(n-k)$-form, $d\*\alpha$ is a $(n-k+1)$-form and $\*d\*\alpha$ is a $(n-(n-k+1)) = k-1$ form. So $\delta$ decreases the degree of $k$-forms by 1.

Thus, the **Hodge Laplacian** $\Delta = (d + \delta)^2 = d\delta + \delta d$ sends $k$-forms to $k$-forms since $\delta$ lowers degree by 1 and $d$ increases degree by 1. Now what happens when we apply this to our Faraday 2-form? $\Delta F = d\delta F + \delta dF$. Since $dF = 0$, the 2nd term is 0 and the first term is $d\*d\*F = d\*J$. In vacuum where $J=0$, then $\Delta F = 0$. This $\Delta$, because of the $(-+++)$ signature, is exactly the d'Alembert wave operator $\square$.


## Action Perspective

We began this post with a connection $A$ but largely stuck with discussing the curvature $F$ which gives rise to force fields. Let's begin again but this time with any spacetime manifold $(M,g)$. That is, we have a 4-manifold with a Lorentzian metric and we'll assume that $\partial M = \varnothing$. We can define a principal $U(1)$-bundle on this manifold which will be classified by the 1st Chern class $c_1 \in H^2(M,\mathbb{Z})$. The action for a $U(1)$-connection on this bundle is $S[A] = \dfrac{1}{2}\int_M F \wedge \*F$ where $F =dA$.

If we vary the connection a little bit by $A+\epsilon a$, we can do some calculus of variations and compute $\delta_A S(a) = \left.\dfrac{d}{d\epsilon}S[A+\epsilon a]\right\|_{\epsilon = 0}$ . The integrand will be $d(A+\epsilon a) \wedge \*(dA + \epsilon a) = F\wedge \*F + \epsilon da \wedge \*F + \epsilon F \wedge \*da + \epsilon^2 da \wedge \*da$. Taking derivatives and setting $\epsilon = 0$, we are left with $da \wedge \*F + F \wedge \*da = 2 da \wedge \*F$ by the symmetric property of metrics.

Next, note that integration by parts gives $\int da \wedge \*F = \int d(a \wedge \*F) - a \wedge d(\*F)$. And the first term, by Stokes Theorem, is 0 since $\partial M = \varnothing$. So we see by substituting in that the $\delta_AS(a) = -\int_M a \wedge d\*F$. For $A$ to be a critical point of $S$ then means that this integral should vanish for all $a$ which means that $d\*F = 0$ (the Euler-Lagrange equation for the action). This is exactly the 2nd equation above that's part of Maxwell's Equations when in vacuum.


## Principal $U(1)$-Bundles over Integral Symplectic Bases

I wrote this awhile ago so the notation doesn't match the above as closely and it's also a bit more technical but here we go. Let $(Q,\omega)$ be a manifold with a closed 2-form which is integral; i.e. $[\omega]$ is in the image of $H^2(Q,\mathbb{Z}) \to H^2(Q,\mathbb{R})$.

**Theorem (Kobayashi):** There exists a principal $U(1)$-bundle $p:P \to Q$ with a connection 1-form $\theta$ such that $d\theta = -2\pi p^\*\omega$.

**Proof:** Let $\{U_i\}$ be a good cover of $Q$. Being closed, $\omega$ is locally exact and we'll assume our cover is such that $\omega\|\_{U_i} = d\alpha_i$ for some $\alpha_i$ on each $i$. On the nonempty overlaps $U_i \cap U_j$, $d(\alpha_i - \alpha_j) = \omega - \omega=0$ which means that $\alpha_i - \alpha_j$ is closed and hence, locally exact; i.e. $(\alpha_i - \alpha_j)\|\_{U_i \cap U_j} = d\alpha_{ij}$ for some function $\alpha_{ij}$. Next, on the triple overlaps, let $f_{ijk}:U_i \cap U_j \cap U_k \to \mathbb{R}$ be defined by $f_{ijk}=\alpha_{ij} +\alpha_{jk}+\alpha_{ki}$. Note that $df_{ijk}=\alpha_i-\alpha_j+\alpha_j - \alpha_k + \alpha_k - \alpha_i = 0$. So $f_{ijk}$ is constant and also forms a Čech cocycle $[\{f_{ijk}\}] \in \check{H}^2(Q,\mathbb{R})$. The Čech cohomology is in fact the same as $H^2(Q,\mathbb{R})$ because $Q$ is a manifold. We claim that all of them can be taken to be integer valued.

**Theorem (Weil):** The correspondence $[\omega] \mapsto [\{f_{ijk}\}]$ induces an isomorphism between $H^2_{dR}(Q,\mathbb{R})$ and $\check{H}^2(Q, \mathbb{R})$. Furthermore, this isomorphism sends the integral part to the integral part.

Since $\omega$ is integral, so is $[\{f\_{ijk}\}]$; hence, find a representative that is integral: $\{\tilde{f}\_{ijk}\}$. We have $\tilde{f} = f + \partial g$ for some Čech 1-cochain $g$. Replacing the $\alpha\_{ij}$ by $\tilde{\alpha}\_{ij}=\alpha\_{ij} + g\_{ij}$ doesn't change the class. Moreover, the $\tilde{\alpha}\_{ij}$ satisfy the cocycle condition and are integral; hence, can be viewed as transformations of $S^1 = \mathbb{R}/2\pi \mathbb{Z}$. We then define $P = \coprod_i U_i \times S^1/\sim$ where $(x,[\phi]) \sim (y,[\psi])$ if and only if $x=y$ and $[\phi] = [\psi - 2\pi \tilde{\alpha}\_{ij}]$.

Next, define $\theta$ on $U_i \times S^1$ by $\theta\|\_{U_i \times S^1} = dt - 2 \pi \alpha_i$ where $t$ is the angular coordinate of $S^1$. To make sure this is well-defined, we look at transition maps: $\Psi\_{ij}:(U_i \cap U_j)\times S^1 \to (U_i \cap U_j)\times S^1; (x,[t]) \mapsto (x,[t-2\pi \tilde{\alpha}\_{ij}])$. On $U_j \times S^1$, $\theta = dt - 2 \pi \alpha_j$ and $\Psi^\*\_{ij} (dt - 2 \pi \alpha_j)=d(t-2\pi \tilde{\alpha}\_{ij})-2\pi\alpha_j = dt-2\pi \alpha_i$. We also see that $d\theta = -2\pi p^\*\omega$. $\square$

**Corollary:** If $\omega$ is also nondegenerate; i.e. a symplectic form, then $(P,\theta)$ is a contact manifold and the Reeb field for $\theta$ generates the circle action.

**Proof:** $\theta \wedge (d\theta)^n = (dt − 2\pi \alpha_i) \wedge (-2 \pi d\alpha_i)^n= (-2\pi)^n dt \wedge p^\*\omega^n \neq 0$. So $\theta$ is contact. Moreover, $\ker d\theta$ is precisely the kernel of $dp$ which are the tangent vectors of the circle fibers. $\square$ 

We'll now switch notation as we move into the setting where $\omega$ is symplectic; we'll use $\alpha$ as the connection 1-form. A principal $U(1)$-bundle $Y$ over a symplectic manifold $(B,\omega)$ is called a **Boothby-Wang bundle** or **prequantization bundle** if and only if $\omega$ is an integral class. Examples include any smooth projective manifold $Q \subset \mathbb{CP}^n$. Take the tautological line bundle on projective space and restrict it to $Q$ and then take the circle bundle. There's also the Kähler form called the Fubini-Study form $\omega$ which is an integral symplectic form. In a sense complex projective geometry is the right setting for quantum theories.

BW bundles have many nice properties. As we've established, $(Y,\alpha)$ is a contact manifold and we may view $\alpha$ as the connection 1-form. Because the Lie algebra of $U(1)$ is $\mathbb{R}$, we can go back in forth between viewing $\alpha$ is real valued or Lie algebra valued. Moreover, $\mathbb{R}$ is an abelian Lie algebra and so the curvature of $\alpha$ is $F = d\alpha + \frac{1}{2}[\alpha \wedge \alpha] = d\alpha$. Now, denoting $\pi:Y \to B$ as the fibration, $\pi^\* \omega = d\alpha$; i.e. we have a way to interpret curvature using the symplectic form on the base.

Therefore, if we have a contractible loop $\gamma$ on the $B$, we can lift it using $\alpha$ in a unique way to a $\tilde{\gamma}$. Of course, this generalizes: a connection gives a way of doing parallel transport. Furthermore, this $\tilde{\gamma}$ may no longer be a loop but a path. It will have endpoints in the same fiber but there may be a **phase shift.**

How might we find this phase shift? Well, we can take $\exp (2\pi i \int_{\tilde{\gamma}} \alpha) = \exp (2\pi i \int_{\gamma} \sigma^\* \alpha)$ where $\sigma:B \to Y$ is a section ($\pi \circ \sigma = \text{id}$). Since we're assuming $\gamma$ is contractible, we can take a capping disk of $\gamma$, call it $D$. Then we have $\exp (2\pi i \int_{\gamma} \sigma^\* \alpha) = \exp (2\pi i \int_D d\sigma^\* \alpha) = \exp (2\pi i \int_D \sigma^\* d\alpha) = \exp (2\pi i \int_D \omega).$ The last equality comes from $\sigma^\* d\alpha = \sigma^\*  \pi^\* \omega = (\pi \circ \sigma)^\* \omega = \omega$. So this is a way of interpreting the phase shift via symplectic area.

What if we had a different capping disk, say $D'$? We don't want the phase shift to depend on our choice of disk. So glue $D$ and $D'$ along $\gamma$ to obtain an $S^2$. Then $\int_{S^2} \omega$ is an integer if $\omega$ is an integral class. And $\exp( 2\pi ki + P) = \exp P$ for $k \in \mathbb{Z}$. So this is another reason why it's good that $\omega$ is an integral class.


## The Aharonov-Bohm Effect

Now, despite introducing the action which uses the potential $A$, it may seem like what we still really care about is $F=dA$ and $A$ is simply an artifact. But the Aharonov-Bohm effect demonstrates the physical reality (and not only mathematical reality) of $A$ as well as provides an example of where fiber bundles appear in "real" life. Let's write down a few physics terms.

- **Solenoid:** Imagine a coiled wire, like a spring.
- **Magnetic Flux:** the measurement of the total magnetic field that passes through a given surface $S$ so in short, it is an integral $\int_S A$. Again, mathematically $A$ is a connection but in physics, we'd call it the **electromagnetic potential.** The curvature $F_A$ is the **magnetic field.**

So consider an experiment in which a solenoid has interior magnetic flux but there is no external magnetic fields. So mathematically, we have a connection $A$ whose curvature $F_A$ vanishes outside of the solenoid; i.e. $A$ is flat. However, when we shoot a beam of electrons past the solenoid, there is an interference pattern. This indicates that there were phase shifts for the electron even though there was no magnetic field acting on them.

What is the mathematical interpretation of this? Here is a [Wikipedia article](https://en.wikipedia.org/wiki/Aharonov%E2%80%93Bohm_effect#Mathematical_interpretation) on the matter, a Veritasium [video](https://www.youtube.com/watch?v=XKSjCOKDtpk&t=1120s), and below is my summary.

We can interpret the effect via fiber bundles. The revelant fiber bundle here is one of phases where the base $B$ represents physical space while the fibers represent all possible phases. Since phases differ by some angle between $0$ and $2\pi$, we can view the fibers as circles $S^1$. A connection gives us a way to lift a path in the base to the fibers. In particular, suppose we have a loop in the base which we lift to some path upstairs. The path might not be a loop and when it isn't a loop, this means that some phase shift occurred even though the electron travelled back to where it began.

Moreover, it's possible that $A$ is a flat connection and so there is no magnetic field to act on the electron and yet, if $A$ is nontrivial, there can still be phase shifts. Recall that $A$ is flat if and only if the holonomy depends only on the homotopy class of the loop. In this case, $A:\pi_1(B) \to U(1)$ can be viewed as a representation of the fundamental group and when the loop is not contractible, then there can be some phase shifts. Even if the path is not a loop, the electrons can pick up some phase shift.

**Question:** Why is the Aharonov-Bohm effect viewed as a quantum effect? It seems like all that is going on is classical field theory.

Perhaps one answer (most of this is given by Wiki) is that we can only measure the absolute value of the wavefunction $\|\psi\|$. We can measure phase differences through quantum interference experiments but there is no way to specify a wavefunction with constant _absolute_ phase. In the absence of an electromagnetic field, one can come close by declaring the eigenfunction of the momentum operator with zero momentum to be the function "1" (ignoring normalization problems) and specifying wave functions relative to this eigenfunction "1". Compare this to the situation in relativity: when there is no gravitating body, there is no favored frame of reference.

Anyways, in this representation, the $i$-momentum operator is (up to a factor $\hbar /i$) the differential operator $\partial_i=\frac {\partial }{\partial x^i}$. However, by gauge invariance, it is equally valid to declare the zero momentum eigenfunction to be $e^{-i\phi (x)}$ at the cost of representing the $i$-momentum operator (up to a factor) as $\nabla_i=\partial_i+i(\partial_i\phi )$. i.e. with a pure gauge vector potential (a 1-form) $A=d\phi$. 

There is no real asymmetry because representing the former in terms of the latter is just as messy as representing the latter in terms of the former. This means that it is physically more natural to describe wave "functions", in the language of differential geometry, as sections in a complex line bundle with a hermitian metric and a $U(1)$-connection $\nabla$. The curvature form of the connection, $iF=\nabla \wedge \nabla$, is, up to the factor $i$, the Faraday tensor of the electromagnetic field strength.

**A more technical summary of the effect:** The Aharonov–Bohm effect is then a manifestation of the fact that a connection with zero curvature (i.e. flat), need not be trivial since it can have monodromy along a topologically nontrivial path fully contained in the zero curvature (i.e. field free) region. By definition this means that sections that are parallel translated along a topologically non-trivial path pick up a phase, so that covariant constant sections cannot be defined over the whole field free region.

For a flat connection, one can find a gauge transformation in any _simply connected_ field free region (acting on wave functions and connections) that gauges away the vector potential. However, if the monodromy is nontrivial, there is no such gauge transformation for the whole outside region. In fact as a consequence of Stokes theorem, the holonomy is determined by the magnetic flux through a surface $S$ bounding the loop $\gamma$: $\exp(2\pi i \int_{\partial S} A)=\exp(2 \pi i\int_S dA)=\exp(2 \pi i \int_S F)$.
But such a surface exists only if $S$ passes through a region of non-trivial field. If $F=0$ on some region and $S$ passes through this region, then $\int_S F = 0$ but a nontrivial $A$ gives $\int_{\partial S} A \neq 0$ and Stokes theorem would be false.
