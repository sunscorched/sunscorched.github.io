---
title: 'Shannon Entropy'
date: 2025-12-12
permalink: /posts/2025/12/shannonentropy/
tags:
  - probability
  - entropy
---

Let's consider a discrete probability distribution. We have events indexed by $i$ with probability $p_i$ of occurring. Then $H(p)=-E[\log(p)]=-\sum_i p_i \log(p_i)$ is the **Shannon entropy** of the distribution; we can use whatever base for the logarithm. Note that since $p_i \in [0,1]$, if $p_i$ is close to 0, $-\log(p_i)$ is large. If $p_i$ is close to 1, then $\log(p_i)$ is small. If $p_i=0$, we'll define the term $p_i \log(p_i)=0$ since $\lim_{x \to 0} x\log(x) = 0$. Note that for $x \in [0,1]$, $-x\log(x) \geq 0$. Hence, for discrete probability distributions, $H(p)\geq 0$.

If every event has uniform chance of happening, then $H(p)$ is maximized. That is, we have the most entropy because there is no way to distinguish between different events using their probabilities and so there are no "interesting" patterns. For example if we're flipping a fair coin, then we can choose $\log_2$ and $H= -0.5\log_2(0.5) -0.5\log_2(0.5) = -1(-1)=1$. In this situation with a fair coin, if someone tells you that they flipped it 1000 times and that one side got 512 (but does not say if it's heads or tails), you would not really have a good guess for whether the 512 counts is for heads or tails. So from a probability standpoint, heads and tails are not really distinct. But for other values of $p$, the function has smaller value and in that case, we can pick out heads and tails. For instance, if $p=0.52$ for flipping heads, then you should guess that the 512 counts is for heads, not tails. More generally, let $p$ be the probability of flipping a heads for a possibly biased coin; let's use $\ln$. Then $H=-p\ln(p) -(1-p)\ln(1-p)$; when $p=0,1$ (so we either never or always get heads), note that $H=0$ (lowest entropy). On the other hand, $H$ is maximized when $p=0.5$. The graph of $H$ on $[0,1]$ is symmetric about the vertical line $p=0.5$.

Another view is that $-\log(p_i)$ measures how "surprising" it would be to see the event. For example, if $p_i=0.9$, then $-\log(0.9)\approx 0.0457$ which means you aren't very surprised to see event $i$ occur since it has 90% chance of happening. So then Shannon entropy is like an expected value for surprise. This sounds paradoxical but "expected value" is a mathematical notion and we just made "surprise" mean something mathematical as well. We shouldn't interpret these psychologically.

For a continuous random variable $X$ with probability density function $f(x)$, the Shannon entropy is $H(X)=E[-\log f(x)] = -\int f(x)\log(f(x))\, dx$. Unlike the discrete situation where $H(p)\geq 0$, here, the entropy can be _negative._ This is because $f(x)>1$ is allowed in which case $-f(x)\log(f(x))<0$.

**Example:** A normal distribution $N(\mu,\sigma)$ has $f(x)=\frac{1}{\sqrt{2\pi\sigma^2}}\exp(-(x-\mu)^2/2\sigma^2)$. Then by linearity of expected value,
$H=-E[\log(f)] = -E[\log((2\pi \sigma^2)^{-1/2}\exp(-(x-\mu)^2/2\sigma^2))] =\frac{1}{2}\log(2\pi\sigma^2)E[1]+\frac{1}{2\sigma^2}E[(x-\mu)^2]$.
  
Now, $E[1]=1 = \log(e)$ and $E[(x-\mu)^2]$ is the variance so this works out to be $H=\frac{1}{2}(\log(2\pi\sigma^2)+1) = \frac{1}{2} \log(2\pi e \sigma^2)$. Note that for large $\sigma$, this has large entropy and for $0<\sigma\ll 1$, the entropy is negative.

**Example:** Let's consider a distribution defined by a Dirac delta function $\delta_\mu$ which is supported at $\mu$. We might think of this as a limit of normal distributions $N(\mu,\sigma)$ with $\sigma \to 0$ and $H(\delta_\mu)=-\infty$.

However, if it's a discrete situation then $-\sum p_i \log(p_i)$ has only one term where $p_i = 1$ and the rest $p_j=0$. But $\log(1)=0$. So for Dirac delta on a discrete set, the entropy is $H=0$.

### Information Gain

