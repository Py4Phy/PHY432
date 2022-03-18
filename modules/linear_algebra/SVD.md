---
layout: default
title: Singular Value Decomposition
parent: Linear Algebra
nav_exclude: true
---

Sometimes the calculation of a matrix inverse is numerically difficult
or it is not defined (if the matrix is not invertible). In this
situation it can still make sense to calculate a *pseudo
inverse*. This pseudo inverse can be obtained from **singular value
decomposition** or **SVD**.

### SVD

The **singular value decomposition** ("SVD") of a matrix

\begin{gather}
\mathsf{A} = \mathsf{U} \mathsf{W} \mathsf{V}^{T}
\end{gather}

is always possible with three matrices having the following
properties: $$\mathsf{W} = \mathrm{diag}(w_j), \ 1 \leq j \leq N,$$ is a
diagonal matrix and the other matrices are orthogonal
$$\mathsf{U}\mathsf{U}^{T} = \mathsf{V} \mathsf{V}^{T} =
\mathsf{1}$$).[^1]

The $$w_j$$ are called the [singular
values](https://mathworld.wolfram.com/SingularValue.html). The rank of
the matrix is the dimension of the matrix minus the number of
occurences of $$w_j = 0$$, which indicate the number of linearly
dependent components.

### Matrix inverse with SVD

Sometimes you want to explicitly find the **inverse of a matrix**,
$$\mathsf{A}^{-1}$$ that is not actually invertible. For such
*singular* matrices (i.e., $$\det\mathsf{A} = 0$$) one can still obtain a useful
equivalent of the inverse, $$\mathsf{W}^{-1}$$, through SVD.

For non-singular matrices

\begin{gather}
\mathsf{A}^{-1} =
  \mathsf{V}\, \mathrm{diag}\left(\frac{1}{w_j}\right) \, \mathsf{U}^{T}
\end{gather}

but even for singular matrices

\begin{gather}
\mathbf{x} = \mathsf{V} \mathsf{W}^{-1} \mathsf{U}^{T}\, \mathbf{b}
\end{gather}

will be a useful answer, provided that $$\mathsf{W}^{-1}$$ is
**augmented**, i.e., any values where $$w_j = 0$$ are also set to 0 in
$$\mathsf{W}^{-1}$$, in effect making the replacement $$\frac{1}{0}
\rightarrow 0$$ (which projects out the linearly dependent subspaces).

- For a $$N \times N$$ matrix, values $$w_j = 0$$ indicate precisely
  where $$\mathsf{A}$$ is singular and very small $$w_j$$ also alert
  you to possible numerical problems (the solution might easily become
  dominated by round-off error and the matrix is said to be
  "ill-conditioned").
- For an overdetermined system (more equations than unknowns[^2])
  $$\mathbf{x}$$ solves the **least-squares fitting problem** and
  determines the solution that minimizes the deviation in the
  least-squares sense.
- For an underdetermined system (fewer equations than unknowns[^3]) it
  can be used to find all the vectors that span the solution space.

## Numerical solution

Efficient algorithms exist to solve these problems and we will
primarily use the optimized algorithms in the
[numpy.linalg](https://docs.scipy.org/doc/numpy/reference/routines.linalg.html)
package:
{% highlight python %}
import numpy.linalg
{% endhighlight %}

For most linear algebra work you should be using *double precision*
because diagonalization routines and eigenvalue solvers have
problems with nearly singular matrices and the better the machine
precision is, the better one can distinguish a nearly singular matrix
from a truly singular one.

## Class material


The notebook
[13_SVD.ipynb]({{ site.nbviewer.resources }}/13_linear_algebra/13_SVD.ipynb)
shows the principles and applications of **SVD** (with skeleton code
in [13_SVD-Students-1.ipynb]({{ site.nbviewer.resources }}/13_linear_algebra/13_SVD-Students-1.ipynb)).


#### Additional resources:

* [13_SVD notebook (PDF)]({{ site.resources.fileurl }}/13_linear_algebra/13_SVD.pdf)
* _[Numerical Recipes in C](http://apps.nrbook.com/c/index.html)_, WH
  Press, SA Teukolsky, WT Vetterling, BP Flannery. 2nd
  ed, 2002. Cambridge University Press. Chapter **2**.


--------

#### Footnotes

[^1]: For singular matrices, some elements on the diagonal of
      $$\mathsf{W}$$ are zero so in order to form the pseudo-inverse
      $$\mathsf{W}^{-1} = \mathrm{diag}(1/w_j)$$ these elements have
      to be augmented and replaced by zero in $$\mathsf{W}^{-1}$$.

[^2]: The *overdetermined system* has more equations $$M$$ than unknowns
      $$N$$, $$M > N$$, i.e., the solution vector $$\mathbf{x}$$ has
      $$N$$ elements but the matrix $$\mathsf{A}$$ now has the shape
      $$M \times N$$.

[^3]: The *underdetermined* system does not typically have a unique
      solution because is has $$M < N$$.

