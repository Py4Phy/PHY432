---
layout: default
title: "Poisson's and Laplace's equation"
parent: Partial Differential Equations
nav_exclude: true
nav_order: 0
---


<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Poisson's equation ##

The electrostatic potential $$\Phi(\mathbf{r})$$ is related to the
charge density $$\rho(\mathbf{r})$$ through **Poisson's equation**

$$
\boldsymbol{\nabla}^2 \Phi = -4\pi\rho
$$

a *hyperbolic PDE*. In Cartesian coordinates it reads

$$
\frac{\partial^2 \Phi(x, y, z)}{\partial x^2} + \frac{\partial^2
\Phi(x, y, z)}{\partial y^2} + \frac{\partial^2 \Phi(x, y,
z)}{\partial z^2} = -4 \pi \rho(x,y,z).
$$

If no charges are inside the domain boundaries, Poisson's equation
reduces to **Laplace's equation**

$$
\frac{\partial^2 \Phi}{\partial x^2} + \frac{\partial^2
\Phi}{\partial y^2} + \frac{\partial^2 \Phi}{\partial z^2} = 0.
$$

We can solve either equation if we are either given the value of the
potential on the boundary or the electric field on the boundary normal
to the surface.


## Solving Poisson's equation numerically

We will look at various [finite difference]({{ site.baseurl }}{% link
modules/ODEs/differentiation.md %}) schemes (both explicit and
implicit) to solve the different classes of PDEs on discretized grids
in space and time. For Poisson's equation, we will introduce a simple
*iterative scheme* to successively improve an initial (poor) guess for
the solution. The most simple of these iterative algorithms is the
*Jacobi method* that updates the value of the potential (here in 2D)
at grid point $$(i, j)$$ as the average of the neighbors,

$$
\Phi_{i,j} = \frac{1}{4}\Big(\Phi_{i+1,j} + \Phi_{i-1,j} + \Phi_{i,j+1} + \Phi_{i,j-1}\Big)
     + \pi\rho_{i,j} \Delta^2
$$

where $$\Delta$$ is the spacing between grid points in the $$x$$ and
$$y$$ direction.

We start with $$\Phi_{i,j} = 0$$ inside the domain boundaries and the
potential defined on the boundary itself.

In Python, the Jacobi update looks very similar
```python
Phi[1:-1, 1:-1] = 0.25*(Phi[2:, 1:-1] + Phi[0:-2, 1:-1] + \
                        Phi[1:-1, 2:] + Phi[1:-1, 0:-2]) + \
                        np.pi * rho[1:-1, 1:-1] * \Delta**2
```
where we made use of NumPy slicing and element-wise operations (as
explained in [numpy_arrays.ipynb]({{ site.nbviewer.resources }}/14_PDEs/numpy_arrays.ipynb)).

### Visualization of iterative solutions

The movies show how the solutions of simple 2D electrostatic problems
relax to the converged solution (using successive over-relaxation
with the Gauss-Seidel algorithm), namely a box with one side at 100 V
and three sides at 0 V (left) and the same box with an additional
charge dipole included (right).

<video width="350.0" height="350.0" controls autoplay loop>
<source type="video/quicktime" src="{{ site.baseurl }}{% link
assets/movies/wire_SOR_3d.mov %}" />
  Your browser does not support the video tag. You can find the video
  file at [{{ site.baseurl }}{% link assets/movies/wire_SOR_3d.mov %}]({{
  site.baseurl }}{% link assets/movies/wire_SOR_3d.mov %}) .
</video>

<video width="350.0" height="350.0" controls autoplay loop>
<source type="video/quicktime" src="{{ site.baseurl }}{% link
assets/movies/dipole_wire_SOR_3d.mov %}" />
  Your browser does not support the video tag. You can find the video
  file at [{{ site.baseurl }}{% link
  assets/movies/dipole_wire_SOR_3d.mov %}]({{ site.baseurl }}{%link
  assets/movies/dipole_wire_SOR_3d.mov %}) .
</video>



## Class material

1. [14_PDEs-1.ipynb]({{ site.nbviewer.resources }}/14_PDEs/14_PDEs-1.ipynb):
   Poisson's and Laplace's equation: Background
   ([board notes on PDEs (PDF)]({{ site.resources.fileurl }}/14_PDEs/14_PDEs-1-LectureNotes.pdf)),
   Gauss-Seidel algorithm, problems:
   [14_PDEs-1-Students.ipynb]({{ site.nbviewer.resources }}/14_PDEs/14_PDEs-1-Students.ipynb) [^1]
2. [14_PDEs-2.ipynb]({{ site.nbviewer.resources }}/14_PDEs/14_PDEs-2.ipynb)
   [^1]:
   fast Jacobi, Gauss-Seidel and Successive Over Relaxation algorithms
   (using NumPy array operations, see
   [board notes on numpyfied Poisson solvers
   (PDF)]({{ site.resources.fileurl }}/14_PDEs/14_PDEs-2-LectureNotes.pdf))
   and how to replace slow Python loops with fastnumpy array
   operations ([numpy_arrays.ipynb]({{ site.nbviewer.resources }}/14_PDEs/numpy_arrays.ipynb)),
   Poisson equation, charge density:
   [14_PDEs-2-Students.ipynb]({{ site.nbviewer.resources }}/14_PDEs/14_PDEs-2-Students.ipynb) [^1]
3. When plotting arrays of data with
   [matplotlib](https://matplotlib.org), one sooner or later one needs
   to use the
   [`numpy.meshgrid()`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.meshgrid.html)
   function which "returns coordinate matrices from coordinate
   vectors"---most users find this function mystifying. The notebook
   [meshgrid.ipynb]({{ site.nbviewer.resources }}/14_PDEs/meshgrid.ipynb)
   makes a bit clearer, _what_ `meshgrid` does and why it is useful.


#### Additional resources  ####

* _Computational Physics_, Ch **19--23**
* _[Partial differential equation](http://www.scholarpedia.org/article/Partial_differential_equation)_, Andrei D. Polyanin et al. (2008), Scholarpedia, 3(10):4605. doi: [10.4249/scholarpedia.4605](http://doi.org/doi:10.4249/scholarpedia.4605)
* _[Numerical Recipes in C](http://apps.nrbook.com/c/index.html)_, WH
  Press, SA Teukolsky, WT Vetterling, BP Flannery. 2nd
  ed, 2002. Cambridge University Press. Chapter **19**.


--------

#### Footnotes

[^1]:

     As usual, `git pull` the resources repository
     [{{ site.resources.shortname }}]({{ site.resources.url }}) to get a
     local copy of the notebook. Then **copy the notebook and all other
     code into your work directory** in order to complete the exercises.
