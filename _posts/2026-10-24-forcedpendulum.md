---
title: 'A Pendulum with Forcing and Damping'
date: 2026-10-24
permalink: /posts/2026/10/forcedpendulum/
tags:
  - classical mechanics
  - dynamical systems
---

Let's consider a single pendulum system with forcing and damping terms. Once the pendulum rod length is fixed, the only parameter needed to describe the position is the angle $\theta$ the pendulum makes with some reference ray and the once the mass is normalized to 1, we only need the angular velocity for the momentum. Without any external forces at all and only initial conditions, we can think of a pendulum as a 2nd order oscillator $\ddot{\theta} = -\omega_0 \sin(\theta)$; note that the term on the right only depends on $\theta$. Damping is the appearance of the term $\dot{\theta}$ with some factor and an external force is a term that depends on time $t$. For us, we'll focus on an example with damping and periodic forcing:

$$\ddot{\theta} = -\omega_0\sin\theta-b\dot{\theta} +F\cos(\omega_d t).$$

Writing $\nu=\dot{\theta}$, we obtain the first-order system

$$\begin{aligned}
\dot{\theta}&=\nu,\\
\dot{\nu}&=-\omega_0\sin\theta-b\nu
+F\cos(\omega_d t)
\end{aligned}$$

<video controls loop autoplay muted width="600">
  <source src="/assets/driven_pendulum_20.mp4" type="video/mp4">
</video>

<video controls loop autoplay muted width="600">
  <source src="/assets/driven_pendulum_20wrapped.mp4" type="video/mp4">
</video>
