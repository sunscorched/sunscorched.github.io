---
title: "Donaldson's Diagonalization Theorem"
date: 2026-06-12
permalink: /posts/2026/06/diagonalization/
tags:
  - 4-manifolds
  - gauge theory
---

For the month of May, I planned to write a series of posts about some spectacular applications of moduli spaces. Alas, I was delayed but here is the first in the series, about Donaldon's work on instantons and the Diagonalization Theorem which he proved in his thesis and was awred the Fields Medal. See Freed-Uhlenbeck or Nabler's survey on the subject. I will also discuss some corollaries such as the existence of exotic $\mathbb{R}^4$s and further aspects of Donaldson theory.

**Theorem (Donaldson, 1983):** Let $M$ be a compact, simply connected, oriented smooth 4-manifold with positive definite intersection form $Q$. Then $Q \simeq \bigoplus^m (1)$ over $\mathbb{Z}$. Here, $m$ is half the number of solutions $\alpha$ to $Q(\alpha,\alpha) = -1$.

**Remark 1:** One can always diagonalize over $\mathbb{R}$ and maybe even $\mathbb{Q}$. But this theorem says that if a unimodular symmetric bilinear form over $\mathbb{Z}$ is the intersection form of a compact, simply-connected, oriented, **smooth** 4-manifold, then it is diagonalizable over $\mathbb{Z}$. Compare this to Freedman's theorem which says that every unimodular symmetric bilinear form over $\mathbb{Z}$ arises as the intersection form of some compact, simply-connected, oriented, **topological** 4-manifold.

**Remark 2:** We do not actually need that $\pi_1(M) = 0$. Rather, we just need that any morphism $\pi_1(M) \to SU(2)$ is trivial. This implies that every flat $SU(2)$ bundle over $M$ is trivial. Also, every abelian group $G$ admits a representation to $S^1 \subset SU(2)$. For instance, when $G$ is moreover finitely generated, then it has cyclic pieces which we can map nontrivially to $S^1$.
But if every morphism $\pi_1(M) \to SU(2)$ is trivial, then the abelianization, $H_1(M) = \pi_1/[\pi_1,\pi_1] = 0$ since otherwise, it would give a nontrivial morphism to $S^1$ and hence, there would be a nontrivial morphism $\pi_1(M) \to SU(2)$. Groups which equal their commutator are called **perfect** and so a sufficient condition for $\pi_1(M) \to SU(2)$ to always be trivial is if $\pi_1(M)$ is a perfect group. An example is the binary icosahedral group which is the fundamental group of the Poincaré homology sphere.

**Remark 3:** We can change the orientation of $M$ and the result will be a negative definite intersection form and we would study the anti self-dual equations. Since there is not much difference, we'll use the ASD equations since, in the context of complex geometry, this is actually preferable. In the context of smooth geometry, there is no difference.

## Brief Remarks on Constructing the Moduli Space

Let $M$ be a closed, smooth, and simply connected 4-manifold and equip it with a Riemannian metric $g$. Consider a principal $SU(2)$ bundle $P \to M$ with $c_2(P)=1$. A connection $A$ on this bundle has curvature $F_A$ and there is also a Hodge star operator $\*$ defined by $g$. The anti-self dual equation is $\*F_A = -F_A$ and the space of ASD connections (or "instantons" as physicists say) on the bundle satisfying this equation forms an infinite dimensional space. When we quotient by the group of gauge transformations, we get a moduli space $\mathcal{M}$. Using the Atiyah-Singer index theorem, a connected portion of this space is exactly 5-dim.

The moduli space is not smooth even if we use a generic Riemannian metric $g$. There are reducible connections which have stabilizer group $U(1)$ rather than only the center of $SU(2)$ which is $\pm \text{Id}$. One result is that the associated complex vector bundle to $P$ splits as a direct sum of line bundles $L\oplus L^*$. These reducible solutions will be important later.

