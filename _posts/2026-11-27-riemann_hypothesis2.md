---
title: 'The Riemann Hypothesis and Claude II'
date: 2026-11-27
permalink: /posts/2026/11/riemann_hypothesis2/
tags:
  - analytic number theory
  - AI
---

On November 20, 2026, two attempts to prove the Generalized Riemann Hypothesis were announced. One was by Anthropic employee Levent Alpöge, working with a frontier, non-public Claude. The announcement is accompanied by 17 million lines of Lean code but no human language preprint yet. The other, by Alessandro Masullo, is claimed to be a human-only proof and a 940 page preprint did accompany the announcement. The latter was not ready for release and the intention was for Masullo to work with number theorist Brian Conrad for a year on polishing the paper. But because of the first announcement, they decided to also make their announcement. The age of AI in math is full of drama. Despite the title of this post, I won't actually have much to say about Claude since no human language preprint has been released but it seems the [Lean code](https://leanprover-community.github.io/blog/posts/riemann-hypothesis/) does indeed run correctly.

I've written before on the Riemann Hypothesis; see [here](https://sunscorched.github.io/posts/2026/08/riemann_hypothesis/) for the definition and some properties of the Riemann zeta function. For this post, I'm really lifting a lot from what people have already written such as [here](https://johncarlosbaez.wordpress.com/2026/11/22/masullo-on-the-riemann-hypothesis/#comment-228187).

## Quick History

Let $\pi(x)$ be the prime counting function which tells you how many primes are less than or equal to a real number $x$. We'll typically be interested in $x$ being an integer since that's where the function could jump.

As a teenager, perhaps around 1792, Gauss proposed that for large $x$, $\pi(x) \approx \dfrac{x}{\ln x}$. Later, circa 1849 in a letter, he improved his proposal to $\pi(x) \approx \text{Li}(x)$ where $\text{Li}(x)= \int^x_2\frac{dt}{\ln t}$, the logarithmic integral. 

It has since been shown that indeed, $\pi(x)$ is approximately $\text{Li}(x)$ with some error terms for large $x$. This is called the [prime number theorem](https://mathworld.wolfram.com/PrimeNumberTheorem.html) and it tells us that the error on $|\pi(x) - \text{Li}(x)|$ is at most, on the order of $O(x \exp(-c\sqrt{\ln x}))$. Since $\exp(\ln x) = x$, $\exp(\sqrt{\ln x})< x$. Then $\exp(c\sqrt{\ln{x}})= \exp(\sqrt{\ln x})^c< x^c$. But with $-c$, we have $\exp(-c\sqrt{\ln x}) = \exp(\sqrt{\ln x})^{-c}> x^{-c}$ and lastly, $x \exp(-c\sqrt{\ln x})>x^{1-c}$. This $c$ is not fixed as we can trade it for whatever constants come along with the big $O$.

As it stands, the prime number theorem is equivalent to the fact that the nontrivial zeros of the Riemann-zeta function $\zeta(s)$ have real part $0 <\text{Re}(s) < 1$. There are various ways one might hope to improve our estimates of the errors between $\pi(x)$ and $\text{Li}(x)$ and many of these ways are equivalent to something about the zeros of $\zeta$. The strongest statement is the Riemann Hypothesis which says that all the nontrivial zeros have real part equal to $1/2$. Koch (1901) showed that if the Riemann Hypothesis is true, we have an improved error term: $\pi(x) = \text{Li}(x) + O(\sqrt{x}\ln x)$. If we take the ratio of the previous error term with this one, we have
$$\dfrac{\sqrt{x}\ln x}{x \exp(-c\sqrt{\ln x})} = \dfrac{\ln x}{\sqrt{x}}\exp(c\sqrt{\ln x})$$
Let $u=\sqrt{\ln x}$ which means $\sqrt{x}=\exp(\frac{1}{2}u^2)$. The RHS can be written as $u^2\exp(-\frac{1}{2}u^2 +cu)$. The quadratic term makes the whole thing limit to 0 as $u \to \infty$.

Later, Schoenfeld (1976) showed that the Riemann Hypothesis is equivalent to $|\pi(x)-\text{Li}| <\frac{1}{8\pi }\sqrt{x}\ln x$ for all $x \geq 2657$. Put another way, the Riemann hypothesis is equivalent: $|\pi(x)-\text{Li}(x)| \leq C x^p$ for any $p > 1/2$, and some $C$ that depends on $p$. We already know we can't get $p$ all the way down to $1/2$.

What are some intermediate steps towards bounding the errors? Back in September 2026, OpenAI announced a proof of the quasi-Riemann Hypothesis which says that all the nontrivial zeros of the Riemann zeta function lie in the strip $a \leq \text{Re}(s) \leq 1-a$ for some $0 < a < 1/2$. Of course, if $a=1/2$, that is the full Riemann Hypothesis. The QRH is equivalent to $|\pi(x)-\text{Li}(x)| \leq C x^p$ for any $p> 1-a$ and $C$ that depends on $p$.

OpenAI's proof is being reviewed but prior to its announcement we've not been able to assert that the zeros live in a narrower strip; i.e. we had not ruled out the possibility of the real parts of the zeros $\rho$ converging towards the line $\text{Re}(s)=1$ as $\text{Im}(\rho) \to +\infty$

## Relation to Primes

I've been asserting that nontrivial zeros of $\zeta$ are related to the distribution of primes but how do we see this more precisely? Since $\dfrac{d}{ds} \ln f(s) = \dfrac{f'(s)}{f(s)}$, we call the RHS the logarithmic derivative of a function. Let $\Lambda(n)$ be the function which equals $\ln p$ when $n$ is a power of a prime $p$ and 0 otherwise. This $\Lambda$ is a bit unwieldly because it jumps up and down. For example, $\Lambda(25)> \Lambda(27)$. So to get a monotonically increasing function, we can use the Chebyshev function $\psi(x) = \sum_{n \leq x}\Lambda(n)$.

In the previous post on the Riemann Hypothesis, we showed how $\zeta$ relates to this function, namely via the logarithmic derivative:

$-\dfrac{\zeta'(s)}{\zeta(s)}=\sum^\infty_{n=1}\dfrac{\Lambda(n)}{n^s}$.

But the sum is really over only powers of primes. The LHS has simple poles at the zeros of $\zeta$ and by Weierstrass Factorization, we can express the LHS in terms of the zeros of $\zeta$. In particular, denote the nontrivial zeros of $\zeta$ with $\rho$:

$-\dfrac{\zeta'(s)}{\zeta(s)} = \dfrac{1}{s-1}-\sum_\rho \dfrac{1}{s-\rho}+\text{other stuff}$

If instead we use the Chebyshev function, we have:

$\psi(x) = x-\sum_\rho \frac{x^\rho}{\rho} -\ln 2\pi-\frac{1}{2}\ln (1-x^{-2})$

If we assume the Riemann Hypothesis, then the $\rho = \dfrac{1}{2}\pm i\gamma$. Introducing and then expanding exponentials gives some sines and cosines. We find that $\psi(x) \approx x- 2\sqrt{x}\sum_{\gamma > 0} \dfrac{\sin(\gamma \ln x)}{\gamma}-\ln(2\pi)$ if the Riemann Hypothesis is true. This shows us the amplitude and frequency of the "waves" contributed by the nontrivial zeros.

## The Generalized Riemann Hypothesis

A **Dirichlet character** of period $N$ is a function on integers $\chi:\mathbb{Z} \to \mathbb{C}$ which satisfies:
1. $\chi(mn)=\chi(m)\chi(n)$ for all $m,n$ and vanishes on numbers that share a factor with $N$.
2. $\chi(m)=0$ if and only if $\gcd(m,N)>1$.
3. $\chi(m+N)=\chi(m)$ for all $m$; i.e. $\chi$ is periodic with period $N$

Note that $\chi(1)=\chi(\pm 1)^2$ so $\chi(1)=1$ while $\chi(-1)$ could be $-1$ or $+1$. Also, $\gcd(0,N)=N$ so $\chi(0)=0$. A simple example is the constant character $\chi \equiv 1$. Another is:

$\chi_0(m) = \begin{cases} 0, & \gcd(m,N) > 1 \\ 1, & \gcd(m,N)=1\end{cases}$

If $\phi$ is the Euler totient function, recall that $x^{\phi(N)} \equiv 1 \pmod{N}$ when $\gcd(x,N)=1$. Let $m$ be such that $\gcd(m,N) = 1$. So $\chi(m)^{\phi(N)}=\chi(m^{\phi(N)})=\chi(1) = 1$ which means $\chi(m)$ must be a root of unity.

Indeed, if we have a group homomorphism $(\mathbb{Z}/N)^\times \to \mathbb{C}$, we can lift this to integers coprime to $N$ and extending by 0 to those sharing a factor with $N$.

**Example:** $N=7$, $\phi(7)=6$. Let $\omega = e^{2\pi i/3}$ and set $\chi(2)=\omega$. This means $\chi(4)=\omega^2$ and $\chi(8)=1$. Since $2^3 \equiv 1 \pmod{7}$, this obeys the group structure of $(\mathbb{Z}/7)^\times \cong \mathbb{Z}/6$. Also, $3 \equiv -2^2\pmod{7}$ so $\chi(3)=\chi(-1)\chi(2)^2 = \chi(-1)\omega^2$ and $5 \equiv -2 \pmod{7}$ so $\chi(5)=\chi(-1)\omega$. We can thus decide whether $\chi(-1)=\pm 1$ and either choice gives a valid Dirichlet character.

Anyways, we can define a function $L(s,\chi)=\sum^\infty_{n=1}\frac{\chi(s)}{n^s}$ where $\chi$ is a Dirichlet character and $\text{Re}\, s > 1$. We can analytically extend these functions to the entire plane. We call these **Dirichlet L-functions.** For example, when the real part is great than 1, the trivial character of period $N$ gives rise to $L(s,\chi_0) = \sum_{\gcd(n,N)=1}n^{-s} = \prod_{p\nmid N} (1-p^{-s})^{-1}$.

These Dirichlet L-functions were used to prove that given $a,n$ which are relatively prime, there are infinitely many primes $p \equiv a \pmod{n}$.

Anyways, the generalized Riemann Hypothesis is pretty similar to the standard one: for any Dirichlet L-function $L(s,\chi)$, there are nontrivial zeros and they all have real part equal to $1/2$.

There are many nice corollaries to this. For example, Hardy and Littlewood showed it implies that primes equal to 3 mod 4 are more common than primes 1 mod 4. They also showed it implies every odd number > 5 is a sum of three primes.

## Masullo's Methods

Masullo's approach is to prove an even broader conjecture for L-functions coming from Hecke characters which arise from algebraic number fields. To prove the GRH in this setting, Masullo claims a new formula for the logarithmic derivative that is supposed to work up to the $1/2$ line.

The formula is a so-called trace formula involving the spectrum of an operator. For operators on infinite-dimensional spaces, many are defined via integrating a distribution called a kernel $k(x,y)$. The trace is the integral of $k(x,y)$ over the diagonal; i.e. when $x=y$. The [Selberg trace formula](https://en.wikipedia.org/wiki/Selberg_trace_formula) is one such example. It's a formula for the character of the [unitary representation](https://en.wikipedia.org/wiki/Unitary_representation "Unitary representation") of a Lie group $G$ on the space $L^2(G/\Gamma)$ where $\Gamma$ is a discrete group. The character is given by the trace of certain functions on $G$. For example, $\Gamma$ could be the fundamental group of a Riemann surface, in which case the formula relates the spectrum of the Laplacian on the surface to the lengths of closed geodesics. Curiously, there are similarities in behavior between closed geodesics and primes.

In 1952, André Weil formulated an explicit formula and showed that the generalized Riemann Hypothesis is equivalent to a certain functional, built from the explicit formula, being positive. This is called [Weil’s positivity criterion](https://en.wikipedia.org/wiki/Weil's_criterion). In the late 1990s, Alain Connes found an operator on a space built from the adeles of a number field whose trace formula is the explicit formula of Weil.

What Masullo did is work on a different space with a different operator though there are important threads between his work and Weil and Connes' work. He produces a formula with a spectral side and a geometric side. But importantly, he claims that he does not need the positivity criterion.

Up till this point, there isn't anything novel yet since the identity is known as well as the general strategy: realize the zeros as the spectrum of an operator, realize the primes as the "closed orbits" on the other side of a trace formula, and establish the GRH via this formula.

But Masullo's way of computing the geometric side gives an expression that is supposed to stay bounded, and hence holomorphic, in a region where the naive sum over primes diverges. Specifically, it is supposed to stay holomorphic everywhere to the right of the $1/2$ line. An equation relating $L(s,\chi)$ and $L(1-x,\bar{\chi})$ rules out zeros to the left of the $1/2$ line. So all nontrivial zeros would lie on the $1/2$ line.

To summarize, there are two main steps. First, producing the trace formula with Masullo's new computation of the geometric side: this is the majority of the 940 pages. Second, showing the geometric side really stays under control as we limit towards a critical boundary. After posting, there's already been feedback suggesting there are gaps or issues with the preprint. Despite that, it can still be instructive to understand where the shortcomings are if they really are shortcomings.

## Appendix: $\pi(x)-\text{Li}(x)$ changes sign infinitely many often

For all $x$ where we can actually determine $\pi(x)$, $\pi(x)<\text{Li}(x)$. But in 1914, Littlewood proved that $\pi(x)-\text{Li}(x)$ changes sign infinitely many time but did he did not determine the first time it occurs. He gave this as a problem to his student Stanley Skewes to determine. In 1933, Skewes gave an enormous upper bound on the first occurence where $\pi(x)> \text{Li}(x)$, assuming the Riemann Hypothesis. The number is enormous and approximately: raise 10 to the 10 to the 10 to the 34. Later in 1955, without assuming RH, he gave an even larger upper bound: replace 34 with 964. Let $\Xi$ be the first occurence of when $\pi(x) > \text{Li}(x)$. To my knowledge, the best upper bound on $\Xi$ is $1.397162914 \times 10^{316}$ and the best lower bounds are around $10^{19}$.
