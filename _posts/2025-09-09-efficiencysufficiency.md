---
title: 'Efficiency and Sufficiency'
date: 2025-09-09
permalink: /posts/2025/09/efficiencysufficiency/
tags:
  - probability
  - statistics
---

Recall that the mean squared error for an estimator $\hat{\theta}$ for a population parameter $\theta$ is simply $\text{MSE}(\hat{\theta}) = E[(\hat{\theta}-\theta)^2]$ and we can decompose this into $\text{MSE}(\hat{\theta}) = \text{Var}(\hat{\theta})+\text{Bias}(\hat{\theta})^2$ where $\text{Var}(\hat{\theta}) = E[\hat{\theta}^2]-E[\hat{\theta}]^2$ and $\text{Bias}(\hat{\theta}) = E[\hat{\theta}] - \theta$. This works because $E[\theta]$ and $E[\theta^2]$ are just (unknown) numbers. If the estimator is unbiased, then this bias term is 0 and the mean squared error is simply the variance. In a variety of situations, a biased estimator can be made unbiased simply by scalar multiplication by a well-chosen factor.

### Efficiency

Suppose we have two **unbiased** estimators $\hat{\theta}_1,\hat{\theta}_2$. Then the **ratio** of their MSE is just a ratio of their variances and we call this the **efficiency** $\text{eff}(\hat{\theta}_1,\hat{\theta}_2) = \dfrac{\text{Var}(\hat{\theta}_2)}{\text{Var}(\hat{\theta}_1)}$ (note that $\hat{\theta}_2$ is on top). If this efficiency is larger than 1, then that means the variance of $\hat{\theta}_2$ is bigger and we'd prefer to use $\hat{\theta}_1$ as an estimator.

**Question:** Why do we call this "efficiency?
**Answer:** Often, the variance depends on the number of samples $n$ that we have and so the variances are of the form $C_i/n$ for $i=1,2$. If $C_2>C_1$, this means that we'd need a larger number of samples if we wanted to decrease the variance of $\hat{\theta}_2$. In that sense, $\hat{\theta}_1$ is more efficient than $\hat{\theta}_2$ because it needs fewer samples to obtain some threshold on the size of variance.

**Example:** Let $\theta$ be the angle at which electrons are emitted in muon decay. It has a probability distribution with PDF being $f(x|\alpha) = (1+\alpha x)/2$ where $x = \cos \theta \in [-1,1]$ and $\alpha \in [-1,1]$ as well. This $\alpha$ is unknown to us but we'd like to predict it. The expected value is then: $\frac{1}{2}\int^1_{-1}x(1+\alpha x)\, dx = \alpha/3$. A quick trick is to spot that the odd functions have integral equal to 0 on intervals that are symmetric across $x=0$. Also, the 2nd moment is $E[X^2] = \frac{1}{2}\int^1_{-1} x^2(1+\alpha x)\, dx = 1/3$. Hence, the variance is $\frac{1}{3}-\frac{\alpha^2}{9}$. 

Our first integral gives us a method-of-moments estimate on $\alpha$: $\hat{\alpha}_{MOM} = 3E[X] = 3\bar{X}$. Then, Churchill writes that the variance is $\text{Var}(\hat{\alpha}_{MOM}) = 9\text{Var}(\bar{X}) = \frac{9}{n}\text{Var}(X) = \frac{3-\alpha^2}{n}$.

