---
layout: default
title: Modules and Packages
parent: Modularization in Python
grandparent: Python
nav_exclude: true
---


A Python **module** is a file with Python code that can be
**imported** by other code. This makes the code in the module
**re-usable**.

A Python module is a **library** for Python code. 

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

We are continuing from [the previous lesson]({{ site.baseurl }}{% link modules/python/functions.md %}) in the "work directory"
`~/PHY432/03_python`. We will use `ipython` and your text editor.


## Structure of a Python module

A [**module**](https://docs.python.org/3/tutorial/modules.html) is a
file with Python code. It typically contains

- variable assignments
- [function]({{ site.baseurl }}{% link modules/python/functions.md %}) definitions
- [classes]({{ site.baseurl }}{% link modules/python/objects.md %})

i.e., code that defines new objects but does not immediately execute
(although nothing prevents you from putting immediately executing code
into this file.

The module name is the file name without the .py suffix.

The module is **imported** in another file with the `import` statement
```python
import MODULE_NAME
```
where `MODULE_NAME.py` would be the module.

You can access all content of the module (variables, function,
classes) with the dot operator
```python
MODULE_NAME.func_name(...)    # call function func_name
MODULE_NAME.var_name          # value of variable var_name
```



## <span class="label" style="background: gray">Exercise</span> A module for constants

### Create `constants.py`

Create a file `constants.py`:
{% highlight python %}
# constants.py

pi = 3.1415926535897932384626
h = 6.62607015e-34
c = 299792458
{% endhighlight %}

### Importing modules

We can **import** the file in the python interpreter with the
[import](https://docs.python.org/3/reference/simple_stmts.html#import)
statement (note: `constants.py` must be in the same directory, check
with `%pwd` and `%ls`)

{% highlight python %}
import constants

two_pi = 2 * constants.pi
hbar = constants.h / two_pi

print('hbar = {:.9e}'.format(hbar))
{% endhighlight %}

Contents of a module are accessed with the "dot" operator, e.g,
`constants.pi`.

Other ways to import:

{% highlight python %}
# direct import
from constants import h, pi
hbar = h / (2*pi)

# aliasing
import constants as c
hbar = c.h / (2*c.pi)
{% endhighlight %}

## <span class="label" style="background: gray">Exercise</span>  Import and use your `myfuncs` module

In the previous lesson you created [myfuncs.py]({{ site.baseurl }}{%
link modules/python/functions.md %}#exercise-create-functions), which
contains three different functions. Now treat it as a *module* and
import it inside a file `problem2.py` and use some of the functions in
the module.

1. Compute the Heaviside function $$\Theta(n)$$ (i.e.,
   `myfuncs.heaviside(x)`) for the integers $$-10 ≤ n ≤ 10$$, assign
   the list to a variable `y`, and print it with
   
   ```python
   print(f"Heaviside: {y}")
   ```
   
   (This `print()` uses an
   [f-string](https://docs.python.org/3/reference/lexical_analysis.html#formatted-string-literals),
   available since Python 3.6 as an improvement over [format
   representations](https://docs.python.org/3/library/functions.html#format);
   both use the [Format Specification
   Mini-Language](https://docs.python.org/3/library/string.html#formatspec).)
2. Compute the temperature of the boiling point of water under
   standard conditions in degrees Celsius from the value in Kelvin,
   $$T_{\mathrm{boil}} = 373.15$$ K. Assign it to a variable `t_boil` and
   print it with
   
   ```python
   print(f"Water boils at {t_boil:.2f} C.")
   ```


## Standard Library and the Python Eco System

The
[Python Standard Library](https://docs.python.org/3/library/index.html)
contains many useful packages/modules. They are always available. For
example

{% highlight python %}
import math

math.sin(math.pi)
{% endhighlight %}


Other packages that we are going to use

* [numpy](https://www.numpy.org/)
* [matplotlib](https://matplotlib.org/)
* [scipy](https://www.scipy.org/scipylib/index.html)

### <span class="label" style="background: gray">Exercise</span> Explore the Standard Library

Import the *[math](https://docs.python.org/3/library/math.html)*
module and the *[os](https://docs.python.org/3/library/os.html)*
module from the [Python Standard
Library](https://docs.python.org/3/library/index.html) in a file
`problem3.py`. Look in these modules for functions and attributes to
solve the following problems:

1. Compute $$\sin(\tau)$$ and assign the result to variable
   `y_full_circle` (see
   [`math.tau`](https://docs.python.org/3/library/math.html#math.tau)). (Optionally,
   you can also print the value.)

2. Define the [cumulative distribution
   function](https://en.wikipedia.org/wiki/Normal_distribution#Cumulative_distribution_function)
   of the normal distribution with mean µ and standard deviation σ
   \\[
        \Phi(x, µ, σ) = \frac{1}{2} \left[1 + \mathrm{erf}\left(\frac{x-µ}{σ \sqrt{2}}\right)\right]
   \\]
   as a Python function `Phi(x, mu=0., sigma=1.0)`.
   
   For a random variable $$X$$ that is normally distributed with mean
   µ=88.6 and standard deviation σ=6.3 compute the probability
   $$P(X>95)$$ to observe a value of $$X > 95$$, using
   \\[
        P(X > x) = 1 - \Phi(x, µ, σ)
   \\]
   Assign your result to a variable `P_aplus` and print it with
   ```python
   print(f"P(X > 95) = {100 * P_aplus:.1f}%")
   ```


3. Get the current working directory as a string and assign to the
   variable `cwd` and print it with
   ```python
   print(f"cwd = '{cwd}'")
   ```





## Packages

A Python
[**package**](https://docs.python.org/3/tutorial/modules.html#packages)
is a collection of modules that are distributed
together. A package modularizes packages. Modules in a package are
also accessed with the dot operator.

For example, in a hypothetical package `physics` we might have a
module `constants` and a module `math`. We can access constants with
```python
import physics    # our package
import math       # standard library

hbar = physics.constants.PlanckConstant / (2*math.pi)
```
Note 
{: .label .label-yellow .float-left }
In this example, the standard `math` module does *not* overwrite (or "shadow") the
`physics.math` module (or *vice versa*): they live in different namespaces. *Packages
organize modules* in so that name collisions are avoided.


All module files are contained in a single directory and the directory
additionally contains a special file `__init__.py`. The `__init__.py`
file can be empty. Packages can be nested.

The package name is the name of the directory that contains the
modules. 

The example `physics` package would contain the following files

	physics/
	├── __init__.py
	├── constants.py
	└── math.py

and submodules would be accessed as `physics.constants` or
`physics.math`. Anything defined in `__init__.py` would be accessible
from `physics` directly.
