---
title: 'A Pendulum with Forcing and Damping'
date: 2026-10-24
permalink: /posts/2026/10/forcedpendulum/
tags:
  - classical mechanics
  - dynamical systems
---

Let's consider a single pendulum system with forcing and damping terms. Once the pendulum rod length is fixed, the only parameter needed to describe the position is the angle $\theta$ the pendulum makes with some reference ray and the once the mass is normalized to 1, we only need the angular velocity for the momentum. The phase space is therefore $S^1 \times \mathbb{R}$ equipped with a symplectic form which allows us to study Hamiltonian dynamics. This space is often thought of as the cotangent bundle of the circle $T^* S^1$. Without any external forces at all and only initial conditions, we can think of a pendulum as a 2nd order oscillator $\ddot{\theta} = -\omega_0 \sin(\theta)$; note that the term on the right only depends on $\theta$. Damping is the appearance of the term $\dot{\theta}$ with some factor and an external force is a term that depends on time $t$. For us, we'll focus on an example with damping and periodic forcing:

$$\ddot{\theta} = -\omega_0\sin\theta-b\dot{\theta} +F\cos(\omega_d t).$$

Here, $F$ is the amplitude of the periodic external driving force which occurs with some frequency related to $\omega_d$
Writing $\nu=\dot{\theta}$, we obtain the 1st order system

$$\begin{aligned}
\dot{\theta}&=\nu,\\
\dot{\nu}&=-\omega_0\sin\theta-b\nu
+F\cos(\omega_d t)
\end{aligned}$$

The usefulness of writing this as a 1st order system is that we can study the critical points and using linear algebra and eigenvalues get a local picture of what happens in the phase space around the critical points. As it turns out, small differences in initial conditions can eventually lead to drastic differences.

Below is an animation with 20 different initial conditions that eventually look very different. We have a plot showing the angular velocity over time, the angle over time, and then evolution in the phase space. This first animation does **not** use $S^1 \times \mathbb{R}$ as the phase space but rather "unrolls" the $\theta$ parameter so that the phase space is $\mathbb{R}^2$. This way, we can see how many times the pendula spin around. Every so often (typically determined by the forcing frequency), we sample a point in phase space to show where the pendulum has evolved to. This gives a set of points which is a discrete and simpler approach to studying dynamics compared to studying the full continuous paths.

<video controls loop autoplay muted width="600">
  <source src="/assets/driven_pendulum_20.mp4" type="video/mp4">
</video>

The animation below is the exact same system but we now wrap the angle $\theta$ so that the phase space is $T^* S^1$.

<video controls loop autoplay muted width="600">
  <source src="/assets/driven_pendulum_20wrapped.mp4" type="video/mp4">
</video>
