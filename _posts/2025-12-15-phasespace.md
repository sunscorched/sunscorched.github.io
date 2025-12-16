---
title: 'Visualizing Phase Spaces'
date: 2025-12-15
permalink: /posts/2025/12/phasespace/
tags:
  - symplectic geometry
  - classical mechanics
---

Consider a simple swinging pendulum. One way to describe its physical state is to use an angle to describe its position with respect to the vertical (where it is located when at rest) and to also give a number describing its angular velocity. The space of all configurations, also called a **phase space**, is $S^1 \times \mathbb{R}$ since the circle $S^1$ describes the angles and the real numbers describe the angular velocity. This space is also known as the cotangent bundle $T^* S^1$. Similarly, we can also consider a double pendulum with two rods and angular velocity for each. The pair of angles together live in a torus $T^2 = S^1 \times S^1$ and the pair of angular velocities live in $\mathbb{R}^2$. This phase space is also known as the cotangent bundle $T^* T^2$. The double pendulum is known to be chaotic; here is an animation depicting this. The plot on the right looks to be a square but we identify the opposite edges to form a torus.

<video controls loop autoplay muted width="600">
  <source src="/assets/double_pendulum.mp4" type="video/mp4">
</video>

In this simulation, we only have the force of gravity. We make the simplifying assumption that no energy is lost to friction. The trail left by the pendulum looks somewhat patterned at first but eventually moves chaotically and the path in the position space $T^2$ looks like scribbles. Note that when one of the rods makes a full revolution, the path in the square looks to jump from one side to the other but we mustn't forget that opposite edges should be "glued" together. It's a bit like the game of Pacman.


<video controls loop autoplay muted width="600">
  <source src="/assets/foucault_pendulum.mp4" type="video/mp4">
</video>
