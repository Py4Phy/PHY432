---
layout: default
title: Standard Form of ODEs
parent: Ordinary Differential Equations
nav_exclude: true
nav_order: 2
---

We will introduce a general formalism for representing systems of
coupled [ODEs]({{ site.baseurl }}{% link modules/ODEs/intro_ODEs.md %}) as
vector functions. This formalism will make it easy to write
integration algorithms for ODEs of any order.

The Jupyter notebook [10-ODEs.ipynb]({{ site.nbviewer.slides
}}/10_ODEs/10-ODEs.ipynb#/) contains the lecture notes.


<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Euler's rule as an integrator

We learn about the basic ideas behind integration algorithms, using
the simple *Euler* algorithm as an example. It can be derived from the
forward difference operator (see the lesson on [differentiation]({{
site.baseurl }}{% link modules/ODEs/differentiation.md %})):

\begin{align}
f(t, y) = \frac{dy(t)}{dt} &\approx \frac{y(t_{n+1}) - y(t_n)}{h}\\\\\\
y_{n+1} &\approx y_n + h f(t_n, y_n) \quad \text{with} \quad y_n := y(t_n)
\end{align}

(The simple Euler algorithm is a bad integrator for many reasons but
it is educational to work with it and it is used, for instance, in
computer games for "physics engines" where speed is more important
than accuracy, unlike *our* applications in science, where correctness
has the highest priority.)


## Standard Form of ODEs

We introduce the formalism for
representing [coupled ordinary differential equations]({{ site.baseurl
}}{% link modules/ODEs/ODEs.md %}) in a general form, the general or
**standard form**.

One ODE of *any order* \\(n\\) \\(\rightarrow\\) \\(n\\) coupled simultaneous
first-order ODEs in \\(n\\) unknowns \\(y^{(0)}, \dots, y^{(n-1)}\\):

\begin{align}
\frac{dy^{(0)}}{dt} &= f^{(0)}(t, y^{(0)}, \dots, y^{(n-1)})\\\\\\
\frac{dy^{(1)}}{dt} &= f^{(1)}(t, y^{(0)}, \dots, y^{(n-1)})\\\\\\
\vdots &  \\\\\\
\frac{dy^{(n-1)}}{dt} &= f^{(n-1)}(t, y^{(0)}, \dots, y^{(n-1)})\\\\\\
\end{align}

and in \\(n\\)-dimensional vector notation:

\begin{align}
\frac{d\mathbf{y}(t)}{dt} &= \mathbf{f}(t, \mathbf{y})\\\\\\
\mathbf{y} &= \left(\begin{array}{c}
  y^{(0)}(t) \\\\\\
  y^{(1)}(t) \\\\\\
  \vdots \\\\\\
  y^{(n-1)}(t)
  \end{array}\right),
\quad
\mathbf{f} = \left(\begin{array}{c}
  f^{(0)}(t, \mathbf{y}) \\\\\\
  f^{(1)}(t, \mathbf{y}) \\\\\\
  \vdots \\\\\\
  f^{(n-1)}(t, \mathbf{y})
  \end{array}\right)
\end{align}


### Euler's rule (standard form)
Given the \\(n\\)-dimensional vectors from the ODE standard form

\begin{equation}
\frac{d\mathbf{y}}{dt} = \mathbf{f}(t, \mathbf{y})
\end{equation}

the **Euler rule** amounts to

\begin{align}
\mathbf{f}(t, \mathbf{y}) = \frac{d\mathbf{y}(t)}{dt} &\approx \frac{\mathbf{y}(t_{n+1}) - \mathbf{y}(t_n)}{\Delta t}\\\\\\
\mathbf{y}_{n+1} &\approx \mathbf{y}_n + \Delta t \mathbf{f}(t_n, \mathbf{y}_n) \quad \text{with} \quad \mathbf{y}_n := \mathbf{y}(t_n)
\end{align}

Translated to Python
```python
# initial conditions
x0, v0 = 0.0, 1.0
y[:] = x0, v0

for i, t in enumerate(t_range):
    # Euler integrator
    y[:] = y + h * f(t, y)
```	

## Resources ##

* _Computational Modelling_: Chapter **2**
* _Computational Physics_: Chapter **9**
* Weisstein, Eric
  W. ["Ordinary Differential Equation."](http://mathworld.wolfram.com/OrdinaryDifferentialEquation.html)
  From MathWorld — A Wolfram Web Resource.
* _[Numerical Recipes in C](http://apps.nrbook.com/c/index.html)_, WH
  Press, SA Teukolsky, WT Vetterling, BP Flannery. 2nd
  ed, 2002. Cambridge University Press. Chapter **16**.


