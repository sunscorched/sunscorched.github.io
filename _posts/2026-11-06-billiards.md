---
title: 'Billiards'
date: 2026-11-06
permalink: /posts/2026/11/billiards/
tags:
  - dynamical systems
---

"Polygonal billiards is the study of Newtonian motion of a point inside a polygon." - Paul Seidel. We typically assume that all collisions are completely inelastic and there is no friction so that the trajectory of the ball can go on indefinitely. When the ball hits a wall, it comes in at some angle measured between the trajectory line and the wall. We have some choices here so we'll always choose to work with an angle $\alpha$ between 0 and $\pi/2$. The ball then reflects off of the wall such that the angle of the outgoing ray and the wall is also $\alpha$. If the ball hits a vertex of the polygon, we'll say that the trajectory after that is undefined.

Of course, one could track the trajectory via careful angle measurements and precisely drawn diagrams. But there is a useful method called **unfolding.** When the ball hits the edge, we reflect the whole table across that edge. The outgoing trajectory also gets reflected and thus, in the unfolded diagram, the trajectory is simply a straight line. You can work out the angles to convince yourself that the trajectory would be a straight line.

Let's begin with a simple example of a square billiard table. Note that whenever the ball bounces on the left, there is wall-crossing on the right.

<video controls loop autoplay muted width="600">
  <source src="/assets/square_billiards.mp4" type="video/mp4">
</video>

In this square grid, let's suppose it has side length normalized to 1. If the starting coordinates of the ball are rational and the slope of the trajectory is also rational, then the trajectory will eventually lead the ball to its starting point. These are called **periodic** trajectories. Below is one such example 

<video controls loop autoplay muted width="600">
  <source src="/assets/periodic_billiards.mp4" type="video/mp4">
</video>

<video controls loop autoplay muted width="600">
  <source src="/assets/triangle_billiards.mp4" type="video/mp4">
</video>

<video controls loop autoplay muted width="600">
  <source src="/assets/hexagon_billiards.mp4" type="video/mp4">
</video>
