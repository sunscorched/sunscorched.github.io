---
title: 'The Entropic Central Limit Theorem and Berry-Esseen Theorem'
date: 2025-12-02
permalink: /posts/2025/12/entropicclt/
tags:
  - probability
  - entropy
---
In this post, I'll revisit the Central Limit Theorem again, this time with a focus on entropy. I'll state a few results at the end without proof including the Berry-Esseen Theorem which tells us about the convergence of the usual Central Limit Theorem. We'll work with continuous random variables and their density functions. Recall that for a random variable $X:(\Omega,\mu) \to \mathbb{R}$ with density $f$, the entropy is defined as $H[f] = -\int_\Omega f(x) \ln f(x)\,d\mu$. We'll just work with $\Omega = \mathbb{R}$ and the usual Lebesgue measure.

## Entropy Fundamentals

**Proposition:** Entropy is a concave functional.

Note that the function $x \ln x$ is concave up on $(0,\infty)$ which may suggest to us that the functional $H[f] = -\int_\mathbb{R} f(x) \ln f(x) \, dx$ is concave. We'll use calculus of variations to check. I'll just give the definition below and the reader may verify the calculation; we'll assume the derivative operators commute with integration.

$$\delta^2 H[f] = \left. \dfrac{d^2}{d\epsilon^2} H[f+\epsilon h] \right|_{\epsilon=0} = -\int \dfrac{h(x)^2}{f(x)}\, dx \leq 0.$$

So the functional is concave and hence, when restricted to a convex set, if there is a local maximum, it will be a unique global maximum. 

Let's figure out what our convex set is and find a local maximum. Let's work with continuous random variables with mean 0 for simplicity and variance $\sigma^2$. So if such a random variable has PDF $f$, then $\int f(x)\, dx = 1, \int x f(x)\,dx = 0, \int x^2 f(x)\, dx = \sigma^2$. If $f,g$ satisfy these conditions, then it's easy to check that so does $tf + (1-t)g$ for $t \in [0,1]$. So The set of all such continuous random variables is a convex set.

Next, we form the following Lagrangian; we'll be using Lagrange multipliers to deal with optimization given some constraints.

$$\mathcal{L}[f] = H[f] -\lambda_0\left(\int f(x) \, dx -1\right) - \lambda_1 \left(\int x f(x)\, dx\right) - \lambda_2\left(\int x^2 f(x) \, dx - \sigma^2 \right)$$

Next, we vary using $f+\epsilon h$ where the 0th, 1st, and 2nd moments of $h$ are all 0 so that $f+\epsilon h$ stays in the set. We find that

$$\delta \mathcal{L}[f](h) = \left.\dfrac{d}{d\epsilon}\right|_{\epsilon=0} \mathcal{L}[f+\epsilon h] = -\int (\ln f +1)h\,dx -\lambda_0\int h\, dx - \lambda_1 \int x h\,dx -\lambda_2 \int x^2 h\, dx.$$

For this to equal 0 for all the admissible $h$, we need $\ln f +1 +\lambda_0 + \lambda_1 x + \lambda_2 x^2 = 0$. For convenience, let's right that we need $ln f(x) = A + Bx + Cx^2$ or $f(x) = e^A e^{Bx} e^{Cx^2}$. Since the mean should be 0, we see that if $B \neq 0$, this would off-center the PDF to not have mean 0. So it must be that $B=0$. For the function to be integrable, we need $C<0$ and in fact, should be $-\dfrac{1}{2\sigma^2}$ so that we get the correct variance. And we'll find that $e^A = \dfrac{1}{\sqrt{2\pi}\sigma}$. In other words, $f$ is the PDF for the normal distribution with mean 0 and variance $\sigma^2$.

