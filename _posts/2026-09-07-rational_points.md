---
title: 'Rational Points on Circles'
date: 2026-09-07
permalink: /posts/2026/09/rational_points/
tags:
  - number theory
---

Let's consider the unit circle $x^2+y^2=1$ defined over $\mathbb{R}$. A **rational point** is $(x,y)\in \mathbb{R}^2$ where $x,y \in \mathbb{Q}$. Examples of rational points on the unit circle are $(\frac{7}{25},\frac{24}{25})$ or $(\frac{8}{17},\frac{15}{17})$. Indeed, we can write these with a common denominator so that a rational point on the circle is of the form $(\frac{a}{c},\frac{b}{c})$ and we see that the integers $a,b,c$ must satisfy the Pythagorean identity $a^2+b^2=c^2$.

Note that once we have a rational point $(x_0,y_0)$ on the unit circle, we can find a lot more. Let $t \in \mathbb{Q}$ be the slope for a line that passes through $(x_0,y_0)$; it can be represented as $y-y_0 = t(x-x_0)$ or $y=tx+ y_0-tx_0$. Then the line intersects the circle in two distinct points (unless it is tangent, in which case, it intersects with multiplicity 2). To find the points, substitute into the equation of the unit circle to get:
$x^2 + (tx+ y_0-tx_0)^2 = 1$. After rearranging, we'll have a quadratic equation of the form $Ax^2+Bx+C = 0$ where $A,B,C \in \mathbb{Q}$. The quadratic formula tells us that the solutions $x_0, x_1$ must sum to $x_0+x_1 = -B/A$ which is rational. Since $x_0$ is rational, then $x_1$ must be as well and hence, $y_1$ must be as well. This argument works for any nondegenerate conic. Therefore, we get the following dichotomy.

**Propostion:** There are either zero or infinitely many rational points on a nondegenerate conic.

The next question one might ask is, for which $d \in \mathbb{N}$ are there rational solutions to $x^2+y^2=d$? For $d=1,2$, we can easily find integer points and hence, get infinitely many rational points.

