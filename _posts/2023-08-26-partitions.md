---
title: 'Fun Fact About Partitions'
date: 2023-08-26
permalink: /posts/2023/08/partitions/
tags:
  - combinatorics
---

Let $p(n)$ denote the number of unordered partitions of $n$. For example, if $n=5$, we can partition this as $1+1+1+1+1,1+1+1+2,1+1+3,1+4,5,1+2+2,2+3$. So $p(5)=7$. We can write down a generating function $P(x) = \sum^\infty_{n=0} p(n)x^n$. But also, observe that if we wrote out $(1+x+x^2+x^3+...)(1+x^2+x^4+x^6...)...(1+x^k+x^{2k}+x^{3k})...$ and start multiplying things out, it amounts to picking an element from each "bubble." If we want a finite product, we eventually only choose 1's. So pick something from the first bubble, say $x^2$, $x^6$ from the second, and $x^6$ from the third, then all 1's. The product is $x^{14}$ and these choices gave us a partition $14=1+1+2+2+2+3+3$. How did we produce this? Our choice of $x^2$ from the **first** bubble says we want two contributions of 1. Our choice of $x^6 = (x^2)^3$ from the **second** bubble says we want three contributions of 2. And our choice of $x^6=(x^3)^2$ from the **third** bubble says we want two contributions of 3.

From calculus, we know that $\sum_{i=0}^\infty x^k = (1-x^k)^{-1}$ so the generating function $P(x) = \prod^\infty_{k=1}(1-x^k)^{-1}$. Here is a cute fact about partitions. **Proposition:** The number of partitions of $n$ into odd pieces equals the number of partitions of $n$ into unequal pieces.

What I mean by a partition with odd pieces just means that $n=a_1+a_2+...+a_p$ where all the $a_i$ are odd. And by a partition with unequal pieces I just mean that $n=b_1+b_2+...+b_q$ where all the $b_\ell$ are distinct. So here's the proof. The generating function for counting the number of odd partitions is a slight modification of the product above: $\prod^\infty_{k=1}(1-x^{2k-1})^{-1}$; the same sort of reasoning from before applies exactly to this situation. On the other hand, to count the number of unequal partitions, we just use $\prod_{k=1}^\infty (1+x^k)$. From each bubble, we can either choose 1 or the power of $x$ and each time we make a choice, the power of $x$ is different than all the ones that came before. And now, we observe that

$\prod_{k=1}^\infty (1+x^k)=\prod^\infty_{k=1} \frac{1-x^{2k}}{1-x^k} = \prod_{k=1}^\infty (1-x^{2k}) \prod^\infty_{\ell=1}(1-x^\ell)^{-1}$. So far, I'm just using that $a^2-b^2=(a-b)(a+b)$ and then reindexing and separating the two products. Lastly, we see that the second product runs through all powers of $x$ while the first only through the evens. When quotienting, we just have the odd powers in the denominator left: $\prod^\infty_{k=1} (1-x^{2k-1})^{-1}$.