Putting things together, we have found the normal distribution $N(0,\sigma^2)$ to be a local maximum for entropy for a given variance and mean 0. Since entropy is concave on the relevant convex set, we know that $N(0,\sigma^2)$ is a global maximum. One can compute this entropy to be $\dfrac{1}{2}(1 + \ln(2\pi \sigma^2)$. Note that for small $\sigma$, the entropy is actually negative so $H$ takes values on all of $\mathbb{R}$. This is different from the entropy of discrete random variables who have entropy bounded below by 0.

**Proposition:** Let $X,Y$ be two independent random variables with densities $p,q$. It is well known the density of $X+Y$ is the convolution $p\*q$. Moreover, $H[p\*q]\geq \max(H[p],H[q])$.

**Proof:** We noted that $\phi(x) = x \ln x$ is a convex function (so $-\phi(x)$ is concave). Jensen's inequality tells us that for any random variable $Z$ and any convex function $\phi$, $\phi(E[Z]) \leq E[\phi(Z)]$.

Now, $(p\*q)(x) = \int p(x-y)q(y)\, dy = E_Y[p(\*-y)]$ can be expressed as expectation of something. We can think of $Z=p(\*-y)$ as a random variable. So by Jensen's inequality, $\phi(E_Y[p(\*-y)]) \leq E_Y[\phi(p(\*-y))]$.

If we integrate both sides with respect to $x$, the left hand side is $\int \phi(p\*q)(x)\, dx = -H[p\*q]$.

The right hand side unpacked is $\int \int \phi(p(x-y))q(y)\, dy \, dx$. By Fubini, we can switch the order of integration to integrate with respect to $x$ firt. Since $q(y)$ doesn't depend on $x$, we can move that out of the inner integral:
$$\int q(y) \int \phi(p(x-y))\, dx \, dy.$$

Using the substituion $u=x-y, du=dx$, the inner integral is just $\int \phi(p(u))\, du = -H[p]$ which is just a number. So the RHS equals $-H[p]\int q(y)\, dy$. Since $q$ is a density, then $\int q(y)\,dy =1$ so we have at the end $-H[p\*q] \leq -H[p]$ and so $H[p\*q] \geq H[p]$. The same argument also shows $H[p\*q] \geq H[q]$ and hence $H[p\*q]\geq \max(H[p],H[q])$. $\square$

## Entropic Central Limit Theorem

Let $X_1,...,X_n$ be iid continuous random variables with mean $\mu$, variance $\sigma^2$ and $S_n = \sum^n X_i$. Let $Y_n = (S_n - n\mu)/\sigma\sqrt{n}$. Then we can check that the mean of $Y_n$ is 0 and the variance is 1.

We'd like to show that $H[Y_n] \leq H[Y_{n+1}]$ where equality holds if and only if the $X_i$ are normal distributions. Also, we know $H[Y_n] \leq H[N(0,1)]$. If we can show this, then we know that monotonically increasing sequences bounded above must converge to some $L \leq H[N(0,1)]$. If we can then show that $L$ is in fact equal to this number, we'll have proven a kind of entropic Central Limit Theorem. This should require more machinery because I think this is a stronger type of convergence than the usual CLT which is about convergence in distribution. There is a 1986 [paper](https://projecteuclid.org/journalArticle/Download?urlId=10.1214%2Faop%2F1176992632) with this a result along these lines.

**Definition:** Let $D(f,\phi) = \int f \log(f/\phi)$ be **relative entropy** where $\phi$ is the standard normal distribution's density and the mean of $f$ is 0 while the variance of $f$ is 1.

Observe $D(f,\phi) = \int f \log f - \int f \log \phi = -H[f] - \int f \log(\phi)$. Since $\phi = \frac{1}{\sqrt{2\pi}} \exp(-x^2/2)$, log of this is $-\frac{1}{2}(\log(2\pi) - x^2)$. Plugging this in, the integral $-\int f \log(\phi)$ is then $\frac{1}{2}(\log(2\pi) -\int x^2 f)$. But the integral $\int x^2 f$ is the variance which is 1. So all told, $D(f,\phi) = H[\phi] - H[f]$, the difference in entropies.

**Theorem:** Let $f_n$ be the density for $Y_n$ as defined earlier. Then $D(f_n,\phi) \to 0$ which means $\lim_{n \to \infty} H[f_n] = H[\phi]$ if and only if $H[f_n]$ is finite for some $n$.

## Berry–Esseen Theorem

Above, we see that we have #$L^1$ convergence when we assume finite entropy for at least one standardized average. In a similar vein, if we assume finite 3rd absolute moment, we can also arrive at a theorem about the rate of convergence in the Central Limit Theorem.

**Theorem (Berry, Esseen):** Let $X_1, X_2, ...$ be i.i.d. random variables with $E[X_i] = 0, E[X_i^2] = \sigma^2 > 0$, and $E[\|X_i\|^3] = \rho < \infty$. Define $Y_n=\frac{1}{n}(X_1+X_2+...+X_n)$ to be the sample mean, with $F_n$ the cumulative distribution function of $\dfrac{Y_n\sqrt {n}}{\sigma}$ and $\Phi$ the cumulative distribution function of the standard normal distribution. There exists a universal $C>0$ such that for all $x$ and $n$, $\|F_n(x)-\Phi(x)\|\leq \dfrac{C\rho}{\sigma^3\sqrt{n}}$.

**Remark:** So the rate of convergence is $O(n^{-1/2})$. More interestingly, the constant $C>0$ works for **any** random variable with finite 3rd absolute moment and some progress has shown that $C < 0.4748$.