**Remark:** We know that $E[\bar{X}] = E[X]$ and if $\bar{X}$ is a specific average we computed from specific observations of muon decay, then $\text{Var}(\bar{X})=0$. But if we treat $\bar{X}$ as its own random variable, then $\text{Var}(\bar{X}) = \frac{1}{n}\text{Var}(X)$. To see why, since $\bar{X}=\frac{1}{n}(X_1+...+X_n)$ where the $X_i$ are all iid. So $\text{Var}(\bar{X}) = \frac{1}{n^2}\text{Var}(X_1+...+X_n)$. Writing things out fully, we'll have that the variance of this sum is $\sum^n_{i=1}E[X^2_i] + 2\sum_{i<j}E[X_i X_j] -(E[X_1]+...+E[X_n])^2$. Now, $E[X_i]=E[X]$ for all $i$ since these are iid. Also, $E[X_iX_j] = \text{Cov}(X_i,X_j) + E[X_i]E[X_j]$. But being independent, the covariance is 0 and we just have $E[X]^2$ from this cross term. The third term in the sum above, if multiplied out is $n^2E[X]^2$, and the first term is $nE[X]$. So putting things together, we have 
$\frac{1}{n^2}(nE[X]+(n^2-n)E[X]^2-n^2E[X]^2) = \frac{1}{n}\text{Var}(X)$.

Continuing, let's find the maximum likelihood estimator which we can do by taking the log of the joint PDF. Since these are iid, the joint PDF is just a product of the individual PDFs so we have $\ell(\alpha) = \log \prod^n_{i=1}(1+\alpha x_i)/2 = -n\log(2)+\sum^n \log(1+\alpha x_i)$.

Differentiating with respect to $\alpha$ and setting equal to 0, we have $\ell'(\alpha) = \sum^n \dfrac{x_i}{1+\alpha x_i} =0$. There isn't a closed form solution but if we have specific observations for $x_i$, then we can plug things in and solve for $\alpha$ to get our maximum likelihood estimator $\hat{\alpha}_{MLE}$.

Now, recall the following amazing theorem about MLEs:

**Theorem:** Let $\hat{\theta}_n$ be the maximum likelihood estimate of some population parameter whose true value is $\theta_0$. Under the some smooth conditions on the PDF $f$ and also that the true value $\theta_0$ is a critical point, not a boundary point, then $\sqrt{nI(\theta_0)}(\hat{\theta}_n-\theta_0)$ converges in distribution to the standard normal distribution $N(0,1)$.

Here, $I(\theta)=E[(\partial_\theta \log f(X|\theta))^2]$ and so $I(\theta_0)$ is some number and the variance of our $\hat{\alpha}_{MLE}$ is approximately $\frac{1}{nI(\alpha)}$ for large $n$. As a reminder, usually $\theta_0$ is unknown to us but by taking lots of samples to produce $\hat{\theta}_n$, we can predict the mean $\theta_0$ of $N(\theta_0,1/nI(\theta_0))$.

