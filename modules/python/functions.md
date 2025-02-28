---
layout: default
title: Functions
parent: Python
nav_exclude: true
---

**Functions** package re-useable code and generalize code by allowing
variable inputs. Writing code with functions is essential for
debugging and reusability. If you have, say, 10 lines of code (or even
less) that do something specific, consider making it a function.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


We are continuing from
[the previous lesson]({{ site.baseurl }}{% link modules/python/flowcontrol.md %}) in the "work directory"
`~/PHY432/03_python`. We will use `ipython` and your text editor.



## Functions

The basic structure a of a Python function

{% highlight python %}
def func_name(arg1, arg2, ...):
    """documentation string (optional)"""
    # body
    ...
    return results
{% endhighlight %}

Repackage our step function:

{% highlight python %}
# Heaviside step function

def heaviside(x):
   """Heaviside step function"""

   theta = None
   if x < 0:
      theta = 0.
   elif x == 0:
      theta = 0.5
   else:
      theta = 1.

   return theta
{% endhighlight %}

When you run it... then nothing happens: The function was defined but
not called.

Now add at the end of `heaviside.py`

{% highlight python %}

x = 3
theta = heaviside(x)

print("Theta({0}) = {1}".format(x, theta))
{% endhighlight %}

and run it. Now the function is being called (`theta = heaviside(x)`)
and its return value assigned to the variable `theta`.

### <span class="label" style="background: gray">Exercise</span> create functions

1. create a file `myfuncs.py`
2. add `heaviside()` to the file
3. add a function `fahrenheit2kelvin()` to convert from Fahrenheit to
   Kelvin [^0]
4. add a function `kelvin2celsius()` to convert from Kelvin to Celsius
   (subtract 273.15).
   
Try out your functions (in `ipython`):

{% highlight python %}
%run myfuncs.py

heaviside(5)
fahrenheit2kelvin(100)
kelvin2celsius(300)

kelvin2celsius(fahrenheit2kelvin(100))
{% endhighlight %}

should give [^4]

~~~
1.0
310.92777777777775
26.850000000000023
37.77777777777777
~~~



### <span class="label" style="background: gray">Exercise</span> Plotting the step function

Perform this activity using *pair programming*[^1].

Use what you learnt about [loops]({{ site.baseurl }}/{% link modules/python/flowcontrol.md %}#loops) and
[functions](#functions) to plot the Heaviside step function. Create a
program `step_plot.py` that

1. defines the Heaviside step function $$\Theta(x)$$ 
   (use [`heaviside(x)` from above](#functions));
2. generates a list of $$x$$ values
   `x_values = [-4, -3.5, -3, ..., 0, 0.5, 1, 1.5, ... 4]`;
3. evaluates $$\Theta(x)$$ for all $$x$$ values and stores the results
   in a list `y_values`;
4. prints the lists of $$x$$ and $$y = \Theta(x)$$ values; it should look
   like
   ~~~
	-4.0 0.0
	-3.5 0.0
    ...
    3.5 1.0
	4.0 1.0 
   ~~~
5. BONUS: plots $$\Theta(x)$$ against $$x$$; see the [Basic
   Plotting]({{ site.baseurl }}{% link modules/python/HelloWorld.md
   %}#basic-plotting) example, namely you can use code like
   
   {% highlight python %}
   import matplotlib.pyplot as plt
   plt.plot(x_values, y_values, '-o', color="red", linewidth=2)
   plt.show()
   {% endhighlight %}
   
   Does your graph look the way that you expect it? [^5]

   ![Plot of the Heaviside step function]({{ site.baseurl }}/{{ site.figs }}/heaviside.png)


## Advanced: Optional keyword arguments

Functions have arguments in their "call signature", e.g., the `x` in
`def heaviside(x)` or `x` and `y` in a function `area()`


{% highlight python %}
def area(x, y):
   """Calculate area of rectangle with lengths x and y"""
   return x*y
{% endhighlight %}

Let's assume that you might also want to be able to calculate the area
when you scale the rectangle with a factor `scale`. Obviously you can
do `scale * area(x, y)`. You could also add a third argument

{% highlight python %}
def area(x, y, scale):
   """Calculate scaled area of rectangle with lengths x and y and scale factor scale"""
   return scale*x*y
{% endhighlight %}

But this means that even for unscaled rectangles you will have to
provide `scale=1`, i.e., `area(x, y, 1)`. 

With an **optional argument** you can set a **default value** that is
used if the argument is not provided:

{% highlight python %}
def area(x, y, scale=1):
   """Calculate scaled area of rectangle with lengths `x` and `y`.
   
   scale factor `scale` defaults to 1
   """
   return scale*x*y
{% endhighlight %}

which can be used as
{% highlight python %}
x, y = 2, 10.5
area(x, y)             # uses scale=1
area(x, y, scale=0.5)
area(x, y, scale=2)
area(x, y, 2)          # DISCOURAGED, use scale=2
{% endhighlight %}

For further details see [More on Defining
Functions](https://docs.python.org/3/tutorial/controlflow.html#more-on-defining-functions).



------------------------------------------------------------

#### Footnotes ####

[^0]:

     See the [conversion from Fahrenheit to Kelvin]({{ site.baseurl }}{% link
     modules/python/variables_expressions_datatypes.md %}#activity-expressions)
      
     $$
     T = \frac{5}{9} (\theta - 32) + 273.15
     $$


[^1]:

     We will try a software engineering technique called
     [pair programming](https://guide.agilealliance.org/guide/pairing.html)
     (borrowed from
     agile/[extreme programming](http://www.extremeprogramming.org/))

     Each of the two programmers takes on one of the following roles:
     - **driver**: has keyboard & types, runs the code
     - **navigator** reads code, provides directions, catches bugs

     *Both* constantly talk to each other: comment on what you're
     typing, comment on what is being typed. Roles are not static but
     are supposed to be switched frequently.

         
     1. Split into teams of 2. (Be nice. Introduce yourselves.) 
     2. Sit next to each other at one desk (online: Share a Zoom Breakout room)
     3. [Flip a coin](https://www.random.org/coins/?num=1&cur=60-usd.0100c-washington)
        to decide who will start out as the *navigator* and who will
        be the *driver*.
     4. Decide whose laptop you are going to use. (online: The *driver* will share their screen and type and run code.)
     5. Switch roles every ~5 minutes (online: Maintain roles for one exercise (or switch if feasible, e.g., if you can quickly exchange code via a remote repository))


[^3]:
   
    Do not type the standard Python prompt `>>>`, it is just shown to distinguish input
    from output.

[^4]:

    You can compare your solution to [myfuncs.py]({{ site.baseurl }}/{{ site.code }}/myfuncs.py).

[^5]:

    You can compare your solution to [step_plot.py]({{ site.baseurl }}/{{ site.code }}/step_plot.py).
