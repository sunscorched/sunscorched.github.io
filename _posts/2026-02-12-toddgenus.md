---
title: 'Complex Cobordism, Landweber Exatness, and the Todd Genus'
date: 2026-02-12
permalink: /posts/2026/02/toddgenus/
tags:
  - complex geometry
  - index theorem
  - stable homotopy theory
---

In my [previous blog](https://sunscorched.github.io/posts/2026/02/spin/), I wrote about the $\widehat{A}$-genus and its refinement $\alpha: \Omega^{\text{Spin}}\_\* \to KO^{-\*}$ which is a graded ring morphism. This map  comes from a $\mathbb{E}\_\infty$ ring morphism which I'll also call $\alpha:M\text{Spin} \to KO$ of ring spectra. Since we see real K-theory featured and spin manifolds, we can ask if there's any ring spectrum map which features complex K-theory and complex manifolds that then gives rise to a map of graded rings and a genus. The short answer is yes, there's a map from $MU \to KU$ which is complex cobordism to complex K-theory and the genus is the so-called Todd genus $td: \Omega^U\_\* \to KU^\*$. Here, we're dealing with stably almost complex manifolds. Complex K-theory also exhibits Bott periodicity and so $KU^* \cong \mathbb{Z}[x,x^{-1}]$ where $\deg x=2$. On the other hand, $\Omega^U_* \cong \mathbb{Z}[x_2,x_4,x_6,...,x_{2i},...]$. I'll try to explain some of the ideas behind this but in an anachronistic way.

From the perspective of getting algebraic invariants for topological spaces, spectra are exactly that: they yield extraordinary cohomology theories. In particular, we may be interested in cohomology theories which give us a theory of Chern classes. This would mean we want classes which are invariant under pullback of functions, they make sense for Whitney sums of vector bundles, that sort of thing. With usual cohomology which satisfies the Eilenberg-Steenrod axioms, we have an additive theory where the 1st Chern class behaves well with tensor products: $c_1(L\otimes K) = c_1(L)+c_1(K)$. This is called an additive theory because it comes from the so-called additive formal group law. I will proceed in a rather unorthodox and unhistorical way, beginning with more recent ideas and going back.


## Formal Group Laws

Let $E$ be a multiplicative cohomology theory; i.e. comes from a ring spectrum. We say that $E$ is **even** if its homotopy groups vanish in odd degrees and is **periodic** if $E^*(pt)$ contains an invertible element of degree 2. Of course, $KU$ satisfies both of these.

Let $E$ be an even periodic cohomology theory. One can then show that $E^\*(\mathbb{CP}^\infty) \cong E^\*(pt)[\![t]\!]$ and $t$ is a choice of a cohomology class in degree 0 (could be in degree 2 but the periodicity allows us to treat it as any even degree we like). Let $L \to X$ be a complex line bundle classified by $f:X \to \mathbb{CP}^\infty$. Then, we may define $c_1^E(L) :=f^*(t) \in E^0(X)$. In other words, we get a theory of Chern classes for $E$! We often call such spectra $E$ to be complex oriented theories.

Of course, for singular cohomology, the Chern classes are additive when we tensor line bundles. But for example, in $KU$, $c^{KU}_1(L) = [L]-1$ and it satisfies $c_1^{KU}(L_0 \otimes L_1)+1 = (c^{KU}_1(L_0)+1)(c^{KU}_1(L_1)+1)$ and so $c_1^{KU}(L_0 \otimes L_1) = c^{KU}_1(L_0) + c^{KU}_1(L_1) + c^{KU}_1(L_0)\cdot c^{KU}_1(L_1)$ (the multiplicative formal group law). 

For general even periodic $E$, we don't expect either the additive or multiplicative formulae to hold but we do expect there to be some formula $c_1^E(L_0 \otimes L_1) = F(c^{KU}_1(L_0),c^{KU}_1(L_1))$ where $F$ is a formal power series in two variables. This follows from examining $E^*(\mathbb{CP}^\infty \times \mathbb{CP}^\infty) \cong E^\*(pt)[\![t_1,t_2]\!]$.

So from studying this, we see that the power series $F$ satisfies some properties.
1. $F(0,t)=t$
2. $F(t_1,t_2)=F(t_2,t_1)$ because tensor product is commutative.
3. $F(t_0,F(t_1,t_2))=F(F(t_0,t_1),t_2)$ because tensor product is associative up to isomorphism.

If $R$ is a ring, then a **formal group law** is $F \in R[\![x,y]\!]$ satisfying these three identities. We say that $F,F'$ are **strict isomorphic** if we have a change of coordinates $g$ that sends $t \mapsto t+a_2t^2+a_3t^3+...$ so that $F'(x,y)=g^{-1}(F(g(x),g(y)))$; this $g$ itself is also a formal power series. When they're strict isomorphic, we say they have the same **formal group.**

Of course, we also have Quillen's theorem which says that complex cobordism $MU$ has $\pi_\* MU \cong L$, the Lazard ring which is the universal ring for formal group laws. Put another way, for an FGL $F$ over a ring $R$, there is a morphism $\phi:\pi_\* MU \cong L \to R$ so that $\phi F_{MU}=F$.

So given an even periodic cohomology theory, we can get a formal group law out of. This fits the philosophy of algebraic topology which is to associate algebraic structure to things arising in topology. The cohomology theory is realized by a spectrum, a topological object, and we associate to it an algebraic invariant, the formal group law over a commutative ring.

Since $MU$ is the universal complex oriented theory and $L$ is the universal ring for formal group laws, we might hope that we can use them to construct a map going the other way: given a FGL over a commutative ring $R$, we wish to use $MU_\*$ to construct a complex oriented cohomology theory. The most naive thing to do is to use $\phi:\pi_\*MU \to R$, the morphism classifying the FGL to make $R$ a module over $\pi_\* MU$. We then form a candidate cohomology theory $X \mapsto R\otimes_{\pi_\* MU} \widetilde{MU}^*(X)$. This would be a cohomology if exactness hold and is an exact functor if $R$ is a flat $\pi_\*MU$ module; i.e. exact sequences are sent to exact sequences. But that's a very strong condition because $L \cong \mathbb{Z}[x_1,x_2,x_3,...]$ is very large and we don't need the full power of flatness. Instead, we can get something weaker. Landweber's theorems precisely gives these weaker conditions for exactness to hold. Let's first state this as a prototheorem without saying what the weaker conditions are until I give a bit of exposition.

**Prototheorem (Landweber):** Given a commutative ring $R$ and formal group law over $R$, under some assumptions, there is a unique even periodic cohomology theory $E$ which gives rise to $R \cong E^0(pt)$ and $F$ using the complex cobordism construction above by tensoring. The conditions on $R$ are purely algebraic.

So the point is that for a ring and FGL, two purely algebraic objects, we can build a cohomology theory that yields a theory of Chern classes by using complex cobordism. The conditions needed are as follows. Let $R$ be a ring and suppose there is a sequence $v_1,v_2,v_3,...$ in $R$ such that for all $i$, $v_i$ is not a zero divisor on $R/(v_1,...,v_{i-1})$. That is, we can multiply by $v_i$ and that would be an injective map on this quotient ring. Then we say that the first $i$ elements $(v_1,...,v_i)$ of the sequence is a **regular sequence.**

**Theorem (Landweber):** Suppose that $\phi:L \to R$ is a ring morphism from the Lazard ring $L \cong MU_\*(pt)$. This ring morphism can be used to make $R$ an $L$-module. Suppose there exists a sequence $v_1,v_2,v_3,...$ so that for every prime $p$ and every $i$, $(p,v_1,v_2,...,v_i)$ are all regular sequences. Then $X \mapsto R_* \otimes_L MU_*(X)$ is a homology theory. The tensoring being over $L$ means $\ell \in L$ acts on $R$ by $\ell \cdot r:= \phi(\ell)r$.

In the case that $R = KU^\* = \mathbb{Z}[x,x^{-1}]$, the ring does satisfy the Landweber conditions and so the cohomology theory that is complex K-theory is actually reconstructible directly from complex cobordism! This is the content of the **Conner-Floyd** theorem which came before the Landweber exactness theorem. The Conner-Floyd work also establishes an orientation $KSp \to KO$. Anyways, importantly, for Landweber's theorem, we require a map $L=MU_\* \to \mathbb{Z}[x,x^{-1}]$. I would like to say that this map **definitionally is** the Todd genus which assigns to a complex cobordism class an integer.

For more on $MU$ and how chromatic homotopy theory aims to study these complex oriented theories, see my [first blog](https://sunscorched.github.io/posts/2023/07/moravaKtheory/).


## Todd Genus

Okay, but I've approached this in a very achronistic way. The first time the Todd genus was encountered, it was not definitionally viewed as this map in the Landweber exactness theorem. It was viewed simply as a number that we assign to complex manifolds. Or rather, we only need to be able to discuss Chern classes so only need stably almost complex structure. But for the purposes of the following discussion, we do actually need a complex manifold.

Let's consider a complex manifold $X$ of complex dimension $n$ with a holomorphic vector bundle $E \to X$. The **holomorphic Euler characteristic** of $E$ in sheaf cohomology is the alternating sum $\chi(X,E) = \sum^n_{q=0} (-1)^q \dim_{\mathbb{C}}H^q(X,E)$. Or instead of sheaf cohomology, think of these as cohomology groups as differential $(0,q)$-form classes. The differential in question is the Dolbeault operator $\overline{\partial}$. In particular, $H^0(X,E)$ is the space of holomorphic sections of $E$.

**Theorem (Hirzebruch-Riemann-Roch):** Let $ch(E)$ be the Chern character of $E \to X$ and $td(X)$ be the Todd class. The Todd class can be computed for any vector bundle from Chern classes; in this case, $td(X)$ means we use $TX$ as the vector bundle. Then $\chi(X,E) = \int_X ch(E)\cdot td(X)$.

**NB:** The Todd genus of $X$ would simply be $\int_X td(X)$. The specific way in which to compute $td(X)$ involves the function $T(x) = \dfrac{x}{1+e^{-x}}$ or the sigmoid function times $x$. This is similar to how the $\widehat{A}$-genus has an associated power series $Q(z) = \dfrac{\sqrt{z}/2}{\sinh(\sqrt{z}/2)}$. In fact, on an **almost complex manifold** $X$, $td(X) = e^{c_1(X)/2}\widehat{A}(X)$.

**Example of using HRR:** Let $X$ be a compact **Kähler** manifold of complex dimension $n$ and $L$ is an **ample** line bundle while $K_X$ is the canonical line bundle. Then the Kodaira Vanishing Theorem tells us that $H^q(X,K_X\otimes L)=0$ for $q>0$. If we also know that $\chi(X,K_X \otimes L) \neq 0$, this means that $H^0(X,K_X \otimes L) \neq 0$; i.e. there are holomorphic sections of $K_X \otimes L$.

Next, let's return to a theory of Chern classes.

**Example:** Consider the Chern character $ch:KU \to H\mathbb{Q}$, which is a morphism of cohomologies where $H\mathbb{Q}$ is our usual singular cohomology. Let $c_1^K$ denote the Chern classes with values in K-theory and use the opposite sign convention as above (doesn't matter so much): $c^K_1(L) = 1-[L^\*]$. Then $ch(c_1^K(L)) = 1-e^{c_1(L^\*)}$. Since $c_1(L^\*)=-c_1(L)$, we can write this as:
$\dfrac{1-e^{-c_1(L)}}{c_1(L)}\cdot c_1(L)$. The associated series multiplied by $c_1(L)$ is $\dfrac{1-e^{-x}}{x}$ which is the inverse of the function $T(x)$ from earlier.

I want to end this section with a note about the complex cobordism ring. Remember that it is about cobordism classes of **stably** almost complex manifolds.

**Example:** Consider the fact that $\mathbb{CP}^1$ has a unique almost complex structure and it is automatically integrable for dimension reasons. The underlying smooth manifold is $S^2$ and the connected sum $S^2 \\# S^2 \cong S^2$ so we might think that in the complex cobordism ring, $[\mathbb{CP}^1] + [\mathbb{CP}^1] = [\mathbb{CP}^1 \\# \mathbb{CP}^1] = [\mathbb{CP}^1]$. The first equal sign is correct but if the second one is also correct, we're forced to accept that $[\mathbb{CP}^1] = 0$ in this ring. So what's the deal? The thing is that we're working with **stably tangential** data and so the stably almost complex structure on $\mathbb{CP}^1 \\# \mathbb{CP}^1$ is not the same as that of $\mathbb{CP}^1$.

## Appendix 1: Landweber Exactness

Now LEFT is a theorem about complex oriented homology theories which correspond to **homotopy** ring spectra, not necessarily $\mathbb{E}\_\infty$ ring spectra. How would we get a theory enriched to the level of $\mathbb{E}_\infty$ ring spectra? For that, we need to formulate things in terms of derived algebraic geometry.

A module over $MU_\*$ is the same as a quasi-coherent sheaf $\mathcal{F}$ over $\text{Spec}\, L$, where $L$ is the Lazard ring. If them module is $M=MU_\*(X)$, then $M$ has the extra datum of a $MU_*MU$ coaction. A coaction on the ring level corresponds to the fact that $\mathcal{F}$ is an equivariant sheaf with respect to an action of an affine group scheme $G$. It is a theorem of Quillen that $G \cong \mathbb{Z}[b_1,b_2,...]$ and assigns to every ring $R$ the **group** of power series $R[[t]]$. To be invertible, the elements are of the form $g(t) = t + b_1 t^2 + b_2 t^3 +...$. The formal group laws set-correspond to $(\text{Spec}\, L)(R)$ and we have an action by $g \in R[[t]]$ by $g\cdot F(x,y) =g (F(g^{-1}(x),g^{-1}(y)))$. This is just the coordinate changes of formal group laws.

Therefore, one can identify the stack quotient $(\text{Spec}\, L)//G$ with the stack of (1-dimensional) formal groups $\mathcal{M}\_{fg}$ and  defines a quasi-coherent sheaf over this stack. If the module $M$ defines a **flat** quasi-coherent sheaf $\mathcal{F}$, then we get a homology theory. Flatness for a quasi-coherent sheaf is sort of the geometric equivalence of a flat module; i.e. tensoring with the module preserves exact sequences. But since we're dealing with sheaves, this needs to be compatible with how sheaves glue local charts. The Landweber exactness theorem can then be interpreted as a flatness criterion for $\mathcal{M}\_{fg}$.

To answer the original question of when we get $\mathbb{E}\_\infty$ ring spectra, we turn to the work of Jacob Lurie. Just to recap, if $X$ is an algebraic stack and $X \to \mathcal{M}\_{fg}$ a **flat** map of stacks, the discussion above shows that we get a presheaf of (homotopy) ring spectra on $X$. If this map factors over each $M_p(n)$ (the stack of 1-dimensional $p$-divisible groups of height $n$) and the map $X \to M_p(n)$ is etale (akin to local diffeomorphisms), then this presheaf can be refined to a sheaf of $\mathbb{E}_\infty$ ring spectra. I don't know much about this but it reminds me of Morava K-theories which are used to "chromatically" study $MU$.

## Appendix 2: Quaternionic K-Theory

Given the pattern of having a ring map from a Thom spectra for cobordism of manifolds to some form of K-theory, we may ask if there is something like this for quaternions. Indeed, there is a $KSp$, a quaternionic K-theory but it is not a ring spectrum. Also, due to the Bott periodicity we see for Clifford algebras (up to Morita equivalence) and the fact that some of these Clifford algebras are quaternionic, so we could just stick to real K-theory, in a sense.

Much of what we've talked about both in this post and the previous one about spin cobordism and the $\alpha$-invariant, we could focus on Dirac operators for so-called $\text{Spin}^c$ or even $\text{Spin}^h$ manifolds. For more on this, a good place to look is Jiahao Hu's [thesis](https://arxiv.org/abs/2310.05061).

