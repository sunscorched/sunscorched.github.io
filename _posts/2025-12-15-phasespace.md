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

In this simulation, we only have the force of gravity. We make the simplifying assumption that no energy is lost to friction. Thus, sometimes the rods swing in a way where the energy in the two rods work against each other while other times, they work together and with gravity to really speed up the motion iin ways that defy our usual intuitions. The trail left by the pendulum looks somewhat patterned at first but eventually moves chaotically and the path in the position space $T^2$ looks like scribbles. Note that when one of the rods makes a full revolution, the path in the square looks to jump from one side to the other but we mustn't forget that opposite edges should be "glued" together. It's a bit like the game of Pacman. Both this animation and the one below were made in Python using matplotlib and related libraries.

We can also consider a spherical pendulum which is one where the bob is attached to a fixed rod but has an extra degree of freedom. The phase space for this system is $T^* S^2$. One famous example of a spherical pendulum is the Foucault pendulum. If you don't live on the equator, you can take the pendulum from its rest position, bring it to up (to gain potential energy), and then let go. You might expect it to simply swing back and forth, straight away from you and then straight back (assuming you don't move from the spot where you initially let it go), as if it were swinging on a fixed axis like the simple pendulum. But if you watch for a while, you'll notice that the pendulum's swing precesses: the axis of rotation shifts. This is due to the rotation of the earth! I find it immensely clever that this experimentally verifies that the earth rotates. The higher the latitude, the clearer the precession. In the animation below, I show the Foucault pendulum from a bird's eye view by projecting the trail of the pendulum onto the ground (instead of it having it on the sphere $S^2)$. I've exaggerated the precession but this is something of what it would look like. I also set the latitude to be 60 deg N which is about the latitude of Southern Alaska.

<video controls loop autoplay muted width="600">
  <source src="/assets/foucault_pendulum.mp4" type="video/mp4">
</video>

Unlike the double pendulum animation where I plotted the position part of the phase space, here I show the velocity part. We have a vector which points in the direction of the movement of the pendulum and the length depicts the magnitude/speed of the pendulum. Note that as the pendulum moves to the limits of its reach (the point of one of the legs of the "star"), the velocity vector goes to 0. This is because the pendulum slows down and reverse direction. Despite the path of the pendulum looking to not be smooth, the velocity does change smoothly, hence the trace of the velocity vector giving a smooth flower-looking path. Also, unlike $T^* T^2$, this phase space $T^* S^2$ is not the trivial product $S^2 \times \mathbb{R}^2$. There are many descriptions for this cotangent bundle; here are a few: a smooth affine variety, a Weinstein domain built from a Legendrian unknot, or the collection of all affine rays in $\mathbb{R}^3$.
