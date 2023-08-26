---
title: 'Fun Fact About Partitions'
date: 2023-08-26
permalink: /posts/2023/08/partitions/
tags:
  - combinatorics
---

Let $p(n)$ denote the number of unordered partitions of $n$. For example, if $n=5$, we can partition this as $1+1+1+1+1,1+1+1+2,1+1+3,1+4,5,1+2+2,2+3$. So $p(5)=7$. We can write down a generating function $P(x) = \sum^\infty_{n=0} p(n)x^n$. But also, observe that if we wrote out $(1+x+x^2+x^3+...)(1+x^2+x^4+x^6...)...(1+x^k+x^{2k}+x^{3k})...$ and start multiplying things out, it amounts to picking an element from each "bubble." If we want a finite product, we eventually only choose 1's. So pick something from the first bubble, say $x^2$, $x^6$ from the second, and $x^6$ from the third, then all 1's. The product is $x^{14}$ and these choices gave us a partition $14=1+1+2+2+2+3+3$. How did we produce this? Our choice of $x^2$ from the **first** bubble says we want two contributions of 1. Our choice of $x^6 = (x^2)^3$ from the **second** bubble says we want three contributions of 2. And our choice of $x^6=(x^3)^2$ from the **third** bubble says we want two contributions of 3.
