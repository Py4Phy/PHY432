---
layout: default
title: Numbers
nav_exclude: true
---

When working with numerical code, one has to be aware of the
limitations imposed by the [representation of numbers in the
computer](#representation-of-numbers) and the numerical errors
[numerical errors]({{site.baseurl}}{% link modules/fundamentals/errors.md
%}) that algorithms invariably accumulate.

## Representation of numbers

Only a finite number of numbers (integers and floating point) can be
exactly represented in binary in the computer. This leads to problems
of overflow[^1] and underflow and errors in floating point arithmetic that
one needs to be aware of for numerical calculations. In particular,
there is a *machine precision* $$\epsilon_m$$, within which two
mathematically different floating point numbers are represented by the
same number in the computer. A common standard to represent floating
point numbers is the IEEE 754 standard[^2], which defines 32 bit *floats*
and 64 bit *doubles* [^3]. 

Certain floating point arithmetic operations such as subtracting
numbers of similar or very different magnitude, repeated summation, or
attempts at establishing exact equivalence, can have unexpected
consequences.[^4]


## Class Material on Numbers

The class will be presented in a Jupyter notebook. The annotated
notebook is
[07-numbers.ipynb]({{ site.nbviewer.resources }}/07_numbers/07-numbers.ipynb).

## <span class="label" style="background: black">Activity</span> Sine series

As an example for how to approximate the \\(sin(x)\\) function we develop
a simple algorithm based on the series expansion 

$$
\sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \dots
$$

How many terms should be included? One possibility is to not include
more terms when the change in the result is below machine
precision. We will analyze the error in our implementation and think
about ways to decrease it.

Follow the link provided on Canvas to set up your repository.[^5]



## Additional resources

* _Computational Physics_: Ch 2.4, 2.5, 3
* Python Tutorial
[Floating Point Arithmetic: Issues and Limitations](https://docs.python.org/3/tutorial/floatingpoint.html)



------------------------------------------------------------

## Footnotes

[^1]:

     Python integers can be used for arbitrary precision integer
     arithmetic; they will not overflow. NumPy integer
     [data types](https://numpy.org/doc/stable/user/basics.types.html)
     such as `int32`, however, will wrap around.

[^2]:

     For everything you ever wanted to know about floating point
     arithmetic see the paper

       D. Goldberg. *What every computer scientist should know about
       floating-point arithmetic.* ACM Comput. Surv.,
       23(1):5--48, 1991. doi:
       [10.1145/103162.103163](https://doi.org/10.1145/103162.103163).

[^3]:

     The Python `float` is a IEEE 754 *double*. NumPy has a wider
     range of numeric data types, including `float32` (like IEEE 754 *float*),
     `float64` (like IEEE 754 *double*) and also `float128`, but the `float128`
     [is not really a true 128-bit
	 number](https://stackoverflow.com/a/17023995/); on typical x86
	 machines, these are C `long double` which can provide up to 80
	 bit precision (but *not* 128 bit), es explained in the NumPy docs
	 on [extended
	 precision](https://numpy.org/doc/stable/user/basics.types.html#extended-precision). 
	 


[^4]:

     See Bruce M Bush's
     [The Perils of Floating Point](http://www.lahey.com/float.htm)
     and a notebook
     [Perils_of_Floating_Point.ipynb]({{site.nbviewer.resources}}/07_numbers/Perils_of_Floating_Point.ipynb)
     based on that article.

[^5]:

     The problem can be found in the public repository [{{ site.org.url
     }}/Activity_05_numbers_sine_series]({{ site.org.url
     }}/Activity_05_numbers_sine_series) — you are welcome to fork it
	 and work on it: as soon as you push your work to GitHub, the
	 autograder will run for you.
