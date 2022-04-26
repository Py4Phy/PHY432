---
layout: default
title: Monte Carlo integration
nav_exclude: true
---

In many cases the best description of nature considers its stochastic,
random character. In particular, statistical mechanics is built on the
idea that insight does not require precise knowledge about all
particles in a system but only their average behavior and their
probability distributions. Calculation of experimental observables
ultimately comes down to obtaining averages of the form

\begin{equation}
\langle f \rangle = \int_a^b f(x) P(x) dx
\end{equation}

where $$P(x)$$ is the probability distribution of random variable $$x$$
and $$f(x)$$ is an "estimator" function.

We already encountered random behavior in the [stochastic
dynamics]({{ site.baseurl }}{% link
modules/scientific_python/stochastic_dynamics.md %}) of Brownian
motion.

This lesson is a brief introduction to **Monte Carlo methods**, which
rely on [pseudo-random
numbers](https://en.wikipedia.org/wiki/Pseudorandom_number_generator).

## Random number generation

In Python we use NumPy's
[random](https://numpy.org/doc/stable/reference/random/index.html)
module for generating pseudo-random numbers. We always initialize the
random number generator in the same way:
```python
from numpy.random import default_rng
rng = default_rng()
```

We can then use different methods of the
[Generator](https://numpy.org/doc/stable/reference/random/generator.html)
instance to obtain random numbers. Often we want numbers $$x$$ that
are distributed according to the *uniform distribution* on the
interval $$[a, b]$$

\begin{align}
x &\sim \mathcal{U}_\text{[a, b]}\\\\\\
P(x) &= \begin{cases}
   \frac{1}{b -a }, \quad a \le x \le b\\\\\\
   0, \text{otherwise}
   \end{cases}
\end{align}

We get $$N$$ numbers in the desired interval with the
[Generator.uniform()](https://numpy.org/doc/stable/reference/random/generated/numpy.random.Generator.uniform.html#numpy.random.Generator.uniform)
method:

```python
x = rng.uniform(low=a, high=b, size=N)
```

Many other distributions are also available but we will also learn how
to sample from specific distributions by using the *inverse transform
method*.

## Monte Carlo integration (class materials)

* [montecarlo_integration.ipynb]({{ site.nbviewer.resources
  }}/17_MC/montecarlo_integration.ipynb): evaluating integrals with
  uniformly sampled numbers
* [importance_sampling.ipynb]({{ site.nbviewer.resources
  }}/17_MC/montecarlo_integration.ipynb): importance sampling for
  non-smooth integrands and sampling from non-uniform distributions
  
  
