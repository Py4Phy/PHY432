---
title: Week 10 Announcement
week: 10
date: 2024-03-25
---

A lot of physics can be formulated in the language of **linear
algebra** with vectors and matrices. Examples are problems in solid
body mechanics and quantum mechanics. Three commonly encountered
requirements are to find solutions to a matrix equation $$\mathsf{A}
\mathbf{x} = \mathbf{b}$$, finding the inverse of a matrix
$$\mathsf{A}^{-1}$$, and solving the eigenproblem $$\mathsf{A}
\mathbf{v}_i = \lambda_i \mathbf{v}_i$$. Instead of writing our own
solvers, we will learn how to use the routines in
[numpy.linalg](https://numpy.org/doc/stable/reference/routines.linalg.html),
NumPy's linear algebra module, which provides efficient and
well-tested algorithm.

A matrix solver is also needed for generalizing the *Newton-Raphson*
[root finding algorithm from the last module]({{ site.baseurl }}{%
link modules/root_finding/Root_finding.md %}) to arbitrary
dimensions. We will develop a general Newton-Raphson solver (and also
learn how to calculate the Jacobian using partial derivatives, based
on the central difference algorithm from the [lesson on
differentiation](modules/ODEs/differentiation.md)).
