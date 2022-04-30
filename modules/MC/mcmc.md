---
layout: default
title: Markov Chain Monte Carlo
nav_exclude: true
---

Monte Carlo methods are used widely to simulate complex systems. As an
example we will look at a model for ferromagnetism, the [Ising
model](https://en.wikipedia.org/wiki/Ising_model). 

![Metropolis Monte Carlo Simulation of the 2D Ising model at temperature kT/epsilon =
2.2]({{ site.resources.rawurl }}/17_MonteCarlo/figs/ising2d_kT2.2.png)

<small>MCMC Simulation of the 2D Ising model at temperature $$kT/\epsilon =
2.2$$. Left: up/down spin distribution. Middle: Average energy per
spin as function of MC step. Right: Average magnetization over simulation.</small>

## Quick introduction to statistical mechanics

Important concepts

* microstates and macrostates
* macroscopic observables
* temperature and heat baths
* equilibrium
* Boltzmann distribution, state probabilities $$P(E_n) = Z^{-1} \exp(-\beta E_n)$$, relative probabilities
  are related by the Boltzmann factor of the energy difference
  $$p_2/p_1 = \exp\big(-\beta(E_2 - E_1)\big)$$
* partition function $$Z = \sum_n \exp(-\beta E_n)$$

## Metropolis MC sampling for the Ising model

Naïve importance sampling is hopeless because the state space is too
large. The solution is the **Metropolis algorithm**

* trial moves that ensure that the whole state space can be reached (single spin flip for a randomly chosen spin)
* Metropolis criterion for the acceptance probability $$p_\text{accept}
  = \min\big(1, \exp(-\beta \Delta E)\big)$$
* calculation of the energy difference  
* implementation of the acceptance step using random numbers with rejection sampling

The Metropolis algorithm can be viewed as a [Markov
Chain](https://en.wikipedia.org/wiki/Markov_chain) generator that
reproduces the correct Boltzmann distribution.

## 1D and 2D Ising model in Python

Object-oriented implementation of the [SpinChain]({{
site.resources.url }}/17_MonteCarlo/ising_1d.ipynb) and
[SpinLattice](({{ site.resources.url }}/17_MonteCarlo/ising_2d.ipynb))
that use Metropolis MC sampling to simulate the equilibrium state of
the 1D and 2D Ising model at finite temperature. The basic data
structure is a NumPy array that records spins with integers +1 or -1
and an update method that flips spins according to the Metropolis
criterion. Auxiliary methods to run a simulation, to calculate
averages, and to plot results are included to aid in interactive
exploration of the Ising model.

We discuss the average energy and magnetization per spin as a function
of temperature. No phase transition is observed in 1D. In 2D a phase
transition near the theoretical critical temperature is visible. The
simulated curves agree well with the analytical solutions for the 1D
and 2D Ising model.

![MCMC simulation of 2D Ising model: average energy compared to
theoretical exact
solution]({{ site.resources.rawurl }}/17_MonteCarlo/figs/ising2d_energy_temperature.png)


<small>MCMC simulation of 2D Ising model: average energy per spin
compared to theoretical exact solution shows good agreement.</small>

![MCMC simulation of 2D Ising model: average magnetization compared to
theoretical exact
solution]({{ site.resources.rawurl }}/17_MonteCarlo/figs/ising2d_magnetization_temperature.png)

<small>MCMC simulation of 2D Ising model: average magnetization per
spin compared to theoretical exact solution indicates the presence of
phase transition between the magnetized phase for $$T<T_c$$ and no
magnetization for $$T>T_c$$.</small>

## Class materials

* [whiteboard lecture notes (PDF)]({{ site.resources.fileurl }}/17_MonteCarlo/17_metropolis_MC_Ising_Model.pdf)
* jupyter notebook **1D Ising model** [ising_1d.ipynb]({{
  site.nbviewer.resources }}/17_MonteCarlo/ising_1d.ipynb)
* jupyter notebook **2D Ising model** [ising_2d.ipynb]({{
  site.nbviewer.resources }}/17_MonteCarlo/ising_2d.ipynb)
  

 
