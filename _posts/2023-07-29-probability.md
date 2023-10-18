---
title: 'A "Basic" Probability Problem'
date: 2023-07-29
permalink: /posts/2023/07/probability/
tags:
  - probability
---
This is yet another post in the series of "I am not at all an expert in this but enjoyed learning about it." Also, I wanted to write something shorter, that doesn't require a big time commitment to read. This seems to fit the bill. The problem that will be posed is basic in the sense that it is easy to understand the question but I did not know how to solve it.

Let $(\Omega,\mu)$ be a probability measure space. A **random variable** is a map $X:\Omega \to \mathbb{R}$ such that the probability that $X=n$, written as $P(X=n)$, equals $\mu(X^{-1}(n))$. Maybe this definition is a bit backwards since we're assuming we know what it means to consider probability. But anyways, we could also have $X:\Omega \to \mathbb{N}$. In this discrete case, the **expected value** $\mathbb{E}(X):= \sum_n n\cdot P(X=n)$. More generally, if the target is $\mathbb{R}$, then the expected value is $\mathbb{E}(X):= \int^\infty_{-\infty}t \mu(X^{-1}(t))\, dt$. Now, we can write $\mu(X^{-1}(t))$ as an integral: $\int_{X^{-1}(t)} 1\,d\mu$. This seems a bit silly but now we have $\int^\infty_{-\infty}t (\int_{X^{-1}(t)}d\mu)\,dt$ and we can exchange the order of integration using Fubini. So the inner integral is $\int_{X^{-1}(t)}t \, d\mu$. But now, what does this mean? We weight the measure of the set $X^{-1}(t)$ by $t$. This is exactly what the function $X$ does! If $X(p)=t$, we can view this as $X$ giving $p$ a weight of $t$. Then, if we integrate over $(-\infty,\infty)$ with respect to $t$, this is precisely just integrating $X$ over all of $\Omega$. So $\mathbb{E}(X)=\int_\Omega X\, d\mu$.

**Lemma:** Expected value is additive; i.e. $\mathbb{E}(X+Y)=\mathbb{E}(X)+\mathbb{E}(Y)$. This is because of the linearity of integration. Note there are no conditions on $X$ and $Y$. In particular, they can be independent of each other or dependent on each other.

The **variance** of a variable is defined to be $\mathbb{E}((X-\mathbb{E}(X))^2)$. So we create a new variable $Y=X-\mathbb{E}(X)$ which is just to center things around the original expected value, then we square it and take the expected value of that thing. We see that this is not going to be additive.

### Balls in a Box

**Question:** Suppose we have $n$ balls in a box labeled $1,...,n$. We pull one out randomly, record the label, and put it back. What is the expected number of times we need to do this in order to have pulled out all $n$ balls? This was posed to me by [Yankl Mazor](https://yankeleh.github.io/). He also explained the solution. 

Let's start with a simpler situation. Let's consider a weighted coin where the probability of flipping heads is $p \in [0,1]$ and thus, the probability of flipping a tails is $1-p$. If $X$ is a random variable representing "the number of flips before seeing heads (and we'll include the flip that gives heads)," then $X$ should have the property that $P(X=n) = (1-p)^{n-1}p$.

The expected value is then $\mathbb{E}(X)=\sum^\infty_{n=1}n(1-p)^{n-1}p$. This looks like the power series for $\frac{d}{dx}(\frac{1}{1-x}) = \frac{d}{dx}\sum^\infty_{n=0} x^n = \sum^\infty_{n=1} nx^{n-1}$. We just plug in $x=1-p$ and multiply by $p$ at the end. Since the derivative is $1/(1-x)^2$, the expected value is $p/(1-(1-p))^2 = 1/p$. For example, if it's a fair coin, then $p=1/2$ and the number of times we expect we need to flip in order to see a heads is 2.

Now, to answer the original question. We can view the situation as one of $n$ different experiments. The first experiment is to see how many times we need to pick out a ball before we see a ball. Well, obviously, the very first draw will give us a ball and the probability of this happening is 1. The second experiment is to see how many times we need to pick out balls before we see a ball distinct from the first one that we see. The probability that any given draw gives a ball distinct from the first is $\frac{n-1}{n}$. The third experiment is about getting a 3rd ball distinct from the previous and the probability of any draw giving us a 3rd ball is $\frac{n-2}{n}$. Of course, we would only start this experiment after we've already drawn two distinct balls. And so on. So the list of probabilities for the experiments is:
$1,\frac{n-1}{n},\frac{n-2}{n},...,\frac{1}{n}$.

Then the expected values are $\frac{n}{n}, \frac{n}{n-1}, \frac{n}{n-2},...,\frac{n}{1}$. By the lemma above, the total expected value is $n\sum^n_{k=1}\frac{1}{k}$. The sum is called the $n$th harmonic number, denoted $H_n$. By using integration, we see that $H_n$ grows roughly at the rate of $\log(n)$ so $nH_n$ has a growth rate in the vicinity of $n\log(n)$. Indeed, if we take a Riemann sum where the rectangles of base length 1 have their left endpoints on the integers, $H_n$ is this left Riemann sum up to $n$ and integration gives a lower bound: $\log(n+1) = \int^{n+1}_1 \frac{1}{x}\, dx < H_n$. But also, using right Riemann sums, we find: $H_n < 1+\int^n_1\frac{1}{x}\,dx = 1+\log(n)$. So $n\log(n+1)< nH_n < n+n\log(n)$. I observe that $1+\log(x) < 6 \log(x)$ for $x \geq 2$ and also $\frac{1}{2}\log(x)< \log(x+1)$. So the estimate looks a little nicer now: $\frac{1}{2}n\log(n) < nH_n < 6n \log(n)$ for $n \geq 2$. For $n=1$, there's only one ball and of course, it only takes one trial.
