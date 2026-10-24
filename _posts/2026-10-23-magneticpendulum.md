---
title: 'Magnetic Pendulum and Basins of Attraction'
date: 2026-10-23
permalink: /posts/2025/12/magneticpendulum/
tags:
  - classical mechanics
  - electromagnetism
  - dynamical systems
---

Consider a pendulum with an iron bob which freely swings from a string, rather than a rod with a hinge. It can swing backwards and forwards but also left and right, and anything in between: it has 2 degrees of freedom. We may place magnets on the ground beneath the pendulum which attracts the iron bob. The magnets could have different strengths of attractive forces and could be placed in many configurations. Then, we'd have a very interesting dynamical system when we move the iron bob to a particular initial position and then let the pendulum swing freely. If the magnets are strong enough, the iron bob can be attracted to then hover above one of the magnets. This system is not unlike a 3 body celestial system with a small satellite orbiting (or possibly crashing).

It can be great fun to animate the dynamics as has been done many times on YouTube but I figured it could be fun to implement in Python with the help of AI. For simplicity, we'll assume the magnets are all of equal strength and arranged in an equilateral triangle.


<video controls loop autoplay muted width="600">
  <source src="/assets/magnetic_pendulum_single.mp4" type="video/mp4">
</video>

Here is an animation with many initial positions. Note that some of them are close to each other but end up attracted to different magnets.

<video controls loop autoplay muted width="600">
  <source src="/assets/magnetic_pendulum_many.mp4" type="video/mp4">
</video>

Here is a graphic showing the basins of attraction.

![label](/files/magnetic_pendulum_basins.png)