The moduli space is noncompact because energy can concentrate at a single point, a phenomenon known as instanton bubbling. Uhlenbeck proved compactness results to establish how these instantons behave with bubbling while Taubes proved some gluing theorems which Donaldson used to establish that one of the boundary components of $\mathcal{M}$ is the original manifold $M$. The topology of $\mathcal{M}$ is independent of the choice of metric $g$.

## Properties of the Moduli Space

The moduli space $\mathcal{M}$ of $SU(2)$ ASD connections for a principal bundle $P \to M$ with $c_2(P) = 1$ has a number of important properties when $M$ is negative definite. Let $\eta$ be the associated rank 2 complex bundle.

1. Let $m$ be half the number of solutions to $Q(\alpha,\alpha)=-1$. Then for almost all metrics on $M$, there exist $p_1,...,p_m \in \mathcal{M}$ such that $\mathcal{M} \setminus \{p_1,...,p_m\}$ is a smooth 5-manifold. The points $p_i$ are in 1-1 correspondence with topological splittings $\eta =\lambda \oplus \lambda^{-1}$.
2. There exist neighborhoods $U_i$ of $p_i$ such that $U_i$ is a cone over $\mathbb{CP}^2$; these arise from the reducible solutions.
3. $\mathcal{M}$ is orientable.
4. $\mathcal{M} \setminus \{p_1,...,p_m\}$ is non-empty and there exists a collar $(0,\epsilon] \times M \subset \mathcal{M}$. Let $\overline{\mathcal{M}} = \mathcal{M} \cup M$. Then $\overline{\mathcal{M}} \setminus \{p_1,...,p_m\}$ is a smooth 5-manifold with boundary.
5. $\overline{\mathcal{M}}$ is compact.

**Remark 3:** Thom proved that the signature is a cobordism invariant of closed, orientable 4-manifolds. So we know that $M$ is cobordant to a connected sum of $p\mathbb{CP}^2 \\#q\overline{\mathbb{CP}}^2$ and that $p-q = \sigma(M)$. We can even arrange for $p+q$ is equal $b_2(M)$ or some other number. But _a priori,_ none of that has any relationship to $m$ which, I remind you, is half the number of solutions $\alpha$ to $Q(\alpha,\alpha) = -1$. We take half since, if $\alpha$ satisfies this, then so does $-\alpha$. I'll keep reminding you of what this $m$ is because it was the source of my confusion. I originally though that Donaldson's work, in the end, only gives us a cobordism. But Thom already proved that such a cobordism exists, so what's the big deal? The big deal is that this $m$ has multiple interpretations, one of them being the number of reducible ASD connections (modulo gauge).

**Lemma:** The intersection form of $M$ is negative definite if and only if there are no self-dual harmonic 2-forms on $M$.

**Proof:** Recall that $Q(\alpha,\beta)$ can be viewed from a differential forms perspective. Suppressing the notation for Poincaré duality, $Q(\alpha,\beta) = \int_M \langle \alpha,\beta \rangle d\text{Vol} = \int_M \alpha \wedge \*\beta$. For example, if $\*\alpha = \pm \alpha$, then $Q(\alpha,\alpha) = \pm \int \|\alpha\|^2 d\text{Vol}$. Let $\omega = \omega_+ + \omega_-$ be a decomposition of a nontrivial harmonic 2-form into its self-dual and anti self-dual parts. Then $\|\omega\|^2 = \|\omega_+\|^2 - \|\omega_-\|^2$. Also, $Q(\omega_-,\omega_-) = -\|\omega_-\|^2$. If $\omega$ is self-dual, then $\|\omega\|^2$ is nonnegative and so $Q(\omega,\omega) > 0$ since $\omega$ is nontrivial. The intersection form couldn't be negative definite in that case. If all the harmonic forms are anti-self dual, then by some Hodge theory, $b^-_2$ is the dimension of these anti-self dual harmonic forms. $\square$

