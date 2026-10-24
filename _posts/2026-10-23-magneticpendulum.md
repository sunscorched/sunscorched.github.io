---
title: 'A Magnetic Pendulum and Basins of Attraction'
date: 2026-10-23
permalink: /posts/2025/12/magneticpendulum/
tags:
  - classical mechanics
  - electromagnetism
  - dynamical systems
---

Consider a pendulum with an iron bob which freely swings from a string, rather than a rod with a hinge. It can swing backwards and forwards but also left and right, and anything in between: it has 2 degrees of freedom. We may place magnets on the ground beneath the pendulum which attracts the iron bob. The magnets could have different strengths of attractive forces and could be placed in many configurations. Then, we'd have a very interesting dynamical system when we move the iron bob to a particular initial position and then let the pendulum swing freely. If the magnets are strong enough, the iron bob can be attracted to then eventually hover above one of the magnets but it's not easy to predict which one based only on the initial position or even first few moments of the trajectory. In this sense, this magnetic pendulum system is similar to a 3 body celestial system with a small satellite orbiting (or possibly crashing) around them. I'm introducing the magnetic pendulum system because you can make a model of it at home with some magnets and string.

It can be great fun to animate the dynamics as has been done many times on YouTube but I figured it could be fun to implement in Python with the help of AI. For simplicity, we'll assume the magnets are all of equal strength and arranged in an equilateral triangle. Here is a particular initial position where for a short time, the pendulum appears to be attracted to the top magnet but then is attracted to the left magnet. We can also bring in initial velocities but for our purposes, we'll only consider initial positions.

<video controls loop autoplay muted width="600">
  <source src="/assets/magnetic_pendulum_single.mp4" type="video/mp4">
</video>

Here is an animation with many initial positions for the pendulum. Note that some of them are close to each other but end up attracted to different magnets. Indeed, this is an example of a **chaotic system** since small deviations in initial conditions can lead to drastically different paths and final results.

<video controls loop autoplay muted width="600">
  <source src="/assets/magnetic_pendulum_many.mp4" type="video/mp4">
</video>

There are many better rendered images but here is a graphic showing the basins of attraction. That is, we color the plane with three colors. A particular point $p$ in the plane is given the color corresponding to the magnet that the pendulum eventually is attracted to if it begins at point $p$. There are points which would not be given a color as the forces perfectly balance out. For example, the exact barycenter of the three magnets is one such point.

![label](/files/magnetic_pendulum_basins.png)

One can make the system more interesting by having larger/smaller magnets placed in different configurations and also giving the pendulum an initial push. We can also add more magnets and change the length of the string.