Here is a related idea; it's not going to play a role later but is useful to know. Let's suppose we have some datapoints that are labeled either $Y=a$ or $Y=b$. These datapoints have a feature $X$ which takes on values 0 or 1. And now, let's suppose we have 10 datapoints, half are $a$, half are $b$. There are 4 $b$'s with $X=0$, and 5 $a$'s, 1 $b$ with $X=1$. 

In general, the **information gain** we get from studying a feature is defined as $IG(X,Y) = H(Y)-H(Y|X)$. Let's see how this works in our example. The entropy of $Y$, without considering $X$ at all is $H(Y) =-0.5\log_2(0.5)-0.5\log_2(0.5)=1$ like above. That is, from probability alone, the $a$ and $b$ are indistinguishable since they have the same count. However, once we take into account the feature $X$, we can compute $H(Y|X) = \frac{4}{10} H(X=0) +\frac{6}{10}H(X=1)$. That is, 4 out of 10 of the points have $X=0$ and 6 out of 10 have $X=1$. Looking at those with $X=0$, they are all of label $b$ which means we have perfect information about any particular point drawn from this subset: it will always be of label $b$. Hence, $H(X=0)$. On the other hand, $H(X=1) =-\frac{1}{6}\log_2(1/6)-\frac{5}{6}\log_2(5/6)\approx 0.65$. So $H(Y|X) \approx (0.66)(0.69)\approx 0.39$. Lastly, $IG(X,Y) \approx 1-0.39 = 0.61$.

So we can think of $IG$ as telling us how much information we gained once we take $X$ into account. Before, we had no way to distinguish $a$ and $b$ by, say, their counts because they have the same counts. But since all the $a$'s have $X=1$ and most $b$'s have $X=0$, then knowing the value for $X$ helps us distinguish $a$'s from $b$'s. Indeed, suppose all $a$'s have $X=1$ and all $b$'s have $X=0$. Then $H(Y|X)=0$ and the information gained is 1; the maximum amount because $X$ would perfectly distinguish the two labels.

### A Characterization of Entropy in Terms of Information Loss