**Proposition:** Suppose $M$ has a negative definite intersection form. Then for split $SU(2)$ bundles $\eta = \lambda \oplus \lambda^{-1}$, there is a unique anti self-dual Yang-Mills connection 

$$A =\begin{pmatrix} e^{i\theta} & 0 \\ 0 & e^{-i\theta} \end{pmatrix}.$$

**Proof:** Connections on $\lambda,\lambda^{-1}$ induce connections on $\lambda \oplus \lambda^{-1}$ and by the lemma above, the curvature must be anti self-dual. Conversely, a split anti-self dual connection on $\lambda \oplus \lambda^{-1}$ is anti-self dual when restricted to each line bundle. The connections are gauge equivalent by split gauge transformation. $\square$

Such split connections are called reducible because, indeed, if we think of them as connections on a flat $SU(2)$ bundle, they give us representations of $SU(2)$ acting on $\mathbb{C}^2$. But such a splitting means that the representation are reducible. Moreover, reducible solutions have nontrivial stabilizers by the gauge group and this is why they give some singularities (the cones) in the moduli space $\mathcal{M}$. Why should these be in 1-1 correspondence with $\alpha \sim -\alpha$ where $Q(\alpha,\alpha) = -1$? I'm not completely sure but a reducible connection $A$ may be thought of as a $U(1)$ connections and the curvature would lie in $H^2(M,\text{Lie}\, U(1)) = H^2(M,\mathbb{R})$. Being anti self-dual, $*F_A = -F_A$ and after normalizing, say, dividing by $2 \pi$, we get an integral class which I'll still denote as $F_A$. This class satisfies: $Q(F_A,F_A) = -\int \|F_A\|^2 d\text{Vol} = -1$. It seems that there is a $\mathbb{Z}/2$ ambiguity since $A$ and the conjugate matrix $\overline{A}$ are gauge equivalent; so we divide by 2.

Alnteratively, following Lawson and using self-dual equations, an element $u \in H_2$ with $u \cdot u=1$ gives $c_1(L) = \text{PD}(u)$ (Poincaré dual) for some line bundle $L$. Taking the conjugate line bundle $\bar{L}$ splits the bundle as $E=L \oplus \bar{L}$. Again, one has to divide the number of classes by 2, because switching $L$ and $\bar{L}$ doesn't change the _real_ isomorphism class of $E$ (the two bundle are complex conjugates of one another).

In fact, Lawson shows that a reducible $SU(2)$ connection isn't just equivalent to a splitting but to a _parallel_ splitting. He finds a bundle map $y: E \to E$ coming from the Lie algebra, from which he gets the splitting by taking eigenvalues of that map, using that $\text{Lie} \,U(1)=i\mathbb{R}$. The eigenspaces of this bundle map are $L$ and $\bar{L}$, and then this bundle map is "parallel" in the normal sense that if $\nabla$ is the induced connection on $\text{End}(E)$, then $\nabla y=0$.

## Sketch of Proof of the Diagonalization Theorem

Let's suppose that $M$ has negative definite intersection form. The boundary of the moduli space $\mathcal{M}$ is $M \sqcup p \mathbb{CP}^2 \sqcup q\overline{\mathbb{CP}}^2$ where $p,q \geq 0$ and $p+q=m$, the number of equivalence classes of reducible ASD connections or half the number of solutions $\alpha$ to $Q(\alpha,\alpha)=1$. Since $b^+_2 = 0$, then $\sigma(M) = -b^-_2 = p-q$ and also $b_2 = b_2^- = -p+q$. In particular, $b_2 \leq p+q$. We would like to show that $b_2 \geq p+q$ as well and hence, $b_2 = p+q=m$. This is important because the elements satisfying $Q(\alpha,\alpha)=1$ give us a way to diagonalize parts of the intersection form over $\mathbb{Z}$. By showing that $b_2=m$, we are showing that the entire intersection form is diagonalizable over $\mathbb{Z}$.

