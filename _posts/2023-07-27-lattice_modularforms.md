---
title: 'Lattices and Modular Forms'
date: 2023-07-27
permalink: /posts/2023/07/lattice_modularforms/
tags:
  - modularforms
  - lattices
---

I am not a number theorist but this topic has fascinated me. The classification of definite forms is very difficult but also appears in the study of 4-manifolds since Freedman proved that closed, oriented, simply-connected, topological 4-manifolds are classified by their intersection form. This post isn't about that so much. Without loss of generality, let's assume that $Q$ is positive definite. If $Q$ is **even**, then its rank and signature are both divisible by 8.

Under the identification of $Q$ with the Euclidean inner product, the domain of $Q$ is identified with some lattice $\Gamma \subset \mathbb{R}^n$. We can write a basis for the lattice and the absolute value of the determinant of the basis is called the **covolume.** In our case, the covolume is 1. 

Since $Q$ is unimodular, $\Gamma$ is isomorphic to its dual. Associated to $\Gamma$ is a **theta function:**
$\theta_\Gamma(q) := \sum_{x\in \Gamma} q^{(x \cdot x)/2}$.

**Example:** Let $\Gamma = 2 \mathbb{Z}$ and so $\theta(q) = 1+ \sum_{n=1}^\infty 2q^{\frac{1}{2}(2n)^2} = \sum^\infty_{-\infty} q^{2n^2}$. If we square this function $\theta(q)^2 = (1+2q^2+2q^8+2q^{32}+...)(1+2q^2+2q^8+2q^{32}+...)$ and write it as $\sum c_{2m}q^{2m}$, the coefficient $c_{2m}$ counts ordered pairs $(a,b) \in \mathbb{Z}^2$ such that $2m = \frac{1}{2}((2a)^2+(2b)^2)$; in other words, it tells us the number of ordered pairs $(a,b) \in \mathbb{Z}^2$ such that $a^2+b^2 = m$. Note that sometimes, we're counting $(\pm a,\pm b)$ and also $(\pm b,\pm a)$ as distinct pairs. And if we have $(0,b)$, then the $\pm$ doesn't affect 0. Here are the first few coefficients:
$\theta(q)^2 = 1 + 4q^2+4q^4+4q^8+8q^{10}+...$
The number of ways to write $1$ as a sum of squares is 4. We have $(\pm 1)^2 + 0^2$ and $0^2 + (\pm 1)^2$. We can write 5 as $(\pm 1)^2+(\pm 2)^2$ or $(\pm 2)^2 + (\pm 1)^2$. Hence, 8 ways. Note that there aren't any ways to write 3 as a sum of two squares.