This section is about a paper of the same title by John Baez, Tobias Fritz, and Tom Leinster. But the ncatLab [page](https://ncatlab.org/johnbaez/show/Entropy+as+a+functor) covers more than their paper. **Caution:** This section only applies to finite probability distributions, not continuous ones.

Let's consider a category where objects are finite sets equipped with probability measures and morphisms are measure-preserving maps. So $f:(X,p) \to (Y,q)$ is a function so that $q_j = \sum_{i \in f^{-1}(j)}p_i$. We'll call this category $\text{FinProb}$.
For example, let $(\{a,b\},p)$ be a set of two elements with $p$ being the measure that assigns $1/2$ to each. Let $q$ be the unique probability measure we can place on a single element set $\{c\}$. Then there is only one possible map $f:\{a,b\} \to \{c\}$. Indeed, $f^{-1}(c )=\{a,b\}$ and the probabilities of $a,b$ add up to 1 which is the probability of $c$.

The discrete version of Shannon entropy tells us that $H(p)=-\sum_i p_i \log(p_i)$ with the convention that $0\log(0)=0$. So here, $H(p) = \log(2)$ and $H(q)=0$. The **information loss** of $f$ is $H(p)-H(q)=\log(2)$. So we lose one bit of information. On the other hand, if we put a measure $r$ on $\{a,b\}$ which puts all the probability weight onto $a$ and none on $b$, then $H(r)=0$ and the information loss of $f$ is now 0.

Now, if we have objects $(X,p),(Y,q)$ and $\lambda \in [0,1]$, there is a measure $\lambda p \oplus (1-\lambda)q$ that we can put on the disjoint union $X \sqcup Y$ in the obvious way. If we have morphisms $f:p \to p',g:q \to q'$, we can also construct $\lambda f \oplus (1-\lambda)g$ on $X \sqcup Y$ so that the function restricts to $f$ or $g$ set-theoretically speaking. We might think of this construction as follows: we flip a coin that has probability $\lambda$ to decide whether we do one process vs. another.

Let's now assume we have a function $F$ which assigns to any such measure-preserving map $f$ a nonnegative real number $F(f)\in [0,\infty)$. We might think of morphisms $f,g$ as processes and so a composition $f\circ g$ is one process followed by another. Now, if we have a sequence $f_n:(X_n, p(n)) \to (Y_n, q(n))$ in $\text{FinProb}$, we say it **converges** to a morphism $f:(X, p) \to(Y,q)$ if:
- for all sufficiently large $n$, we have $X_n = X,Y_n = Y$, and $f_n(i)=f(i)$ for all $i \in X$;
- $p(n)\to p$ and $q(n)\to q$ pointwise.

We define $F$ to be continuous if $F(f_n) \to F(f)$ whenever $f_n$ is a sequence of morphisms converging to a morphism $f$.

We can also make a category $\mathbb{R}_+$ with a single object and morphisms are real numbers $[0,\infty)$ which compose by addition. Then a function $F$ above can be viewed as a functor if it satisfies the usual properties of functors.

**Theorem:** Suppose $F$ is any map sending morphisms in $\text{FinProb}$ to $[0,\infty)$ and that it obeys the following three axioms:
1. Functoriality: $F(f\circ g)=F(f)+F(g)$ whenever $f,g$ composable.
2. Convex Linearity:  $F(\lambda f \oplus (1-\lambda)g)=\lambda F(f)+(1-\lambda)F(g)$ for all morphisms $f,g$ and scalars $\lambda \in [0,1]$.
3. Continuity: $F$ is continuous.

Then there exists a constant $c \geq 0$ such that for any morphism $f:p \to q$ in $\text{FinProb}$, $F(f) = c(H(p)-H(q))$.

This is quite amazing: for any map $F$ satisfying the three axioms, it automatically is a scaled version of information loss where $H(p)$ is the Shannon entropy. So in this way, Shannon entropy falls out naturally. We can extend this theorem to a category of finite measures on finite sets rather than only probability measures. In that case, if we also impose homogeneity: $F(af)=aF(f)$ for all (measure preserving) morphisms $f$ and $a \in [0,\infty)$, then Shannon entropy will again appear. The proof relies on a result of Faddeev which can be reinterpreted in operadic terms. Then Shannon entropy is not a morphism of operad algebras, but only a lax morphism.

**Remark:** I don't think we need to go into it but both $\text{FinProb}$ and $\mathbb{R}\_+$ are categories where the set of objects and also sets of morphisms can be given topologies. So these are **topological categories.** Moreover, they are both symmetric monoidal. The symmetric monoidal structure on $\text{FinProb}$ is given by disjoint union and on $\mathbb{R}\_+$ it's the usual addition. Also, $[0,\infty)$ is a (topological) monoid and we can give $\text{FinProb}$ and $\mathbb{R}\_+$ the structure of $[0,\infty)$-module categories.

### Appendix: Gibbs Measure

Here is a bonus section. Let's suppose we're studying a physical system where a **finite** number of states are possible with index $i$, probabilities $p_i$, and energies of the state $E_i$. Now, suppose we want to maximize the entropy $S=-k\sum_i p_i \log(p_i)$ subjected to the following constraints:
1. Normalization of probabilities: $\sum_i p_i = 1$.
2. Fixed average energy: $\langle E \rangle =\sum_i p_i E_i$.

The first constraint is very natural for probability and the second one is natural for thermodynamics. We can solve this with Lagrange multipliers. Let 

$L=-k\sum_i p_i \log(p_i) -\alpha(\sum_i p_i -1) -\beta(\sum_i p_i E_i -\langle E \rangle)$ where $\alpha,\beta$ are Lagrange multipliers.

Taking partial derivatives and setting to zero, we have:

$\partial L/\partial p_i = -k(\log(p_i)+1)-\alpha - \beta E_i=0$.

Hence, $\log(p_i) = -\alpha/k - 1- \beta E_i/k$ and so $p_i \sim \exp(-\beta E_i)$.

We can move into the world of continuous probability distributions. The probability of the system $X$ being in state $x$ (equivalently, of the random variable $X$ having value $x$) is $P(X=x)=\frac{1}{Z(\beta)} \exp(-\beta E(x))$.

Here, $E$ is a function from the space of states to the real numbers; in physics, $E(x)$ is interpreted as the energy of the configuration $x$. The parameter $\beta$ is a free parameter; in physics, it is the inverse temperature. The normalizing constant $Z(\beta)$ is the partition function. However, in infinite systems, the total energy is no longer a finite number so additional care must be taken to deal with this.

Anyways, associated to this distribution is a **Gibbs measure** and one of the reasons why it's important is because of the Hammersley–Clifford theorem which implies that any probability measure that satisfies a Markov property is a Gibbs measure for an appropriate choice of (locally defined) energy function.

The Markov property basically says that the probability of being in some state at step $n+1$ only depends on the state immediately before it at step $n$.