Suppose $p+q>0$ because otherwise, the intersection form is trivial. Then there is an $\alpha_1 \in H_2(M,\mathbb{Z})$ such that $Q(\alpha_1,\alpha_1) = -1$. This means that there is an orthogonal decomposition $H_2(M,\mathbb{Z}) = \mathbb{Z}\langle \alpha_1\rangle \oplus G_1$. For any $\beta \in H_2$, $\beta = -Q(\alpha_1,\beta) \alpha_1 + (\beta + Q(\alpha_1,\beta)\alpha_1)$. Then, writing $Q(\alpha_1,\beta)$ as $q$, $Q(-q\alpha_1, \beta + q\alpha_1) = -q^2 -q^2Q(\alpha_1,\alpha_1) = -q^2+q^2=0$.

Next, take $\alpha_2 \neq \pm \alpha_1$ which satisfies $Q(\alpha_2,\alpha_2) = -1$. The Schwartz Inequality says $Q(\alpha_1,\alpha_2)^2 < Q(\alpha_1,\alpha_1)Q(\alpha_2,\alpha_2) = +1$. (it is strict because $\alpha_2$ and $\alpha_1$ are linearly independent). Since these are $\mathbb{Z}$ valued, this implies that $Q(\alpha_1,\alpha_2) = 0$. So they are orthogonal and $\alpha_2 \in G_1$. Applying the same reasoning to $\alpha_2$, $G_1$ decomposes orthogonally and we then have, $H_2(M,\mathbb{Z}) = \mathbb{Z} \alpha_1 \oplus \mathbb{Z}\alpha_2 \oplus G_2$. By iterating this procedure, we obtain $H_2(M,\mathbb{Z}) = \mathbb{Z}\alpha_1 \oplus...\oplus \mathbb{Z} \alpha_m \oplus G$ where $G$ is either empty or the orthogonal complement of all the other pieces. Hence, $b_2 \geq p+q$ and therefore, $b_2 = p+q$. So then $G$ is empty and hence, we've diagonalized $H_2(M,\mathbb{Z})$ over $\mathbb{Z}$. $\square$

## Corollaries

**Corollary 1:** Let $M$ be a closed, simply-connected, orientable 4-manifold. If it's intersection form $Q \neq 0$, is definite, and $Q(\alpha,\alpha) \neq \pm 1$ for all $\alpha \in H_2(M,\mathbb{Z})$, then $M$ is not smoothable. This holds, for example, if $Q$ is even.

If it were smoothable, then we can diagonalize it. But being unimodular, this requires all the elements of the diagonal to be $\pm 1$. So a well known example of a non-smoothable 4-manifold is the one with $E_8$ as its intersection form since it is definite yet not diagonalizable over the integers. In fact, there is an abundance of positive definite, even intersection forms. In rank 32, there are at least 80 quadrillion. There are also many odd positive definite forms which do not take the value 1.

**Corollary 2:** Let $M$ be smooth, simply connected. If $Q$ is even and definite, then $M$ is homeomorphic to $S^4$. If $Q$ is odd and positive definite, it is a connected sum of $\mathbb{CP}^2$s.

Now, one can try to build a smooth manifold with the $E_8$ lattice as its intersection form. The mission will fail but we can try to see how far we get and where it fails. One would glue smooth pieces in a plumbing construction and find that the self-intersection of 2-spheres presents a problem in the smooth category; these are called Casson handles. Freedman had proved that topologically, the Casson handles are simply standard 2-handles. Let $U$ be the interior of the Casson handle. If it were diffeomorphic to $\mathbb{R}^4$, then we can smoothly embed an $S^3$ into it and then we can chop off the complicated exterior and glue in a smooth $B^4$. The result would be a smooth, closed 4-manifold with $E_8$ as lattice which contradicts the Diagonalization Theorem. Therefore:

**Corollary 3:** There exists an open manifold $U$ homeomorphic to $\mathbb{R}^4$ and compact set $K$ such that one cannot smoothly embed $S^3$ in such a way that it bounds $K$. Thus, $U$ is not diffeomorphic to $\mathbb{R}^4$.


