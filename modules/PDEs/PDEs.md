---
layout: default
title: Partial Differential Equations
has_children: true
has_toc: true
nav_exclude: true
---

Most physical phenomena are ultimately described by a relationship
between changing quantities. If only a single quantity such as time is
changing, [Ordinary Differential Equations]({{ site.baseurl }}{% link
modules/ODEs/ODEs.md %}) (ODEs) result. However, as soon as more than a
single quantity varies independently from the other ones, [partial
differential
equations](https://mathworld.wolfram.com/PartialDifferentialEquation.html)
(**PDEs**) have to be solved.

For example, a scalar field $$U(x, y)$$ admits the general second order PDE

$$
A(x, y)\frac{\partial^2 U}{\partial x^2} +
2B(x, y)\frac{\partial^2 U}{\partial x \partial y} +
C(x, y)\frac{\partial^2 U}{\partial y^2} + 
D(x, y)\frac{\partial U}{\partial x} +
E(x, y)\frac{\partial U}{\partial y} +
F(x, y) = 0 
$$

For notational convenience, partial derivatives are often written in subscript notation, so the same general equation reads

$$
A(x, y) U_{xx} +
2B(x, y) U_{xy} +
C(x, y) U_{yy} + 
D(x, y) U_{x} +
E(x, y) U_{y} +
F(x, y) = 0.
$$

## Classes of second-order PDEs

Second-order PDEs (highest partial derivatives are second order, such
as $$U_{xz}$$ or $$U_{tt}$$) are ubiquitous in physics and can be
broadly classified as

* *elliptic* PDEs (discriminant $$AC - B^2 > 0$$, second derivatives of all variables and all with the same sign, e.g., Poisson's equation $$\nabla^2 U(x, y, z)  = U_{xx} + U_{yy} + U_{zz} = -4\pi\rho(x,y,z)$$);
* *parabolic* PDEs ($$AC - B^2 = 0$$, second order derivative of one variable and first order derivative of the other one, e.g., the heat equation $$\nabla^2 U(x, y, z, t) - a \frac{\partial U}{\partial t} = 0$$);
* *hyperbolic* PDEs ($$AC - B^2 < 0$$, second derivatives of all variables with the opposite sign, e.g. wave equation $$\nabla^2 U(x, y, z, t) - c^{-2} \frac{\partial^2 U}{\partial t^2} = 0$$).

## Boundary conditions

PDEs are more complicated than ODEs. General solutions of PDEs involve arbitrary functions and additional *[boundary conditions](https://mathworld.wolfram.com/BoundaryConditions.html)* (values or derivatives of the solution $$U(x,y)$$ on the boundary of the problem domain) have to be specified to obtain a specific solution (in addition to any *initial conditions*).

* *Dirichlet boundary conditions* prescribe the value of the solution on a surrounding closed surface.
* *Neumann boundary conditions* specify the value of the normal derivative on the surrounding surface.
* *Cauchy boundary conditions* set both the value and the normal derivative on the surrounding closed surface (i.e., both Dirichlet and Neumann boundary conditions are imposed).
* *Robin boundary conditions* specify that a weighted sum of Dirichlet and Neumann boundary conditions have to have a given value on the boundary.

Often, no analytic solutions can be found or the analytic solutions are unwieldy. PDEs can be solved numerically, though. However, different types of PDEs require customized algorithms.
