---
title: 'Mathematical Polygonal Billiards'
date: 2026-11-06
permalink: /posts/2026/11/billiards/
tags:
  - dynamical systems
---

"Polygonal billiards is the study of Newtonian motion of a point inside a polygon." - Paul Seidel. Most of this post is based off of the billiards chapter in his excellent [notes](https://www.ams.org/open-math-notes/omn-view-listing?listingId=111288). There is a wealth of other interesting material in those notes. Anyways, mathematical billiards is an idealized version of the game of billiards with a ball bouncing off the walls of the table; for this post, we'll stick to polygonal tables. We typically assume that all collisions are completely elastic and there is no friction so that the trajectory of the ball can go on indefinitely. When the ball hits a wall, it comes in at some angle measured between the trajectory line and the wall. We have some choices here so we'll always choose to work with an angle $\alpha$ between 0 and $\pi/2$. The ball then reflects off of the wall such that the angle of the outgoing ray and the wall is also $\alpha$. If the ball hits a vertex of the polygon, we'll say that the trajectory after that is undefined.

An alternative analogy is to consider a laser pointer that you place on a table. Mirrors are set up so that when you shine the laser, it bounces off the mirrors and you track the trajectory of the photons. Of course, one could track the trajectory via careful angle measurements and precisely drawn diagrams. But there is a useful method called **unfolding.** When the ball hits the edge, we reflect the whole table across that edge. The outgoing trajectory also gets reflected and thus, in the unfolded diagram, the trajectory is simply a straight line. You can work out the angles to convince yourself that the trajectory would be a straight line. If you begin with the unfolded plane and draw a straight line, you can then fold everything back up, mapping the line segments as you fold, so that in the end, you have a single copy of the table with all the line segments in place to form the billiards trajectory.

Let's begin with a simple example of a square billiard table. Note that whenever the ball bounces on the left, there is wall-crossing on the right.

<video controls loop autoplay muted width="600">
  <source src="/assets/square_billiards.mp4" type="video/mp4">
</video>

In this square grid, let's suppose it has side length normalized to 1. If the starting coordinates of the ball are rational and the slope of the trajectory is also rational, then the trajectory will eventually lead the ball to its starting point. These are **periodic** trajectories; trajectories that eventually return to their starting point and direction of travel, and hence, will trace the same path again. Periodic trajectories are defined not just for a square table but any polygon or even tables with curved edges. Below is an example of a periodic trajectory. It returns to its starting point more than once but the first time it does, it is not moving in the initial direction of travel. In the unfolded plane, it's rather easy to see if a trajectory is periodic by seeing if the line passes through the same point (after accounting for reflections).

<video controls loop autoplay muted width="600">
  <source src="/assets/periodic_billiards.mp4" type="video/mp4">
</video>

For any triangle where all of its angles are acute, we can drop an altitude line from each vertex; i.e. the line which forms a right angle when it intersects the opposite side. We can then form an inscribed triangle out of those intersection points (the base of the altitudes). This triangle is called the orthic or Fagano triangle and gives us a 3-bounce trajectory. It should be pointed out that not all periodic orbits need to form a "loop". Some periodic orbits in right triangles, for example, simply reverse direction. So the image of the trajectory is a path that does not close up to form a loop.

The question of finding periodic trajectories is not easy. In fact, up until June 2026, it was not even known if every triangle has a periodic trajectory. There is a [preprint](https://arxiv.org/abs/2606.10102) claiming that every polygon has at least one periodic orbit.

Of course, the unfolding principle works for other kinds of tables as well. Here is an equilateral triangle as a billiards table.

<video controls loop autoplay muted width="600">
  <source src="/assets/triangle_billiards.mp4" type="video/mp4">
</video>

And here is one for a regular hexagon.

<video controls loop autoplay muted width="600">
  <source src="/assets/hexagon_billiards.mp4" type="video/mp4">
</video>

I've been choosing polygons that give tilings of the plane but we don't have to do so. There's no problem with the reflected images overlapping with each other in the visualization, so long as its understood that there's not "real" overlap in the actual dynamical system. For example, when can make examples using non-convex polygon. The unfolding can still be done and we could define a topological space from the unfolding which would form a Riemann surface.

## Group Actions

Now, there is something interesting about the examples I've given. Let's begin more generally. If $P$ is our polygon and $r_1,...,r_m$ are reflections across its edges, then let $G$ be the group generated by all of these reflections; it is a subgroup of the isometries on the plane. Let $G\cdot P = \{g(P): g \in G\}$ be all the reflected copies of $P$. The stabilizer of the original $P$ are the elements of $G$ which keep $P$ fixed. If the stabilizer is trivial, we say the group action is **free.** Considered another way, is it possible to apply two different group elements to $P$ and get the same copy; i.e. $g(P)=h(P)$? If it is possible, then the action is not free since $gh^{-1}(P)=P$ but $gh^{-1}$ is not the identity. 

For a square and equilateral triangle, their associated groups do give free actions. For the square, if we let $P = [0,1]\times [0,1]$, then the reflections are:
- $(x,y) \mapsto (-x,y)$
- $(x,y) \mapsto (2-x,y)$
- $(x,y) \mapsto (x,-y)$
- $(x,y) \mapsto (x,2-y)$
  
And the group they generate are transformations of the type $(x,y) \mapsto (\epsilon_1 x+2m,\epsilon_2y+2n)$ where $\epsilon1,\epsilon_2 =\pm 1, m,n \in \mathbb{Z}$. If one of these transformations preserves $P$, this means $\epsilon_1[0,1]+2m = [0,1]$. If $\epsilon_1=+1$, then $m$ must be 0. If $\epsilon_1 = -1$, then then interval is transformed to $[2m-1,2m]$ which cannot equal $[0,1]$ for any $m$. A similar argument for the $y$-coordinate shows then that the only transformation preserving $P$ is $\epsilon_1=\epsilon_2=+1$ and $m=n=0$.

The equilateral triangle is a bit trickier but still simple to show the action is also free. But it's not the case for a hexagon. Take a regular hexagon centered at the origin in the complex plane with vertices on the 6th roots of unity $e^{k\pi i/3}$ for $k=0,...,5$. Label the vertices as $v_0,...,v_5$ and let $r_j$ be the reflection across the line containing the side from $v_j$ to $v_{j+1}$ where the indices are taken modulo 6. Then the element $g=r_3 \circ r_1 \circ r_2 \circ r_0$ is not the identity; it's a counterclockwise rotation in the plane by $2\pi/3$. However, $g(P)=P$.

This does not invalidate the unfolding for the hexagon but it is an interesting subtly. If we try to fold the tiles back to get the trajectory and we only use the geometric location of the end tile, we can run into the issue of choosing the wrong way back to the initial tile. What we get could be the wrong trajectory, even disconnected line segments.

## The Poincaré Recurrence Theorem

Let me end with a theorem of Poincaré.

**Theorem:** Inside any polygon $P$, choose any point and any direction. There exists a billiards trajectory whose starting position and direction are arbitrarily close to the ones chosen, and which after some amount of bounces, returns to a position and direction arbitrarily close to the ones chosen.

I'll simply quote Paul Seidel for an explanation:

> "'Arbitrarily close' means: you get to specify a desired precision, and the theorem guarantees the existence of a trajectory that fits those specifications. Suppose that you declare the specification to be 'positions at distance less than $0.001$ from the one we fixed, and directions whose angle differs by less than $0.001^\circ$ from the one we fixed'. By the recurrence theorem, there is a trajectory that starts off like that, and after some unknown time, again satisfies that. If you now get more picky and refine your bounds to $0.000001$, there is also a trajectory with those properties, but it will probably be much longer and complicated than the previous one. These trajectories won’t usually be periodic: they are only 'almost periodic', in the sense that they return to a state very close to their starting state."

The proof of this theorem is really quite brilliant. The key is to work in **phase space** which is a disjoint union of rectangles. The rectangles are indexed by the edges and the horizontal coordinate means a position on the edge (we exclude the endpoints since we don't deal with trajectories that hit vertices) and the vertical coordinate will be an angle between 0 and $\pi$, exclusive. That is, for each edge $e$, there is a rectangle $R_e = (0,\text(length)(e)) \times (0,\pi)$. The angle is the angle of travel of the ball as it bounces off an edge and travels back into the interior of the polygon. We'll denote the phase space by $\Omega$, following more of Seidel's notation.

Now, if we take a point $p$ in phase space, this means we choose a boundary point and inward direction. Place the ball at the boundary point, and move it in the prescribed direction until we hit the boundary of the polygon. Then, record the new position and the reflected direction (the direction in which the ball will continue after bouncing off). This defines another point in phase space, $T(p)$. This defines a billiards map $T: \Omega \dashrightarrow \Omega$. The dash arrow signifies that $T$ is not always defined; there's the issue with the vertices but that is a measure 0 event. As such, barring those problems, there is in fact, an inverse map $T^{-1}$. Let $T^n$ be the map obtained by composing $T$ with itself $n$ times. If $n$ is negative, we use the inverse.

If we make a change of coordinates, we can compute the derivative of $T$ which, at a point, is a 2 x 2 matrix. and find that the determinant equals 1. In other words, the map $T$ is area-preserving. For this reason, we get the following:

**Theorem:** Let $U \subset \Omega$ be any set with positive measure. There exists a point $p$ and a positive integer $n$ such that $T^n(p) \in U$. That is, after $n$ iterations, $p$ is mapped back into $U$.

The proof is simple. Pick any positive $N$. Since the map $T$ is area preserving, then the union of $T(U), T^2(U),..., T^N(U)$ is at most $N$ times the area of $U$. If $N$ is very large, then there must be overlap since the area of the polygon is finite, equal to a constant times its perimeter. So there are numbers $0<j<k<N$ such that $T^j(U)\cap T^k(U)$ has positive area. If we apply the inverse map to this set $j$ times, we then will get the set $U \cap T^{k-j}(U)$ which will have the same positive area which means there is a point $p \in U$ such that $T^n(p) \in U$ as well where $n=k-j$. $\square$

This theorem is equivalent to how the recurrence theorem was stated above. The "arbitrarily close" concept is captured in making $U$ have as small of positive area as we like. Moreover, the theorem is actually very general. We just ask for a few assumptions:
- the dynamical system is defined on a phase space with finite volume
- energy is conserved; e.g. not lost to friction or heat
- the dynamics are deterministic

In such systems, the Poincaré recurrence theorem still holds and there are an abundance of "almost periodic" trajectories.

## A rational billiard flow is uniquely ergodic in almost every direction

There are a few definitions of a **translation surface.** A hands-on definition is to begin with a collection of polygons in the Euclidean plane; they need not be convex. The only rule is that every edge must be paired with a parallel edge of the same length. We can then glue each edge to the edge it is paired with. There are different ways to glue but since we’re in the Euclidean plane, there exist translations; these are the maps we use for gluing. Formally, we are defining an equivalence relation on the union of the polygons, call it $P$.

The result is a topological space $X = P/\sim$ which we’ll assume is connected. In fact, $X$ will be a compact, orientable 2-manifold. Under the equivalence, some of the vertices of $P$ will be identified. Let $x \in X$ be the image of a vertex. There is a neighborhood $U_x$ of $x$ whose preimage is a union of circular sectors. We can measure the angles of those sectors. It turns out that they will sum to a multiple of $2\pi$. If the angle is larger than $2\pi$, then we say that $x$ is a **singularity**.

An alternative way to define a translation surface is that we want a compact Riemann surface with a meromorphic differential 1-form $\omega$ on it. The form is holomorphic away from the singularities and at a singular point with angle $2\pi(k+1)$, the order of the pole of $\omega$ is $k$. This kind of form is also often called an abelian differential.

Note that away from the singularities, there is a vertical flow; one can just walk “north” on $P$ and then when an edge is reached, use the identification to “teleport.” One can also multiple the abelian differential by $e^{i\theta}$ for some angle $\theta$ and thus, rotate the flow. In this way, we can ask some dynamical questions. such as whether there are periodic trajectories of this flow or whether there are trajectories that uniformly fill up the space $X$. I’ll make this more precise in a moment.

But first, let’s consider a concrete class of polygons, the ones where its angles are all rational multiples of $\pi$. In such a setting, if we have a billiard moving in some initial direction determined by an angle $\theta_0$, the possible directions its trajectory can take is finite. In fact, take all the angles which are rational multiples of $\pi$ and divide by $\pi$ so we just have rational numbers. If $N$ is the least common multiple of the denominators of all the rational numbers, the number of possible directions of the trajectory is $2N$.

Similar to how we unfolded for a single trajectory above, we now unfold by reflecting across all the edges. More precisely, we have reflections across each edge and they generate a group. We apply this group to the original rational polygon; this gives $2N$ copies of the polygon. Moreover, we’ve created parallel edge pairs of the same length so we can form a translation surface as described above.

Back to the idea of “uniformly fill up.” Start with a finite measure space $X$ with measure $\mu$. For convenience, say we normalize the total measure of $X$ to be 1. For each positive real $t$, we have a family of measurable functions $T_t:X \to X$ such that for positive $s,t$, $T_{s+t} = T_s\circ T_t$. A family of flows satisfies this axiom. We say that this family **ergodic** if each $T_t$ preserves $\mu$ and the following condition holds: for any measureable set $A$, if for all $t >0$, we have that $T^{-1}_t(A) \subset A$, then either $A$ has measure 0 or 1. We say that the family $T$ is uniquely ergodic if there is only one $T$-invariant Borel probability measure on $X$.

A consequence of being ergodic is Birkhoff’s theorem which roughly says that the time average of a function $f$ on the orbit converges to the space average of $f$. More precisely, take any member of the family $T$; for convenience, I’ll just call it $T$. Let $f:X \to \mathbb{R}$ be an integrable function. Then for almost every point $x \in X$, we have

$$\lim_{k \to \infty} \dfrac{1}{k+1}\sum^k_{i=0} f(T^i(x)) =\int_X f \, d\mu$$

For example, say $A$ has measure 0.1 and $f$ is 1 on $A$ and 0 otherwise. For a point $x$, we can look at where it moves under iterations of $T$. If it lands in $A$, then $f$ would indicate this with 1. The theorem tells us that for a large number of iterates, about 10% of the time, they land in $A$ since $A$ has 10% of the total measure. Since we could take any set $A$ with positive measure and its indicator function for $f$, this shows that under many iterates, most points would visit every set in proportion to its measure.

Brought into the context of billiards, if the billiard flow were ergodic, this would mean most trajectories bring the ball through any given (measurable) region and do so in proportion to the measure of the region. A theorem from a 1986 Annals paper tells us this is, in fact, the case for rational polygons. Or rather, somewhat stronger:

**Theorem (Kerchhoff-Masur-Smillie):** For every translation surface (which includes every rational polygon), and for almost every angle $\theta \in S^1$, the flow in the direction $\theta$ is uniquely ergodic.

I won't discuss the proof but here is a short [note](https://lipn.univ-paris13.fr/~monteil/papiers/fichiers/kms.pdf) on the theorem.

## Orbit Closures in the Moduli of Translation Surfaces

There are also many results which study the space of all translation surfaces. Let $g \geq 1$ be the genus and $\alpha = (\alpha_1,…,\alpha_n)$ be positive integers which sum to $2g-2$ and consider all pairs $(X,\omega)$ where $X$ is a genus $g$ Riemann surface and $\omega$ is a holomorphic 1-form whose zeros have multiplicities $\alpha_1,…,\alpha_n$. This is somewhat different from the setup above. But $\omega$ defines a canonical flat metric (using the complex structure of $X$) with conical singularities at its zeros. Also, integrating $\frac{i}{2}\omega \wedge \bar{\omega}$ over $X$ gives the area of the surface.

We say that $(X,\omega)$ and $(X’,\omega’)$ are equivalent if there is a biholomorphism $f:X \to X’$ such that $f^*\omega’ = \omega$. We’ll denote $\mathcal{H}(\alpha)$ as the moduli space of translation surfaces using this equivalence. When we range over all partitions of $2g-2$, we see that these $\mathcal{H}(\alpha)$ form the strata of some moduli space of genus $g$ Riemann surfaces with some extra structure.

Since translation surfaces are defined locally on $\mathbb{C} \cong \mathbb{R}^2$ with transition maps being translation maps $z \mapsto z+c$, there is an action of the group $SL(2,\mathbb{R})$ on $\mathbb{R}^2$ which preserves the transition maps since parallel edges of the same length will be sent to some other parallel pair of the same length. So the action of this group also induces flows on $\mathcal{H}(\alpha)$. For example, the Teichmüller and horocycle flows are generated by two respective families of matrices

$$\begin{pmatrix} e^t & 0 \\ 0 & e^{-t} \end{pmatrix}, \begin{pmatrix} 1& s \\ 0 & 1 \end{pmatrix}$$

**Nota bene:** It is somewhat amusing that each translation surface has its own dynamics but when we form a space of translation surfaces, that space too, has rich dynamics.

The moduli space $\mathcal{H}(\alpha)$ also has some natural coordinates. For a translation surface $(X,\omega)$, integration of $\omega$ along closed loops that generate the homology $H_1(X,\mathbb{Z})$ gives complex numbers called **absolute periods.** Similarly, we can also integrate along paths connecting the $n$ singularities to get **relative periods.** Together, we get $2g+n+1$ numbers for $(X,\omega)$. Veech and Masur proved that the map sending translation surfaces to periods is a local homeomorphism and thus, we obtain local coordinates.

Let $\mathcal{H}_1(\alpha)$ be the subset of translation surfaces with area 1. For any subset $N$ of these area 1 translation surfaces, let $\mathbb{R}N = \{(X,t\omega): (X,\omega) \in N, t\in \mathbb{R}\}$. That is, we just scale the abelian differentials.

Also, recall that the **support** of a measure is the largest closed subset where every open neighborhood of every point in this subset has strictly positive measure.

**Definition:** An ergodic $SL(2,\mathbb{R})$-invariant probability measure $\nu_1$ on $\mathcal{H}_1(\alpha)$ is called **affine** if 
1. The support of $\nu_1$ is an immersed submanifold and the self-intersection set is closed and of $\nu$-measure 0. If $f:S \to \mathcal{H}_1(\alpha)$ is the immersion, then each point of $S$ has a neighborhood $U$ such that $\mathbb{R}f(U)$ is locally given by complex linear subspace defined over $\mathbb{R}$ in the period coordinates.
2. Let $\nu$ be the measure supported on $\mathbb{R}f(S)$; i.e. scale the immersed submanifold. So $d\nu = d\nu_1da$. Then each point in $S$ has a neighborhood $U$ such that the restriction of $\nu$ to $\mathbb{R}f(U)$ is an affine linear measure in the period coordinates on $\mathbb{R}f(U)$, i.e. it is (up to normalization) the restriction of the Lebesgue measure to the subspace $\mathbb{R}f(U)$.

The 2015 Annals paper of Eskin-Mirzakhani-Mohammadi have several theorems. One of them is about orbit closures under $SL(2,\mathbb{R})$ action or the action of $P$ which is the subgroup of these matrices with 0 in the lower left corner.

**Theorem (Eskin-Mirzakhani-Mohammadi):** Let $x\in \mathcal{H}_1(\alpha)$. Then the closures of the orbits under $P$ and $SL(2,\mathbb{R})$ action are the same and moreover, is an affine invariant submanifold. That is, it admits an affine measure $\nu_1$ as defined above.

So under a rather natural group action on the moduli space, the closure of the orbit is not arbitrary but has a lot of structure. A natural question one can ask is, "How does the dynamics on a moduli space of translation surfaces relate to dynamics on a particular translation surface?" For example, if we're looking at a particular straightline trajectory on a translation surface; e.g. a trajectory for a polygonal billiards table, and this trajectory is space-filling, we can rotate it to be "vertical" and then apply the Teichmüller flow mentioned earlier. It contracts the surface vertically while expanding it horizontally. In this way, we **renormalize** the flow.

Now, in the previous section, we have a theorem for all translation surfaces and almost all directions. However, many theorems in the field of billiards are stated as "almost all translation surfaces." So given a specific translation surface, it wasn't easy to deduce its properties.

For example, we've been avoiding having trajectories going into the corners of the billiards table or the conical singularities of the translation surfaces. But we could wonder how many straightline trajectories between singularities---these are called saddle connections---exist for a given $(X,\omega)$ of length at most $L$. And also ask how the number grows as $L \to \infty$. One can show that the growth is quadratic, roughly $cL^2$ for some constant $c$ but it's not easy to determine what $c$ is.

However, with Eskin-Mirzakhani-Mohammadi's theorem, we know the orbit closure of the surface is an affine invariant submanifold that carries a finite invariant volume form. Work of Eskin-Masur show that the constant $c$ is proportional to the volume of the orbit closure.

Another example is related to the theorem from the previous section. We know that after a very long time, most trajectories on a translation surface are space-filling. But if the trajectory runs for finite time $T$, it won't be perfectly uniform yet. There will be some error and we may ask what the error decay is as a function of $T$. By renormalizing, we can then see that the error decay rate is related to how the tangent space of the moduli space stretches; this is measured by Kontsevich-Zorich Lyapunov exponents. Since EMM shows that the orbit closure is an affine invariant submanifold, the exponents can be computed from the topology of the particular affine invariant submanifold.