## Higher Topological Charge $k = c_2(P)$

In general, we could have chosen a larger topological charge for the $SU(2)$-bundle $P \to M$. One way of thinking about a large $k$ is to just imagine we have more instantons on $M$ and at a distance, they might not interact but as they get closer, they could interact.

The dimension of the moduli space of ASD connections for topological charge $k$ is given by the Atiyah-Singer index theorem: $8k-3(1-b_1+b^+)$. Here, $b_1$ is the 1st Betti number of $M$ and $b^+$ is the dimension of the maximal subspace on which the intersection form is positive definite. Another way to write this is $\frac{3}{2}(\chi + \sigma)$ where $\chi = 2-2b_1 + b^+ + b^-$ is the Euler characteristic and $\sigma = b^+ - b^-$ is the signature.

When $M = \mathbb{R}^4$ and $k = 1$, the dimension is 5. An intuitive idea for this is that $5 = 4+1$. We have 4 spacetime parameters for placing the location of the instanton. And then we have one parameter that tells us how much the curvature concentrates at a point. In the case of $M = S^4$, the moduli space $\mathcal{M}_1 = B^5$, the 5-ball. The center of the ball corresponds to an instanton that is uniformly spread out over the whole of $S^4$. As you move in straight line towards the boundary, this means the instanton is starting to concentrate around a point in $S^4$. At the limit, the energy is all concentrated at that point.

**Question:** But what about $k = 2$ and higher $k$? Why doesn't it increase by 5 each time?
**Answer:** If we add a second instanton, then we can quotient things out by gauge. But now, since there are two instantons, the gauge can only fix their relative directions. So if we fix one of them, the other has some $SU(2)$-freedom and $\dim SU(2)=3$.

Let's study $\mathbb{CP}^2$ and $\mathbb{P}^1 \times \mathbb{P}^1$. Both are simply connected and both have $b^+ = 1$. So for $k=1$, the virtual dimension is $-1$ and hence, there are no ASD connections: the moduli space is empty. Now, suppose we didn't have the virtual dimension and we just expect that $\mathbb{CP}^2$ has a 5 dimensional moduli space. What would go wrong? The moduli space would bound $\mathbb{CP}^2$ and it might have some cones on the other end. But those cones correspond to reducible solutions which correspond to $\alpha$ such that $Q(\alpha,\alpha)=-1$; there aren't any such elements. So then $\mathbb{CP}^2$ would bound a 5-manifold. By Thom's theorem, this means $\sigma(\mathbb{CP}^2) = 0$; but the signature is 1. There is our contradiction.

For $k=2$, the dimension of the moduli space is 10. Their descriptions are given in Donaldson-Kronheimer's book, p. 127.
For $\mathbb{CP}^2$, $\mathcal{M}_2$ can be described thusly. Let $\mathbb{P}^\*$ be the dual projective plane. That is, a point in $\mathbb{P}^\*$ corresponds to complex projective lines of $\mathbb{CP}^2$. The conics in this dual space are defined by homogeneous equations of degree 2; these form a 6 complex dimensional space; the basis can be viewed as: $x^2,y^2,z^2,xy,yz,xz$. We then projectivize to get $\mathbb{CP}^5$. Then $\mathcal{M}_2$ is the open subset of $\mathbb{CP}^5$ of nonsingular conics. Singular conics are given by the symmetric product $\text{Sym}^2 \mathbb{CP}^2$ (unordered pairs of points); these are pairs of lines (including double lines) in $\mathbb{P}^\*$; this corresponds to points in $\mathbb{CP}^2$.

