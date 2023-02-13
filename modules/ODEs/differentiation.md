---
layout: default
title: Differentiation
parent: Ordinary Differential Equations
nav_exclude: true
nav_order: 0
---

Taking numerical derivatives is based on the elementary definition

$$
\frac{dy(t)}{dt} := \lim_{h\rightarrow 0} \frac{y(t+h) - y(t)}{h}
$$

We will then derive different finite difference approximations to the
derivative and assess their error.

## Class material

You can follow the lecture in the slides
[09-differentiation-theory.ipynb]({{ site.nbviewer.slides }}/09_differentiation/09-differentiation-theory.ipynb).

### <span class="label" style="background: black">Activity</span>Error analysis of differentiation algorithms

In this activity you will implement different finite difference
algorithms for numerical differentiation. You will then analyze how
the algorithmic [error]({{ site.baseurl }}{% link
modules/fundamentals/errors.md %}) depends on the spacing $$dt$$ that you use
to evaluate the derivative. As you will see, there is a point when
numerical (floating point representation) errors limit the achievable accuracy.


## Additional resources

* _Computational Physics_: Ch 5.1 -- 5.6
* If you are interested in *integration* then see
  [the lectures on integration in 2016](https://asu-compmethodsphysics-phy494.github.io/ASU-PHY494-2016/2016/02/09/07_Integration/).




