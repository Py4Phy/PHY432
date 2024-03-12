---
title: Week 8 Announcement
week: 8
date: 2024-03-12
---

With the *RK4* and the *velocity Verlet* integrator we now know two
good integration algorithms for different situations. Verlet will be
useful for solving the common problem of integrating Newton's (or rather
Hamilton's) equations of motion due to its good energy
conservation. RK4 is an all-round integrator that we can use for
general coupled ODEs. 

We will study a few **applications**. You will use the Verlet
integrator to discover Neptune by **simulating the anomaly in Uranus'
orbit due to Neptune** (homework). In class we will **simulate a baseball
throw**. We will first look at the simple case of only including air
resistance (i.e., a drag force) and then add spin, which, through the
*Magnus force*, will allow us to generate curve ball trajectories.

Optionally, you can also learn more about **molecular dynamics**
simulations, a standard method to model large numbers of interacting
particles.
