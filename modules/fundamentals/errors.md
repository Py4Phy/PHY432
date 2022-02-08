---
layout: default
title: Errors
nav_exclude: true
---

When working with numerical code, one has to be aware of the
limitations imposed by the [representation of numbers in the
computer]({{ site.baseurl }}{% link modules/fundamentals/numbers.md %}) and
the [numerical errors](#errors) that algorithms invariably accumulate.


## Errors

Algorithms (especially those that involve floating point numbers)
generally accumulate errors. The key insight is that the total error
consists of an algorithmic error (also known as the *approximation
error*), which typically decreases with increasing the computational
cost and a *round-off error*, which increases with the number of
operations or the computational cost.

## Class material

### Lecture

You can follow the lecture in the notebook
[08-errors.ipynb]({{ site.nbviewer.resources }}/08_errors/08-errors.ipynb).



### <span class="label" style="background: gray">Example</span> Sine Series

We will analyze the error of the sine function implementation in
[erroranalysis/sine-series-erroranalysis-students.ipynb]({{
site.nbviewer.resources
}}/08_errors/erroranalysis/sine-series-erroranalysis-students.ipynb). (The
full solution is available as
[erroranalysis/sine-series-erroranalysis.ipynb]({{
site.nbviewer.resources
}}/08_errors/erroranalysis/sine-series-erroranalysis.ipynb).)


## Additional resources for Errors

* _Computational Physics_: Chapter **3**

