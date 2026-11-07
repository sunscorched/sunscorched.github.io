---
title: 'Billiards'
date: 2026-11-06
permalink: /posts/2026/11/billiards/
tags:
  - dynamical systems
---

"Polygonal billiards is the study of Newtonian motion of a point inside a polygon." - Paul Seidel. We typically assume that all collisions are completely inelastic and there is no friction so that the trajectory of the ball can go on indefinitely. When the ball hits a wall, it comes in at some angle measured between the trajectory line and the wall. We have some choices here so we'll always choose to work with an angle $\alpha$ between 0 and $\pi/2$. The ball then reflects off of the wall such that the angle of the outgoing ray and the wall is also $\alpha$. If the ball hits a vertex of the polygon, we'll say that the trajectory after that is undefined.

Of course, one could track the trajectory via careful angle measurements and precisely drawn diagrams. But there is a useful method called **unfolding.** When the ball hits the edge, we reflect the whole table across that edge. The outgoing trajectory also gets reflected and thus, in the unfolded diagram, the trajectory is simply a straight line. You can work out the angles to convince yourself that the trajectory would be a straight line. If you begin with the unfolded plane and draw a straight line, you can then fold everything back up, mapping the line segments as you fold, so that in the end, you have a single copy of the table with all the line segments in place to form the billiards trajectory.

Let's begin with a simple example of a square billiard table. Note that whenever the ball bounces on the left, there is wall-crossing on the right.

<video controls loop autoplay muted width="600">
  <source src="/assets/square_billiards.mp4" type="video/mp4">
</video>

In this square grid, let's suppose it has side length normalized to 1. If the starting coordinates of the ball are rational and the slope of the trajectory is also rational, then the trajectory will eventually lead the ball to its starting point. These are called **periodic** trajectories and are defined not just for a square table but any polygon. Below is one such example. In the unfolded plane, it's rather easy to see if a trajectory is periodic by seeing if the line passes through the same point (after accounting for reflections).

<video controls loop autoplay muted width="600">
  <source src="/assets/periodic_billiards.mp4" type="video/mp4">
</video>

For any triangle where all of its angles are acute, we can drop an altitude line from each vertex; i.e. the line which forms a right angle when it intersects the opposite side. We can then form an inscribed triangle out of those intersection points (the base of the altitudes). This triangle is called the orthic triangle and gives us a 3-bounce trajectory. It should be pointed out that not all periodic orbits need to form a "loop". Some periodic orbits in right triangles, for example, simply reverse direction. So the image of the trajectory is a path that does not close up to form a loop.

The question of finding periodic trajectories is not easy. In fact, up until June 2026, it was not even known if every triangle has a periodic trajectory. There is a [preprint](https://arxiv.org/abs/2606.10102) claiming that every polygon has at least one periodic orbit.

Of course, the unfolding principle works for other kinds of tables as well. Here is an equilateral triangle as a billiards table.

<video controls loop autoplay muted width="600">
  <source src="/assets/triangle_billiards.mp4" type="video/mp4">
</video>

And here is one for a regular hexagon.

<video controls loop autoplay muted width="600">
  <source src="/assets/hexagon_billiards.mp4" type="video/mp4">
</video>

I've been choosing polygons that give tilings of the plane but we don't have to do so. There's no problem with the reflected images overlapping with each other in the visualization, so long as its understood that there's not "real" overlap in the actual dynamical system. But one could also define a topological space of the unfolding to form a Riemann surface.
