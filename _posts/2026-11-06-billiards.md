---
title: 'Mathematical Polygonal Billiards'
date: 2026-11-06
permalink: /posts/2026/11/billiards/
tags:
  - dynamical systems
---

"Polygonal billiards is the study of Newtonian motion of a point inside a polygon." - Paul Seidel. Most of this post is based off of the billiards chapter in his excellent [notes](https://www.ams.org/open-math-notes/omn-view-listing?listingId=111288). There is a wealth of other interesting material in those notes. Anyways, mathematical billiards is an idealized version of the game of billiards with a ball bouncing off the walls of the table; for this post, we'll stick to polygonal tables. We typically assume that all collisions are completely inelastic and there is no friction so that the trajectory of the ball can go on indefinitely. When the ball hits a wall, it comes in at some angle measured between the trajectory line and the wall. We have some choices here so we'll always choose to work with an angle $\alpha$ between 0 and $\pi/2$. The ball then reflects off of the wall such that the angle of the outgoing ray and the wall is also $\alpha$. If the ball hits a vertex of the polygon, we'll say that the trajectory after that is undefined.

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