For $\mathbb{P}^1 \times \mathbb{P}^1$, let's view it as embedded as a quadric $Q \subset \mathbb{CP}^3$. The moduli space $\mathcal{M}_2$ is a subset of nonsingular quadrics in $\mathbb{CP}^3$ which includes $Q$ itself. The space of all quadrics has complex dimension 10 and when we projective, it has complex dimension 9. We then consider all $Q'$ such that it intersects $Q$ in four lines (one pairs from each of the rulings of $Q$, we allow counts of multiplicity 2). This is a singular complex variety $K$ of complex dimension 5. moreover, if $Q' \neq Q$ is an element, then so is $Q' + tQ$ for $t \in \mathbb{C}$. So $K$ is a cone and $\mathcal{M}_2$ is an open subset of this cone.

## Appendix

We can think about Yang-Mills theory in a more general setting. Let $G$ be a compact Lie group with Lie algebra $\mathfrak{g}$ and $P \to M$ a principal $G$ bundle over a Riemannian manifold $(M,g)$. We also can study connections $A$ on $P$ with curvature $A \in \Omega^2(M,\text{ad}\, P)$. That is, we have an adjoint representation $\text{ad}:\mathfrak{g} \to \text{End}(\mathfrak{g})$ which comes from using the Lie bracket; it is induced by conjugation $\text{Ad}:G \to \text{Aut}(G)$ which assigns to $g$ the map $x \mapsto gxg^{-1}$. We may choose an $\text{ad}$-invariant inner product on $\mathfrak{g}$ and use the metric on $M$ to define pointwise norms.

Let $\mathcal{Y}(A) = \frac{1}{2}\int_M \|F_A\|^2 \, d\text{Vol}_g$ be the **Yang-Mills functional.** It is gauge invariant, only depending on the gauge equivalence class of $A$. Interetingly, in dimension 4, it is also conformally invariant; i.e. it only depends on the conformal class of $g$.

The derivative of $\mathcal{Y}$ is found by looking at $A +ta$ for $a \in \Omega^1(M,\text{ad}\, P)$ and then differentiating with respect to $t$ and setting $t=0$ afterwards. We'll find that
$\left. \dfrac{d}{dt}\right|_{t=0}\mathcal{Y}(A+ta) = \int_M \langle d^*_AF_A,a\rangle \, d\text{Vol}_g$.

Thus, a critical point of this functional is a connection $A$ whose curvature satisfies $d^*_A F_A =0$; this is the Euler-Lagrange equation. If a connection satisfies this equation, since all connections satisfy the Bianchi identity $d_A F_A=0$, we say $F_A$ is a harmonic 2-form with values in $\text{ad}\, P$.

Now, if $F_A =0$, then we say $A$ is a **flat connection** (no curvature) and it obviously satisfies $d^*_AF_A =0$ and moreover, $\mathcal{Y}(A)=0$. So flat connections are global minima of $\mathcal{Y}$.

In dimension 4, Hodge start acts on 2-forms which are linear combinations of self-dual and also anti-self-dual connections. These are automatically critical points of $\mathcal{Y}$ because $\*F_A = \pm F_A$ and so $d_A^\* F_A = d_A(\*F_A) = \pm d_A F_A = 0$ by the Bianchi identity. Once we fix our isomorphism class of principal bundle $P \to M$ which is determined by $c_2(P) \in H^4(M,\mathbb{Z}) = \mathbb{Z}$ which we treat as an integer $k$, then we'll see that the ASD connections minimize $\mathcal{Y}$ in their topological class.

By this, I mean that $2\mathcal{Y}(A) = \int_M \|F_A\|^2 = \int_M (\|F^+_A\|^2 + \|F^-_A\|^2)$. On the other hand, $8\pi^2 k = \int_M(\|F^+_A\|^2 - \|F^-_A\|^2)$ so $\int_M\|F_A\|^2 = \pm 8\pi^2 k + 2\int\|F_A^\mp\|^2$. Self-dual connetions have $F_A = F^+_A$ and anti-self-dual have $F_A = F^-_A$. If $k < 0$, then an ASD connection minimizes $\mathcal{Y}$, giving a value of $8\pi^2\|k\|$.

I'm not sure what the other critical points of $\mathcal{Y}$ mean in physics but I believe they are studied.