To compute $I(\alpha)$, we have $\partial_\alpha (\log(1+\alpha x)-\log 2) = \dfrac{x}{1+\alpha x}$. So the expected value is $\frac{1}{2}\int^1_{-1}\dfrac{x^2}{(1+\alpha x)^2} (1+\alpha x)\, dx$. The integrand is $x^2/(1+\alpha x)$ and we can do long division before integrating to get $x/\alpha -1/\alpha^2+1/(\alpha^2+\alpha^3x)$ (don't forget to divide by 2 later). The first term is an odd function so that integral will be zero. If we work things out and do a bit of simplifying, we find that for $\alpha \neq 0$ in $(-1,1)$, this number works out to be $\frac{1}{2\alpha^3}(-2\alpha + \log\left(\dfrac{1+\alpha}{1-\alpha}\right))$. When $\alpha=0$, then the integrand is just $x^2/2$ and hence, $I(0)=1/3$.

Thus, we can now compute the efficiency of the method-of-moments estimator to the maximum likelihood estimator (just take the ratio): $\dfrac{\text{Var}(\hat{\alpha}_{MLE})}{\text{Var}(\hat{\alpha}_{MOM})} = \frac{1}{nI(\alpha)}\cdot\frac{n}{3-\alpha^2} = \dfrac{2\alpha^3}{3-\alpha^2}\left(\log\left(\dfrac{1+\alpha}{1-\alpha}\right)-2\alpha \right)^{-1}$. We can plot this and find that as $|\alpha|\to 1^-$, this ratio goes to 0, meaning the variance of the MLE is getting smaller faster than that of MOM and is more efficient for larger $\alpha$. And for $\alpha=0$, the efficiency is exactly 1; this is also the unique global maximum of the curve. So in fact, for all $\alpha \in (-1,1)$, MLE is as efficient or more efficient than MOM.

**Theorem (Cramer-Rao):** Let $X_1,...,X_n$ be iid with PDF $f(x|\theta)$ and $T=t(X_1,...,X_n)$ is some **unbiased** estimate of the parameter $\theta$. Then under some smoothness assumptions on $f$, the variance $V(T)\geq \dfrac{1}{nI(\theta)}$. 

**Remark:** Being unbiased, the mean squared error is simply the variance since the biased term goes away. An unbiased estimate which achieves this lower bound is called **efficient.**

**Proof:** Let $Z = \sum^n_{i=1} \partial_\theta \log(f(X_i|\theta)) = \sum^n \dfrac{\partial_\theta f(X_i|\theta)}{f(X_i|\theta)}$. In my notes [[20240903101636]], I showed that the expected value $E[Z]=0$. Also, by definition, the correlation of two variables is their covariance divided by the squareroot of the product of their variances and this is always $\leq 1$. So $\text{Cov}^2(Z,T)\leq V(Z)V(T)$. We also know that $I(\theta) = V[\partial_\theta \log f]$ by definition and so $V(Z) = nI(\theta)$.

So we now want to show that the covariance $\text{Cov}(Z,T)=1$ (which is rather remarkable since $T$ can be **any** unbiased estimator). Since $E[Z]=0$, the covariance is simply

$E[ZT] = \int...\int \left(t(x_1,...,x_n)\left(\sum^n_{i=1}\dfrac{\partial_\theta f(x_i|\theta)}{f(x_i|\theta)}\right)\prod^n_{j=1}f(x_j|\theta)\right)\, dx_1...dx_n$

Note that if we take the derivative of the product term with respect to $\theta$, then the product rule gives us a sum of $n$ terms where one of them is a derivative $\partial_\theta f(x_i|\theta)$ and the rest of the terms are $f(x_j|\theta)$ where $j \neq i$. In other words, the sum term times the product term above is equal to $\partial_\theta (\prod^n f(x_j|\theta))$.
Moreover, since $t$ is independent of $\theta$, under the needed smoothness assumptions, we can move $\partial_\theta$ past the integrals. So we now have
$E[ZT]=\partial_\theta \left(\int...\int t(x_1,...,x_n)\prod^n_{j=1}f(x_j|\theta)\, dx_1...dx_n\right) = \partial_\theta E[T] = \partial_\theta (\theta) = 1$.

So we've shown that the covariance above is 1 and dividing by $V(Z) = nI(\theta)$ completes the proof. $\square$

**Example:** The Poisson distribution has $I(\lambda) = 1/\lambda$. This theorem says that for any unbiased estimator $T$ of $\lambda$ based on a sample of independent Poisson random variables $X_1,...,X_n$, the variance $V(T)\geq \lambda/n$.

The maximum likelihood estimate of $\lambda$ is $\bar{X}$ (an unbiased estimator) whose variance is $\lambda/n$. So the MLE estimate is optimal among all unbiased estimators. However, it is possible that there is a biased estimator with a smaller mean squared error.

### Sufficiency

Here's something to ponder: if we flip a (possibly) biased coin $n$ times and get $k$ heads, then we can estimate the probability of heads to be $k/n$. Note that here, we're only using $k$, we're not using more information about the distribution such as the order in which the heads occurred. In this way, the statistic $k/n$ is "enough" for our purposes, we don't need to know more about how the heads were generated. With that said, here's a definition.

**Definition:** A statistic $T(X_1,...,X_n)$ is **sufficient** for $\theta$ if the conditional distribution of $X_1,...,X_n$ given $T=t$ does not depend on $\theta$ for any value of $t$.

So we do not gain further information about $\theta$ by knowing more about the probability distribution of $X_1,...,X_n$. Put another way, **how** $t$ is achieved is independent of $\theta$.

**Example:** Motivated by the coin flip scenario, let $X_1,...,X_n$ be a sequence of independent Bernoulli random variables with $P(X_i=1) = \theta$. Then $T=\sum^n_{i=1}X_i$ is sufficient for $\theta$. The conditional probability (by definition) is $P(X_1=x_1,...,X_n=x_n|T=t) = P(X_1=x_1,...,X_n=x_n,T=t)/P(T=t)$.

Since $X_i \in \{0,1\}$ for all $i$, the numerator means the probability that a specific subset of size $t$ of the $X_i$ are equal to 1 and $n-t$ of them are equal to 0. Since the $X_i$ are independent, this probability is just $\theta^t(1-\theta)^{n-t}$. The denominator is the same thing but now it's not a specific subset; rather we run over all subsets so we have an extra ${n \choose t}$ term. Thus, the conditional probability above is $1/{n \choose t}$ which is independent of $\theta$. So $T$ is a sufficient statistic.

We could also have a very silly statistic such as $T = 0$ which is also independent of $\theta$ but it's not a useful statistic even if it's sufficient.

**Theorem:** $T(X_1,...,X_n)$ is sufficient for $\theta$ if and only if the joint PDF factors into the form $f(x_1,...,x_n|\theta) = g(T(x_1,...,x_n),\theta)h(x_1,...,x_n)$.

I won't give the proof here but they are found in Churchill's Lecture 6 notes.

**Corollary:** If $T$ is a sufficient statistic for $\theta$, then the maximum likelihood estimate is a function of $T$, viewed as its own variable (coordinate).

**Proof:** Let's write $\vec{x}=(x_1,...,x_n)$. Above, we have that the joint PDF $f(\vec{x}|\theta) = g(T(\vec{x}),\theta)h(\vec{x})$ which is the likelihood. To maximize this quantity, we just need to maximize $g(T,\theta)$. $\square$

**Theorem (Rao-Blackwell):** Let $\hat{\theta}$ be an estimator of $\theta$ with $E[\hat{\theta}]<\infty$ for all $\theta$. Suppose $T$ is a sufficient statistic for $\theta$ and let $\tilde{\theta} = E[\hat{\theta}|T]$. If $\tilde{\theta} \neq \hat{\theta}$, then for all $\theta$, $E[(\tilde{\theta}-\theta)^2] < E[(\hat{\theta}-\theta)^2]$.

**Proof:** First, we argue that $\tilde{\theta}$ and $\hat{\theta}$ have the same expected value. Recall that the expected value of an expected value is itself: $E[E[X]]=E[X]$. Secondly, $E[E[Y|X]] = \int E[Y|X]p(x)\,dx = \int p(x)\int y p(y|x)\, dydx = \int y\left(\int p(y|x) p(x) \, dx \right)\, dy$. But $\int p(y|x)p(x) \, dx= p(y)$ (we integrated out the $x$). So we then have $\int y p(y)\, dy = E[Y]$.

Hence, $E[\tilde{\theta}] = E[E[\hat{\theta}|T]] = E[\hat{\theta}]$. Thus, we can just compare the variances.
$V(\hat{\theta}) = V(E(\hat{\theta}|T) + E(V(\hat{\theta}|T)) = V(\tilde{\theta}) + E(V(\hat{\theta}|T))>V(\tilde{\theta})$ unless the variance $V({\hat\theta}|T)=0$ which only occurs if $\hat{\theta}$ is a function of $T$ in which case $\hat{\theta} = \tilde{\theta}$. $\square$

The first equality $V(\hat{\theta}) = V(E(\hat{\theta}|T)) + E(V(\hat{\theta}|T))$ is the [law of total variance](https://en.wikipedia.org/wiki/Law_of_total_variance). For the first term, compute the conditional mean across different $T$ and see how it varies, for the second, it's the average variation across different $T$. 
