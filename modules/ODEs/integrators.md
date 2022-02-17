---
layout: default
title: Integrators
parent: Ordinary Differential Equations
has_children: false
nav_exclude: true
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Principles of integrators for ODEs

The first part of this lesson introduced the [formalism and the basic
ideas behind integration algorithms]({{ site.baseurl }}{% link
modules/ODEs/standard_form.md %}).

We revisit the *Euler algorithm* and introduce much better algorithms,
namely the [Runge-Kutta
schemes](#accuracy-and-performance-of-euler-and-runge-kutta-integrators)
and the [Verlet integrator](#verlet-integrators).

## Accuracy and performance of Euler and Runge-Kutta integrators

The second part shows how to assess the accuracy of integration
algorithms and analyzes in more depth the simple
[Euler integrator](https://en.wikipedia.org/wiki/Euler_method) and the
[Runge-Kutta methods](https://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods),
namely `rk2` and `rk4`. As examples we use the simple 1D
harmonic oscillator with potential energy function $$U(x) =
\frac{1}{2} k x^2$$, an anharmonic oscillator ($$U(x) = \frac{1}{2} k
x^2 (1-\frac{2}{3} \alpha x)$$), and a 6-th power oscillator ($$U(x) =
\frac{1}{6} k x^6$$).

The Jupyter notebook
[10-ODE_integrators.ipynb]({{ site.nbviewer.resources }}/10_ODEs/10-ODE_integrators.ipynb)
contains the lecture notes and implementations are in the module
[integrators.py]({{ site.resources.fileurl }}/10_ODEs/integrators.py).[^4]

## Verlet integrators

The third part introduces a different class of integrators: time
reversible (and symplectic) integrators such as the **velocity
Verlet** algorithm, which have worse accuracy than e.g. RK4 but long
term stability.

* The notebook
  [10-ODE-integrators-verlet.ipynb]({{ site.nbviewer.resources }}/10_ODEs/10-ODE-integrators-verlet.ipynb)
  implements the *velocity Verlet* algorithm and shows how to use it
  to calculate the orbit of the Earth around the sun.



## Resources ##

* _Computational Modelling_: Chapter **2**
* _Computational Physics_: Chapter **9**
* [scipy.integrate](https://docs.scipy.org/doc/scipy/reference/integrate.html)
  for high performance integration algorithms for Python, in
  particular see
  [scipy.integrate.odeint()](https://docs.scipy.org/doc/scipy/reference/generated/scipy.integrate.odeint.html)
  and
  [scipy.integrate.ode()](https://docs.scipy.org/doc/scipy/reference/generated/scipy.integrate.ode.html#scipy.integrate.ode).
* Weisstein, Eric
  W. ["Ordinary Differential Equation."](http://mathworld.wolfram.com/OrdinaryDifferentialEquation.html)
  From MathWorld — A Wolfram Web Resource.
* _[Numerical Recipes in C](http://apps.nrbook.com/c/index.html)_, WH
  Press, SA Teukolsky, WT Vetterling, BP Flannery. 2nd
  ed, 2002. Cambridge University Press. Chapter **16**.


------------------------------------------------------------

## Footnotes


[^4]:

     As usual, `git pull` the resources repository
     [{{ site.resources.shortname }}]({{ site.resources.url }}) to get a
     local copy of the notebook. Then **copy the notebook and all other
     code into your work directory** in order to complete the exercises.
