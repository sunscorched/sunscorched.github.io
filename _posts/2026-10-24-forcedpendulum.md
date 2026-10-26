---
title: 'A Pendulum with Forcing and Damping'
date: 2026-10-24
permalink: /posts/2026/10/forcedpendulum/
tags:
  - classical mechanics
  - dynamical systems
---

Let's now consider a pendulum system with forcing and damping terms.

\[
\ddot{\theta}
=-\omega_0\sin\theta-b\dot{\theta}
+F\cos(\omega_d t).
\]

Writing \(\nu=\dot{\theta}\), we obtain the first-order system
\[
\begin{aligned}
\dot{\theta}&=\nu,\\
\dot{\nu}&=-\omega_0\sin\theta-b\nu
+F\cos(\omega_d t).
\end{aligned}
\]

<video controls loop autoplay muted width="600">
  <source src="/assets/driven_pendulum_20.mp4" type="video/mp4">
</video>

<video controls loop autoplay muted width="600">
  <source src="/assets/driven_pendulum_20wrapped.mp4" type="video/mp4">
</video>
