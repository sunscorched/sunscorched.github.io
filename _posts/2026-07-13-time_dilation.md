---
title: 'Time Dilation and Length Contraction'
date: 2026-07-13
permalink: /posts/2026/07/timedilation/
tags:
  - special relativity
  - physics
---

I have written about length contraction [elsewhere](https://sunscorched.github.io/posts/2023/07/relativity/) but the topic of time dilation is certainly related. In general, the unifying concept is that of Lorentz transforms and the Poincaré group action. Indeed, it can be confusing to know when the time dilation and length contraction formulas apply, depending on how the different frames of reference are set up. The safer thing to do is use Lorenz transformations.

Let's recall the two postulates of special relativity which I'll word in a slightly different way:
1. If a physical experiment is conducted in two different inertial frames but all relevant aspects of the experiment are the same, the observed results will also be the same. That is, the laws of physics behave the same way in every inertial frame but of course, the observation has to be made in the same frame as the experiment.
2. The speed of light is always measured to be the same in every inertial frame.

In special relativity, spacetime is modeled on the Minkowski space $(\mathbb{R}^4,g)$ where the metric $g$ has signature $(-+++)$. Thus, the isometries are the **Lorentz group** $O(3,1)$. The "unit sphere" in this setting satisfies the equation $x^2+y^2+z^1 = 1+t^2$ which forms a hyperboloid. We may replace the 1 with any $r^2$ and if $r=0$, then we have the special scenario of the **light cone.** Because speed is a ratio of distance and time, if the speed of light is always constant, then we might suspect that sometimes distances and time are actually changing in an intrinsic way.


Let $\gamma^{-1} = \sqrt{1-\frac{v^2}{c^2}}$ where $v$ is the speed of the object and $c$ the speed of light. Below, we'll have $E$ be the earth and $\mu$ represent muons.

Time dilation: $\Delta t_E = \gamma\Delta t_\mu$

Length contraction: $L_\mu = \gamma^{-1} L_E$

## Case Study: Gamma Rays and Muons

I learned about this from [MinutePhysics](https://www.youtube.com/watch?v=rVzDP8SMhPo). One of the experiments we can run on the surface of the earth is seeing what particles are created from highly energetic gamma rays coming from space, colliding with atmospheric molecules. Among the particles are muons which we can also create in the lab. In the lab setting, we measure that muons have a half-life of about $1.5 \mu s$ (microseconds) and an average life expectancy of $2.2 \mu s$. In this time, light travels about 660 meters.

So how is it that the muons produced high in our atmosphere can reach us before they decay? The answer is due to special relativity. The muons are traveling very fast, almost the speed of light at say, $0.99995c$. At such speeds, $2.2 \mu s$ for them is about $220 \mu s$ for us and light can travel 66 kilometers in that time.

From the muon's perspective, they still only experience $2.2 \mu s$ so why don't they decay before reaching us? From their perspective, the distance between them and the surface of the earth gets contracted. At $0.99995c$, 50 kilometers of atmosphere is contracted to about 500 meters.

