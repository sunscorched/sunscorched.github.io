---
title: 'Brieskorn Spheres'
date: 2026-01-31
permalink: /posts/2026/01/brieskornspheres/
tags:
  - algebraic topology
  - algebraic geometry
---

Let $a = (a_1,...,a_n) \in \mathbb{N}^n$ be an $n$-tuple of positive integers; we typically want $a_k > 1$. Let $V_a = \{z_1^{a_1}+...+z_n^{a_n}=0\} \subset \mathbb{C}^n$ be the complex algebraic hypersurface with an isolated singularity at the origin and let $M_a = \{z_1^{a_1}+...+z_n^{a_n}=\delta\}$ be the Milnor fiber which is a smooth manifold for small $\delta>0$. Actually, we'll also call $M_a$ the Milnor fiber which is what I just wrote but intersected with a small ball $B^{2n}$ centered as 0. We also have $\Sigma_a = S^{2n-1}_\epsilon \cap V_a$ which is called the link of the singularity, obtained by intersecting the singular variety with a small sphere centered at 0. This link is diffeomorphic to the boundary of $M_a$. We will explain some of the ideas for showing how $\Sigma_a$ is a homotopy sphere in many cases and how one finds their oriented diffeotype. We follow this [post](https://mathoverflow.net/questions/65705/how-to-calculate-the-exact-differential-structure-of-brieskorn-variety), these [slides](https://webhomes.maths.ed.ac.uk/~v1ranick/slides/singexot.pdf), and Brieskorn's original [paper](https://webhomes.maths.ed.ac.uk/~v1ranick/papers/brieskorn.pdf).

Recall that a homotopy $n$-sphere is a smooth $n$-manifold homotopy equivalent to $S^n$. For $n \neq 4$, these form finite abelian groups under connected sum and contain subgroups $bP_{n+1}$ of the homotopy $n$-spheres that bound parallelizable manifolds. Interestingly, when $n+1$ is even, then only the standard sphere bounds a parallelizable manifold. In dimensions $n=4m$, the intersection form is symmetric and the signature is the main invariant of interest. In dimensions $n=4m+2$, the intersection form is skew-symmetric and the Kervaire invariant (which only takes values 0 or 1) is the one of interest. These two invariants act as obstructions to surgering a bounding manifold into a ball of the appropriate dimension. In particular, $bP_{4m+2}$ is always either trivial or $\mathbb{Z}/2$. Now, [Kervaire-Milnor](https://www.uni-math.gwdg.de/schick/publ/Groups%20of%20homotopy%20spheres%20I.pdf) computed many of these groups and Brieskorn's paper implies the following:

**Theorem (Brieskorn-Hirzebruch):** Every homotopy sphere of dimension $4m+3$ ($m \geq 1$) which bounds a parallelizable manifold can be realized as a link of the form $\Sigma_a$ where $a = (2,2,...,2,3,6k-1)$ for some positive integer $k$. Phrased differently, these homotopy spheres all bound a parallelizable manifold that can be constructed by plumbing together $\mu$ (Milnor number) copies of $T S^{4m+1}$ using a nonsingular quadratic form.

There is also another result:

**Theorem (Levine):** For $4m+1$, $(m \geq 1)$, let $\Sigma_a$ be the homotopy sphere where $a=(2,2,...,2,3)$. This has Kervaire invariant 1 and if the subgroup $bP_{4m+2}=\mathbb{Z}/2$, then $\Sigma_a$ generates $bP_{4m+2}$.

With these two theorems together, then **every** homotopy sphere of odd dimension that bounds a parallelizable manifold is realized as a Brieskorn sphere. As we said above, all the even dimension homotopy spheres that bound parallelizable manifolds are standard spheres. It's incredible to me that we can produce so many exotic spheres from algebraic varieties.

Moving forward, we'll focus more on the $4m+3$ case. Recall that the Milnor fiber of a hypersurface singularity has the homotopy type of a bouquet of $S^{n-1}$ and so its only homology is located in degree $0,n-1$. The number of spheres in this bouquet is the Milnor number $\mu$ which, in the case of Brieskorn varieties is $\mu = (a_1-1)(a_2-1)...(a_n-1)$. For example, Milnor's original exotic 7-sphere can be realized by $\Sigma(2,2,2,3,5)$ and so $\mu = 8$. When $k=27$, then $\mu = 320$ which is quite large! More generally, the Milnor number is a homotopy invariant of a hypersurface singularity.

There is also a monodromy map for the Milnor fiber $\Phi:M \to M$ which comes from parallel transport of the Milnor fibration and induces a map $\Phi_\*:H_{n-1}(M_a,\mathbb{C}) \to H_{n-1}(M_a,\mathbb{C})$. The characteristic polynomial of $M_a$ is $\Delta(t) = \det(t\text{Id}-\Phi)$. It turns out that we can write $\Delta(t) = \prod_{0<i_k < a_k} (t-\zeta_1^{i_1}...\zeta_n^{i_n})$ where $\zeta_k = \exp(2\pi i/a_k)$.

**Theorem (Brieskorn):** For $n \geq 4$, $\Sigma_a$ is $(n-3)$-connected and is a homotopy sphere if and only if $\Delta_a(1) = 1$.

Brieskorn also proved that the Kervaire invariant of $M_a$ (which is the Arf invariant in a topological setting) is determined by $\Delta_a(-1)$. In particular, for a $(4m+1)$-homotopy sphere, it is 0 if $\Delta_a(-1) \equiv \pm 1 \pmod{8}$ and 1 if $\Delta_a(-1)\equiv \pm 3 \pmod{8}$.

We also have automorphisms $\omega_k$ given by multiplying the $k$th coordinate by $\zeta_k$; these generate a finite automorphism group $\Omega_a \cong \bigoplus^n \mathbb{Z}/(a_k)$. Let $J_a = \mathbb{Z}[\Omega_a]$ be the group ring and $I_a$ the ideal generated by elements of the form $1+\omega_k +...+\omega_k^{a_k-1}$. For example, if $a_k = 4$, we have $1+\omega_k+\omega_k^2 +\omega_k^3$. Pham showed that $H_{n-1}(M_a,\mathbb{Z}) \cong J_a/I_a$. Let $j = (j_1,...,j_n)$ where for each $k$, $0 < j_k < a_k$. There's a basis $v_j = \prod^n_{k=1}\sum^{a_k-1}_{r=0}\exp(2\pi i j_k r/a_k) \omega^r_k$.

In the basis $v_j + v_{a-j}$ and $i(v_j-v_{a-j})$ of $J_a/I_a \otimes \mathbb{R}$, the intersection form of $M_a$ is diagonalized. This implies that $\langle v_j + v_{a-j}, v_j + v_{a-j} \rangle = \langle i(v_j - v_{a-j}), i(v_j - v_{a-j}) \rangle = 2 \langle v_j,v_{a-j}\rangle$ and all the rest of the entries of the intersection form are 0.

Now, $\langle v_j,v_{a-j}\rangle > 0$ if and only if $0 < \sum j_k/a_k < 1 \pmod{2}$; that is, subtract all the copies of 2 that you can from this sum until you're between 0 and 1. Similarly, that term is negative if and only if $-1 < \sum j_k/a_k < 0 \pmod{2}$.

So from this, we can compute the signature. For the first case above, we just need to count the number of $n$-tuples $j$ satisfying the condition and similarly for the second. This will precisely give $\sigma^+$ and $\sigma^-$ and their difference is the signature $\sigma = \sigma^+-\sigma^-$ of the Milnor fiber which we can use as an invariant of the Brieskorn sphere $\Sigma_a$.

Kervaire-Milnor showed that $bP_{4m}$ is cyclic of order $\sigma_m/8$ where $\sigma_m = \epsilon_m 2^{2m-2}(2^{2m-1}-1)\text{numerator}(B_m/4m)$. Here, $\epsilon_m = 1$ if $m$ is even, and is $2$ if $m$ is odd. $B_m$ is the $m$th Bernoulli number and it grows quickly. The Brieskorn spheres $\Sigma_a$ of dimension $4m-1$ where $a = (2,2,...,2,3,6k-1)$ for $k=1,2,...,\sigma_m/8$ are given by $\sigma(M_a) = (-1)^m 8k \in \mathbb{Z}$.

For example, $\Sigma_a$ where $a = (2,2,2,3,5)$ is a homotopy 7-sphere which generates $bP_8 = \mathbb{Z}/28$. The number of homotopy spheres in some of these dimensions is quite large. For example, for $n=11$, there are $992$ homotopy spheres. In $n=15$, there are $16,256$ where half of them bound parallelizable manifolds and are Brieskorn spheres. And in $n=19$, there are $523,264$ where again, half of them bound parallelizable manifolds and are Brieskorn spheres.

## Appendix: _On Manifolds Homeomorphic to the 7-Sphere_ - 1956

I'd like to discuss the result that, in my opinion, really launched the subject of differential topology. This [paper](https://people.math.osu.edu/burghelea.1/MaterialDiffTopology/Milnorsphere.pdf) by John Milnor demonstrates that there is a smooth 7-manifold homotopy equivalent to the 7-sphere with different characteristic classes (rational Pontryagin classes) than the standard 7-sphere. At first, Milnor thought he found a counterexample to the Generalized Poincaré Conjecture (Theorem) which says that an $n$-manifold homotopy equivalent to an $n$-sphere is in fact, homeomorphic to it. But then, using Morse theory (Reeb's lemma), he discovered that his manifold is a topological 7-sphere. Therefore, he answered a question that no one was even asking: "Are there distinct smooth structures on manifolds?" His paper answers, "yes." Some years after this paper, Stephen Smale proved the Generalized Poincaré Conjecture for dimensions greater than 4.

The 7-manifold in the paper is constructed as follows. Consider $S^3 \subset \mathbb{H}$ to be the unit quaternions. We'll build an $S^3$ bundle over $S^4$ using quaternion multiplication. Specifically, take two copies of $B^4 \times S^3$, each with $S^3 \times S^3$ as boundary, and glue them together by identifying $(a,b)$ in the boundary of one with $(a,a^2 b a^{-1})$ in the other. As I said above, Milnor used Reeb's lemma: if a Morse function on a closed manifold has only two critical points (max and min), then the manifold must be topologically, a sphere. Intuitively, the flow lines cannot do anything complicated other than leave from the maximum and be absorbed into the minimum.

To show that this smooth manifold is not diffeomorphic to $S^7$, Milnor proved that it is not the boundary of any smooth 8-manifold with vanishing 4th Betti number. Of course, the standard $S^7$ is the boundary of $B^8$ which has vanishing 4th Betti number. He also shows that this manifold does not have an orientation-reversing diffeomorphism to itself but $S^7$ clearly does since it embeds into $\mathbb{R}^8$ and we can use a reflection in Euclidean space to get an orientation-reversing map.

To achieve this, lets think about general theory. $(M^7,\mu)$ be a closed, smooth 7-manifold with orientation $\mu \in H_7(M,\mathbb{Z})$ and $H^3=H^4=0$. By the work of Thom, every closed, orientable 7-manifold is the boundary of some 8-manifold. This is not true for unorientable since the unoriented cobordism ring is $\Omega^0_* \cong \mathbb{Z}/2[x_i:i \neq 2^n-1] = \mathbb{Z}/2[x_2,x_4,x_5,x_6,x_8,...]$. Observe that $x_2x_5$ is in degree 7. So $\Omega^O_7 = \mathbb{Z}/2$ though $\Omega^{SO}_7 = 0$.

Anyways, let $(W,\nu)$ be an oriented 8-manifold bounding $M$; that means $\nu \in H_\*(W,M)$ and $\partial \nu = \mu$. Next, we may consider a map $H^4(W,M)/\text{Tor} \to \mathbb{Z}$ by $\alpha \mapsto \langle \nu, \alpha^2 \rangle$. Because $H^3(M)=H^4(M) = 0$, the morphism $i:H^4(W,M) \to H^4(W)$ is an isomorphism and so we can pullback the 1st Pontryagin class. Let $q(W) = \langle \nu, i^*p^2_1(W) \rangle$ and let $\sigma(W)$ be the signature. Then, define $\lambda(M) = 2q(W) - \sigma(W) \pmod{7}$.

**Theorem (Milnor):** $\lambda(M)$ does not depend on $W$.

I won't give the proof of this here but I'll at least motivate where $\lambda$ comes from. Hirzebruch (using Thom's work), showed that for 8-manifolds, there is a signature formula:
$\sigma(W) = \langle \nu, \frac{1}{45}(7p_2(W) - p^2_1(W) \rangle$.

So $45 \sigma +q = 7\langle \nu, p_2 \rangle \equiv 0 \pmod{7}$ and $90\sigma + 2q \equiv -\sigma + 2q \equiv 0 \pmod{7}$.

There are other invariants like $\lambda(M)$ which are defined using a bounding manifold but are in fact, independent of the choice. For example, Rokhlin's invariant for homology 3-spheres. Anyways, we have two corollaries.

**Corollary 1:** If $\lambda(M) \not\equiv 0$, then $M$ is not the boundary of any 8-manifold $W$ with $b_4(W) = 0$.
If there were such a manifold $W$, then $p_1=\sigma = 0$ and so $\lambda(M) = 0$.

**Corollary 2:** If $\lambda(M) \not\equiv 0$, then $M$ does not admit an orientation-reversing diffeomorphism.
Write $-M$ as having the opposite orientation of $M$, we see that $\nu$ would need to be changed to $-\nu$ and $\sigma(-W) = -\sigma(W)$. Hence, $\lambda(-M) = -\lambda(M)$. On the other hand, if there were such a diffeomorphism, $\lambda(-M) = \lambda(M)$ and hence, must be 2-torsion. But only 0 is 2-torsion mod 7.

So what would be left to do is show that Milnor's 7-manifold has $\lambda \neq 0$. I won't do the computations; Milnor's original paper is quite short. Let $(h,j) \in \mathbb{Z} \oplus \mathbb{Z}$ and $f_{hj}:Sp(1) = S^3 \to SO(4)$ be defined by $f_{hj}(u)\cdot v = u^h v u^j$ for $v \in \mathbb{R}^4$. This gives a principal $Sp(1)$ bundle over $S^4$ which we denote as $P_{hj} \to S^4$.

For each odd integer $k$, let $M^7\_k$ be the total space of the principal $Sp(1)$-bundle $P_{hj}$ where $h+j=1, h-j=k$. In the example above, we have $(h,j) = (2,-1)$ and $k=3$. We have two lemmas from Milnor's paper:

**Lemma:** $\lambda(M_k) \equiv k^2 -1 \pmod{7}$.
**Lemma:** $M_k$ admits a Morse function with only two critical points and hence, is homeomorphic to a sphere (Reeb lemma).

The two of these together give us the following theorem:

**Theorem:** For $k^2 \not \equiv 1 \pmod{7}$, $M_k$ is homeomorphic to $S^7$ but not diffeomorphic to $S^7$. For $k = \pm 1$, the manifold is diffeomorphic to $S^7$.

So for $k=3$, $3^2 \equiv 2 \pmod{7}$ and hence, $M^7_3$ is an exotic 7-sphere. At the time the paper was written, Milnor did not know what other $k$'s give a manifold diffeomorphic to $S^7$. For example, $k=13,15$ both satisfy $k^2 \equiv 1 \pmod{7}$ but they might not be the standard sphere. The residues of $k^2$ for odd $k=1,3,5,7,9,11,13$ is $1,2,4,0,4,2,1$ and then this repeats. So in fact, Milnor found three 7-manifolds homeomorphic to $S^7$ but not diffeomorphic to it.

As the reader may have noticed, John Milnor's work was featured many times in this post. Milnor proved the existence of exotic spheres and then with Kervaire, studied them in detail. Milnor also wrote one of the first books (that I know of) on Morse theory and also a great book on complex hypersurface singularities where Milnor fibers appear.