Modular arithmetic gets us infinitely many examples of circles with zero rational points. Let's suppose $d\equiv 3 \pmod{4}$. Then writing $x=a/c,y=b/c$ and assuming there is no common divisor for all three $a,b,c$ other than 1, we see the problem is now about studying $a^2+b^2 \equiv 3 c^2 \pmod{4}$. For squares, we know that they have to be equal to 0 or 1 modulo 4; it's not possible for them to equal 2 or 3 mod 4. We see that $c^2 \equiv 1 \pmod{4}$ cannot happen since $a^2+b^2 \equiv 0,1,2 \pmod{4}$. So then $c^2 \equiv 0\pmod{4}$ which means that $a^2+b^2$ must be 0 mod 4; so either $a^2$ and $b^2$ are both 2 mod 4 (which can't happen) or both 0 mod 4. This last case is what remains for us and so we conclude that $a^2,b^2,c^2$ are all equal to 0 mod 4 which implies $a,b,c$ are all even. But that means they all have 2 as a divisor which contradicts our original assumption. To summarize what we've learned so far:

**Proposition:** For circles defined by $x^2+y^2=d$, if $d \equiv 3 \pmod{4}$, there are no rational points. For the $d$ in which there exists one rational point, then there are in fact infinitely many rational points.

## Gaussian Integers $\mathbb{Z}[i]$

We want to strengthen the above proposition and we'll do so by visiting the Gaussian integers $\mathbb{Z}[i]$ which are of the form $a+bi$ where $a,b \in \mathbb{Z}$ and $i^2 = -1$. This ring has a (squared) norm $N(a+bi)=a^2+b^2$ and it is multiplicative; i.e. $N(xy)=N(x)N(y)$.

If $p$ is prime in $\mathbb{Z}$; i.e. cannot factor nontrivially, it isn't necessarily prime in $\mathbb{Z}[i]$. For example, $5 = (1+2i)(1-2i)$. Indeed, let $p \equiv 1 \pmod{4}$ and let $G= (\mathbb{Z}/p)^\times$ be the multiplicative group of elements coprime to $p$ (which are all integers less than $p$). This group has order $p-1 = 4k+1-1 = 4k$.

**Lemma:** For any finite field $F = \mathbb{F}_q$ where $q=p^n$, the multiplicative group of units is a cyclic group.

**Proof:** Finite fields of characteristic $p$ are isomorphic to something of the form $\mathbb{F}\_p[x]/(a(x))$ where $a(x)$ is some irreducible polynomial. Denote  the order of $G=F^\times$ by $N$. The number of elements that satisfy $x^d -1$ is at most $d$; i.e. there are at most $d$ roots. This means there are at most $d$ elements whose order is some number dividing $d$.
Now the fundamental theorem for finitely generated abelian groups is that they take on the form $\mathbb{Z}^r \oplus \mathbb{Z}/n_1 \oplus ...\oplus \mathbb{Z}/n_k$ where we have a free part and torsion part. The torsion parts are direct sums of cyclic groups and can be arranged so that each $n_i$ divides $n_{i+1}$. So to write it another way, $n_1 | n_2 |...|n_k$. In our sitation, $G$ is finite so $r=0$ and the number of roots of $x^{n_k}-1$ is the product $n_1n_2...n_k \leq n_k$. So this forces $n_1=n_2=...=n_{k-1}=1$. That is, $G=\mathbb{Z}/n_k$ is cyclic. $\square$

Since $G = \mathbb{F}_p^\times$ is a cyclic group, pick a generator $g$. Let $x=g^k$ and note that $x^4 = g^{4k}=1$ in $G$. In a field, the solutions to $y^2=1$ have only two solutions $\pm 1$ so $x^2=-1$ since it can't equal $+1$ in $G$. Note that if $p=4k+3$, then this argument fails as the order of $G$ is $4k+2$ and there can't exist $x$ such that $x^4 = 1$ because Lagrange's theorem guarantees that the order of subgroups must divide the order of the group.

So when $p \equiv 1 \pmod{4}$, we know there exists $x \in \mathbb{Z}$ such that $x^2 \equiv -1 \pmod{p}$ which means $p$ divides $x^2+1$. In $\mathbb{Z}[i]$, this factors as $(x-i)(x+i)$. If $p$ were prime in $\mathbb{Z}[i]$ as well, then it must divide either $x+i$ or $x-i$. Suppose it's the former; so there is $a+bi$ such that $p(a+bi)=x+i$ which means $pb = 1$ when comparing real and imaginary parts. But there are no solutions to $pb=1$ when $p$ is prime in the integers. A similar argument shows $p$ doesn't divide $x-i$ either. So $p$ is not prime in $\mathbb{Z}[i]$ and hence, must itself factor.

If instead $p\equiv 3 \pmod{4}$, could it factor in $\mathbb{Z}[i]$? Suppose it could; i.e. $p= \alpha \beta$. Then using the (squared) norm $N$, we have $N(p) = N(\alpha)N(\beta)$ which means $p^2 =(a^2+b^2)(c^2+d^2)$ for some constants. The divisors of $p^2$ are $1,p,p^2$. For the factors $\alpha,\beta$ to not be trivial (not be units in $\mathbb{Z}[i]$), we must have that $N(\alpha)=N(\beta)=p$. So this means $p=a^2+b^2$ which, modulo 4 means $a^2+b^2 \equiv 3 \pmod{4}$. But above, we already argued why this can't happen. Thus, a prime $p \equiv 3 \pmod{4}$ in $\mathbb{Z}$ remains a prime in $\mathbb{Z}[i]$.

Let's go back to the question of which $d \in \mathbb{N}$ are such that we have rational solutions to $x^2+y^2=d$. In the context of $\mathbb{Z}[i]$, we want to find $x+yi$ so that its norm is $d$. If $d$ contains a prime factor $p \equiv 3 \pmod{4}$, then we can write $d=p^kq$ here $q$ are the other factors and $k$ is a power.

So then $p$ must divide the product $(x+yi)(x-yi)$. Because $p$ is a prime in $\mathbb{Z}[i]$, if $p$ divides a product, **it must divide one of the factors** (that's what it means to be prime). If $p$ divides $x+yi$, then $p$ must divide both $x$ and $y$ and hence, also $x-yi$. So then, if $x+yi$ is divisible by $p^\ell$ for some $\ell$, then $x^2+y^2$ must be divisible by $p^{2\ell}$. 

To summarize, if we want solutions to $x^2+y^2=d$ and we have that $p \equiv 3 \pmod{4}$ is a prime factor of $d$, this forces there to be an even number of $p$ factors in $d$.

To move to rational solutions of $x^2+y^2=d$, if $x=a/c, y=b/c$, then $a^2+b^2=dc^2$. Now, a **valuation** $v_p$ counts the number of time $p$ divides a number. Clearly, $v_p(ac)=v_p(a)+v_p(c)$. For rational values, we can extend via $v_p(a/c)=v_p(a)-v_p(c)$. So applying it to the equation above, we have:
$v_p(a^2+b^2) = v_p(d)+v_p(c^2)$.

The left hand side is even as we argued and if $p$ divides $c^2$, it must divide $c$ itself. So $v_p(c^2)$ is also even. Hence, $v_p(d)$ must be even. In conclusion:

**Proposition:** If there are rational solutions to $x^2+y^2=d$, then for every prime factor $p \equiv 3 \pmod{4}$, it must divide $d$ an even number of times.

The converse is also true: Let $d = p_1^{2k_1}...p_j^{2k_j} d'$ where all the $p_1,...,p_j$ are 3 mod 4 and $d'$ contains only primes congruent to 1 mod 4 or is equivalently, 2. Take all the squares out of $d'$ so that we write $d = k^2q$ where $q$ is square-free and only contains prime factors 2 or those congruent to 1 mod 4.

All primes $p \equiv 1 \pmod{4}$ can be written as a sum of two squares; this is by [Fermat's theorem](https://en.wikipedia.org/wiki/Fermat%27s_theorem_on_sums_of_two_squares#). Observe that the product of sums of 2 squares are themselves the sum of two squares: $(u^2+v^2)(g^2+h^2)=(ug-vh)^2+(uh+vg)^2$. This means that we can write all the prime factors of $q$ as sums of 2 squares and conclude in the end that $q$ itself is also a sum of two squares. Thus, $d=k^2q = k^2(A^2+B^2) = (kA)^2 + (kB)^2$ which is an explicit integer (and hence, rational) solution. So we now write the final form:

**Proposition:** There exists a rational solutions to $x^2+y^2=d$ if and only if for every prime factor $p \equiv 3 \pmod{4}$, $p$ divides $d$ an even number of times. When there exists a rational solution, then there are infinitely many.

As a closing remark, let's increase the degree of the polynomial defining the curve to obtain an elliptic curve defined over $\mathbb{Q}$; i.e. a curve whose defining equation is $y^2=x^3 + Ax+B$ with rational coefficients. It is always possible to get the equation into such a Weierstrass form if we work over a field of characteristic not equal to 2 or 3. The Mordell-Weil theorem says that the set of rational points of the curve form a finitely-generated abelian group. The group law is defined geometrically with rational lines and since it's finitely-generated and abelian, this means it has a free part and a torsion part. 

There is a way to define a height for elliptic curves and for a given finite height, you can count the density of curves of rank $k$. Then let the height go to infinitely and see if there is convergence. It turns out that the asymptotic density for rank 0 and rank 1 elliptic curves are both $1/2$. So unlike the case of conics which, if there is even one rational point, there are in fact infinitely many, for elliptic curves, there can be finitely many. Also, the rational points of elliptic curves of higher rank are exceedinly rare. Some people conjecture that there is a bound on the highest rank. The current record (29 August, 2026) for highest rank is 31 and was discovered by Levent Alpöge and Ava Howell using Anthropic's Claude model.