Being even, $(x\cdot x)/2$ is an integer and so this is an ordinary Taylor series in $q$. These exponents are also nonnegative (that's how the Euclidean dot product is). Also, if we have a basis for the lattice $\{e_1,...,e_n\}$ and $x = \sum a_i e_i$, then $x \cdot x = \sum^n a^2_i e^2_i + 2\sum_{i,j} a_i a_j e_i \cdot e_j$. The first term is at least $\sum^n a^2_i$ since $e^2_i \geq 1$. As the $a_i$ grow, $x \cdot x$ grows like a polynomial of degree $n/2$. If we make the substitution $q = e^{2\pi i t}$, then $\theta_\Gamma(t) = \sum_{x \in \Gamma} e^{\pi it (x \cdot x)}$ and
$\theta_\Gamma(it ) = \sum_{x \in \Gamma} e^{-\pi t (x \cdot x)}$.

The **Poisson summation formula** for a function $f$ on $\mathbb{R}^n$ decaying sufficiently fast at infinity, says that for any lattice $\Lambda \subset \mathbb{R}^n$, the sum of values of $f$ on $\Lambda$ equals the sum of values of its **Fourier transform** on the dual lattice $\Lambda$. Here, $\Gamma \cong \Gamma^*$ because of unimodularity. Moreover, $e^{-\pi |x|^2}$ is its own Fourier transform (here, I'm just writing $|x|^2$ to mean $x \cdot x$). I'll prove it below for $n=1$.

**Lemma:** If $\varphi(x) = e^{-\pi |x|^2}$, then the Fourier transform $\hat{\varphi}(\xi) = e^{-\pi |\xi|^2}$.

**Proof:** Let's just work on $\mathbb{R}$ though the same proof works on $\mathbb{R}^n$. $\hat{\varphi}(\xi):= \int^\infty_{-\infty} \exp(-\pi x^2-2\pi ix \xi) \, dx$. We can multiply by $1 = e^{-\pi \xi^2} e^{\pi \xi^2}$. Moving the second term into the exponent since it has no $x$ dependence, we have that the exponential becomes: $\exp(-\pi(x^2+2ix \xi -\xi^2)) = \exp(-\pi x+i\xi^2)$. Substituting $u = x+i\xi, du = dx$, we have that $\hat{\varphi}(\xi) = e^{-\pi \xi^2} \int^\infty_{-\infty}  e^{-\pi u^2}\, du$. The integral is the Gaussian integral and it equals 1. So $\hat{\varphi}(\xi) = e^{-\pi \xi^2}$. For $\mathbb{R}^n$, we would basically do the same thing by studying a product: $\prod^n_j \int^\infty_{-\infty} \exp(-\pi x^2_j - 2\pi i x_j \xi_j)$. $\square$

So, each term in the theta function is its own Fourier transform and $\Gamma \cong \Gamma^*$. The Fourier transform of $e^{-\pi t x^2}$ is almost the same but is $t^{-n/2}e^{-\pi \xi^2/t}$. So, by the Poisson summation formula, $\theta_\Gamma(it) = \sum_{x \in \Gamma} e^{-\pi t x^2} = \sum_{x \in \Gamma} t^{-n/2} e^{-\pi \xi^2/t} = t^{-n/2} \sum_{x \in \Gamma} e^{-\pi \xi^2/t}$. On the other hand, $\theta_\Gamma((i/\sqrt{t})^2) =\theta_\Gamma(-1/t) = \sum_{x \in \Gamma} e^{- \pi i x^2/t}$. Hence, $\theta_\Gamma(-1/t) = t^{n/2}\theta_\Gamma(it)$. Lastly, $\theta_\Gamma(-1/t) = (it)^{n/2}\theta_\Gamma(t)$.

Recall that the transformation $t \mapsto -1/t$ is given by one of the generators of $SL(2,\mathbb{Z})$. 

Also, $\theta_\Gamma(t + 1) = \sum e^{\pi i(t+1)x^2}$. Since $x\cdot x$ is even, $e^{\pi i x^2} = 1$. Hence, $\theta_\Gamma(t+1) = \theta_\Gamma(t)$. This transformation $t \mapsto t+1$ is the other generator of $SL(2,\mathbb{Z})$. Hence, $\theta_\Gamma$ is a **modular form** of weight $n/2$. This is an integer since $n$ is a multiple of 8.

#### Brief Aside on Modular Forms

Let $\Gamma \subset SL_2(\mathbb{Z})$ be a finite index subgroup; this is not the same $\Gamma$ as above but since this is the standard notation in the literature, I'll use it here. Recall that a **modular form of weight $k$ and level $\Gamma$** is a holomorphic function $f:\mathbb{H} \to \mathbb{C}$ on the upper-half plane satisfying:
1. $f(\frac{a\tau + b}{c \tau +d})= (c\tau+d)^{-k} f(\tau)$ for $\begin{matrix} a & b \\ c & d \end{matrix} \in \Gamma$.
2. $f$ is bounded as $\tau \to i \infty$.

Let $\pi_N:SL_2(\mathbb{Z}) \to SL_2(\mathbb{Z}/N\mathbb{Z})$ be reduction mod $N$ on matrices. Typically, we want $\Gamma$ to contain $\Gamma(N) = \ker \pi_N$; we call such $\Gamma$ **congruence subgroups.** If we're studying $\Gamma = SL_2(\mathbb{Z})$, then we only need to check that $f$ satisfies property (1) for the generators $T=\begin{pmatrix} 1 & 1 \\ 0 & 1 \end{pmatrix}, S = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}$. This is what we did above with the theta function $\theta_\Gamma$. One can sort of see why modular forms are related to rank 2 lattices in $\mathbb{C}$ since $SL_2(\mathbb{Z})$ just changes the basis vectors and we only need to check the upper-half plane since we can take $\tau, 1$ as a basis where $\tau \in \mathbb{H}$.

The boundary of $\mathbb{H}$ is $\mathbb{RP}^1$ and we can also consider $\mathbb{QP}^1 = \mathbb{Q} \cup \infty$. Then, an element $\begin{pmatrix} a & b \\ c & d \end{pmatrix} \in SL_2(\mathbb{Z})$ sends $x \in \mathbb{Q}$ to $(ax+b)/(cx+d)$ and sends $\infty$ to $a/c$. If $cx+d = 0$, then $x \mapsto \infty$. The **cusps** of a subgroup $\Gamma$ are the $\Gamma$-orbits. For example, if $\Gamma = SL_2(\mathbb{Z})$ we see that $0 \mapsto b/d$. Given any $b,d$ with $\gcd(b,d) = 1$ (so the fraction is fully reduced), then we just need to find $a,c$ so that $ad-bc=1$ to form an element of $\Gamma$. This is guaranteed by the Euclidean algorithm. And also, any matrix with $d=0$ sends $0 \mapsto \infty$. Hence, there is one orbit and thus, $SL_2(\mathbb{Z})$ itself has one cusp.

As we saw above, it turns out that any even, unimodular rank $8m$ lattice produces a modular form of weight $4m$ for $SL_2(\mathbb{Z})$ because we have a Poisson summation formula in the setting of unimodular lattices. The definitions of modular forms makes it clear that the modular forms of weight $k$ and level $\Gamma$ form a vector space and in fact, can be alternatively described in the following way. 

Let $M_k(\Gamma)$ denote the space of modular forms of weight $k$, level $\Gamma$. Define the modular curve to be $X_\Gamma = \Gamma ∖ ( \mathbb{H} \cup \mathbb{QP}^1)$. That is, we take the upper-half plane; it has $\mathbb{RP}^1$ as the boundary at infinity; we add in the rational points. We then quotient by the action of $\Gamma$. Let $\omega$ be the canonical line bundle on this curve; then the holomorphic sections of $\omega^{\otimes k}$ is denoted $H^0(X_\Gamma,\omega^{\otimes k})$ and it's not hard to see that this is isomorphic to $M_k(\Gamma)$. Hence, the dimensions of these spaces of modular forms can be computed using the Riemann-Roch formula. One of the interesting things is that $M_k(SL_2(\mathbb{Z})) = \mathbb{C}\cdot G_{2k} \oplus S_k$ decomposes into the direct sum of a 1-dim subspace generated by the $2k$-Eisenstein series and the so-called **cusp forms** of weight $k$. These are modular forms that, when we extend them to $\overline{\mathbb{H}} = \mathbb{H} \cup \mathbb{QP}^1$, they vanish on the cusps of $\Gamma$.

The definition of the Eisenstein series is straightforward:
$G_{2k}(t):= \sum_{(m,n) \in \mathbb{Z}^2 \setminus (0,0)} (m+n \tau)^{-2k}$ where $k \geq 2$ (this last condition is to get absolute convergence). We note that a proper congruence subgroup $\Gamma$ may be such that the vector space of Eisenstein series is **not** just 1-dim. Also, note that if we replaced $-2k$ with a negative odd integer, terms would cancel in pairs which is why we only work with even powers. We can use $G_4,G_6$ to define the $j$-invariant for elliptic curves. It turns out that for $\Gamma = SL_2(\mathbb{Z})$, there are no cusp forms of weight $k < 12$ and hence, $\dim_\mathbb{C} M_k = 1$ for $k<12$. Since constant functions are modular forms of weight 0, it turns out that constant functions are the **only** modular forms of weight 0 by this dimension consideration.

**Example:** The $E_8$ lattice is rank 8 and hence, its theta function gives a modular form of weight 4 which means it must be a multiple of the Eisenstein series $G_8$. Since the theta function of any lattice has terms of the form $q^{(x \cdot x)/2}$, we always have $x=0$ in the lattice and hence, we have some constant terms. When the lattice is unimodular and definite, then the constant term is 1. Thus, $\theta_{E_8}(q) = \frac{1}{c_0}G_8$ where $c_0$ is the constant term of $G_8$. Amazingly, $c_0 = 2\zeta(4) = 2\sum^\infty_{n=1} \frac{1}{n^4} = \frac{\pi^4}{45}$ where $\zeta$ is the Riemann-Zeta function.
In fact, $\theta_{E_8}(q) = 1+ 240\sum^\infty_{n=1} \sigma_3(n)q^n$ where $\sigma_3(n)$ is computed by taking all the positive divisors of $n$, cubing them, and then summing. For example, $\sigma_3(2) = 1^3+2^3 = 9$.

**Example:** In the example above with $\Lambda = 2\mathbb{Z}$, we saw that the square of the theta function has coefficients that tell us the number of ways to write an integer $m$ as a sum of two squares; more generally, the coefficients of $q^{2m}$ in $\theta^k_{2\mathbb{Z}}(q)$ tell us when $m$ can be written as a sum of $k$ squares. Let $\Gamma_1(4) \subset SL_2(\mathbb{Z})$ be the subgroup of matrices congruent to $\begin{pmatrix} 1 & * \\ 0 & 1 \end{pmatrix}$ after taking mod 4. It turns out that $\theta^{2j}_{2\mathbb{Z}}$ is itself a modular form of weight $j$, level $\Gamma_1(4)$. By Riemann-Roch, one finds that for $j=1$, $M_1(\Gamma_1(4))$ is 1-dimensional so this modular form is a multiple of some Eisenstein series. In fact,
$\theta^2_{2\mathbb{Z}}(q) =1+4\sum^\infty_{m=1}(\sum_{d|m} \chi_4(d))q^{2m}$ where $\chi_4(d)=0$ when $d \equiv 0,2 \pmod{4}$, $\chi_4(d)=+1$ when $d \equiv 1 \pmod{4}$, and $\chi_4(d)=-1$ when $d \equiv 3 \pmod{4}$. In other words, the number of ordered pairs $(a,b)$ such that $a^2+b^2 = m$ is given by $4(d_1(m)-d_3(m))$ where $d_1(m)$ is the number of divisors $d$ of $m$ congruent to 1 mod 4 and $d_3(m)$ is similar but congruent to 3 mod 4. This recovers a theorem of Jacobi.
For example, $d_1(3)=d_3(3)$ and hence, 3 cannot be written as a sum of two squares. On the other hand, $d_1(5) = 2,d_3(5)=0$ and so there are 8 ordered pairs for 5.

**Corollary (originally due to Euler, after 1640):** If $p$ is an odd prime, then it can be written as a sum of two squares if and only if $p \equiv 1 \pmod{4}$.

**Corollary:** An integer $m$ can be written as the sum of two squares if and only if when writing out its prime factorization, all the primes $p \equiv 3 \pmod{4}$ have even powers.

If we let $k=2j = 4$, then we obtain a modular form where for every $m$, the coefficient for $q^{2m}$ is positive. This recovers a theorem of Lagrange:
**Theorem (Lagrange's 4 Squares Theorem, 1770):** Every positive integer can be written as a sum of four squares.

But more than that, we get a theorem of Jacobi, proved in 1834, which gives the exact number of 4-tuples $(w,x,y,z) \in \mathbb{Z}^4$ such that $m=w^2+x^2+y^2+z^2$. See this masters [thesis](https://www.universiteitleiden.nl/binaries/content/assets/science/mi/scripties/varmamaster.pdf) for more on this topic of modular forms and sums of squares.
