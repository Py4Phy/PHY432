---
layout: default
title: Debugging Python code
nav_exclude: true
---

Code contains errors (also known as
**[bugs](https://en.wikipedia.org/wiki/Software_bug)** --- literally
the first "bug" was a *moth* stuck in an electromechanical relay of the
Mark II computer).

![The first bug: A page from the Harvard Mark II electromechanical computer's log, featuring a dead moth that was removed from the device. Courtesy of the Naval Surface Warfare Center, Dahlgren, VA., 1988. - U.S. Naval Historical. (Image is in the Public Domain)](https://upload.wikimedia.org/wikipedia/commons/f/ff/First_Computer_Bug%2C_1945.jpg)

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Exceptions ##

When Python code fails, it raises an **[Exception](https://docs.python.org/3/tutorial/errors.html#exceptions)**:

```python
>>> 10 * (1/0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero

>>> 4 + spam*3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'spam' is not defined

>>> '2' + 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```


## Error handling ##

Some errors cannot be avoided and we our code to handle them
gracefully. This is especially true when handling external inputs.

Python provides the
[try...except](https://docs.python.org/3/tutorial/errors.html)
statement to handle exceptions.

In the example, we handle
1. incorrect input (detected by a `TypeError`)
2. division by zero

```python
def normalize(data):
   """Normalize numbers in data to range 0...1"""
   
   try:
      xmin = min(data)
      xmax = max(data)
   except TypeError:
      raise TypeError(f"ERROR: data = {data} contains non-numeric input")

   datarange = xmax - xmin
   try:
      normalized_data = [(x - xmin)/datarange for x in data]
   except ZeroDivisionError:
      print("Range of data is 0, returning 0")
      normalized_data = [0.0 for x in data]
      
   return normalized_data
```


If you want to raise an exception, use
```python
raise ValueError("Incorrect input for data")
```

Note that one can also simply *re-raise* an existing exception from an
`except` block with a bare `raise` statement.


**Fail early and often** — when your code cannot continue safely, it's
better to raise an exception and give up. Calling code can then still
decide to handle the exception.


## Types of bugs ##

Bugs can be

* [syntax and language errors](#syntax-and-language) (easy, relatively
  speaking)
* input errors (not properly dealing with bad/wrong/unexpected input
  data): errors that raise exceptions under certain conditions
* [logic errors](#logic-errors), [edge cases](#edge-cases), corner cases (hard)

Here we provide an introduction to the absolutely necessary business
of identifying and fixing ("squashing") software bugs. Work through
this page and then see [More Resources](#more-resources) at the end
for more advanced material. Bug-hunting can be difficult and tedious
but you have to do it --- code that produces wrong results is useless.


## General strategy

1. Be clear about what your code *ought* to do: what are the inputs,
   what are the outputs? What do you *expect* to get?

2. If you get an *exception* with a *stack trace*: look at the code
   that is referenced.

3. Output intermediate values (e.g., `print()` calls). Compare what
   you get to what you expect. Run the program in your head to
   understand what values you should see.

4. Make one change and re-run. Is the bug fixed? If not, repeat.


## Helpful strategies

* Have a terminal and an editor open, side by side, so that you can
  quickly run the modified code. (Don't forget to save changes before
  running the code...)

* Prototype small code pieces interactively in `ipython`.

* Modularize code (functions, classes, modules) and test individual
  pieces of code.

* Run programs inside `ipython` using the `%run` magic function:

  ```python
  %run hello.py
  ```
  
  The advantage is that now you can *examine variables interactively*
  inside the interpreter.[^1]

* Learn to use the [Python debugger in
  ipython](https://ipython.readthedocs.io/en/stable/interactive/reference.html#using-the-python-debugger-pdb)
  (enable with `%pdb` in ipython).

## <span class="label" style="background: black">Activity</span> Fix as many bugs as possible!

Code for the examples below comes in a Classroom Activity (set-up link
provided in the Canvas LMS). [^0]


### Syntax and language

#### Bug 1
Print the numbers 0 to 9:
{% highlight python %}
fro num in range(10):
    print(num)
{% endhighlight %}

#### Bug 2
Print the squares of the numbers 0 to 9:
{% highlight python %}
for num in range(10):
    x = num**2
     print(x)
print("Done") 
{% endhighlight %}

#### Bug 3
Print "error" for input 0 or the inverse of the input number:
{% highlight python %}
x = input("Enter non-zero number --> ")
if x = 0:
   print("ERROR: number cannot be 0")
else:
   inverse = 1/x
   print(inverse)
{% endhighlight %}

#### Bug 4
Define the sinc-function $$\mathrm{sinc}(x) = \sin(x)/x$$:
{% highlight python %}
def sinc(x):
   return sin(x)/x

print(sinc(3.145))
{% endhighlight %}

### Slicing and list building

A common problem is getting the indexing wrong, resulting in
`IndexError` or subtle errors in the lists themselves. If faced with
slicing problems, try to build and slice lists interactively in
`ipython` and then transfer the working slice recipe to your code. You
sometimes may want to create a simpler or shorter list for testing.

#### Bug 5
Show that my favorite season in Arizona is winter:

{% highlight python %}
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
print('My favorite season is ', seasons[4])
{% endhighlight %}

#### Bug 6
Create a list of values -10, -9.8, -9.6, ..., -0.2, 0, 0.2, ..., 10.

{% highlight python %}
h = 0.2
x = [-10 + i*h for i in range(100)]
{% endhighlight %}


### Edge cases

*Edge cases* occur at the boundaries of the allowed range of input;
typically, you have to test them explicitly. (*Corner cases* occur
when multiple edge cases come together.)

#### Bug 7
The sinc function is defined for all real numbers
{% highlight python %}
import math
def sinc(x):
   return math.sin(x)/x
{% endhighlight %}

but this implementation is incomplete.

1. find values for which our function does not produce the correct
   result
2. fix it
3. BONUS: plot `sinc(x)` for values from -10 to 10 in steps of 0.2. 



### Logic errors

*Logic errors* tend to be the worst because your code runs and might
even produce output that looks roughly correct even though it is
wrong. You find logic errors by having a good understanding of what
your code should produce for a given input and then trying different
inputs and following the input through the code.

#### Bug 8
Create a list of squares of the first 10 natural numbers (0, 1,
2, ..., 10) and print their sum [^2]:
{% highlight python %}
squares = []
s = 0
for n in range(1, 10):
   squares.append(s)
   s = n*n
   print(n, s)

sum_s = sum(squares)
print("sum of squares", sum_s)

# result should be 385
{% endhighlight %}

#### Bug 9
Calculate the position of an object in free fall as a function of time
and store time points (in 1-s intervals) and positions in two arrays
(for plotting):[^3]

{% highlight python %}
g = -9.81
t, h, tmax = 1., 0., 10.

times, positions = [], []
while t <= tmax:
   x = 0.5 * g * t * t
   times.append(t)
   positions.append(x)
   t += h

print(times)
print(values)
{% endhighlight %}


## More resources

* Software Carpentry's lesson on
  [Errors and Exceptions](https://swcarpentry.github.io/python-novice-inflammation/09-errors.html)
  and [Debugging](https://swcarpentry.github.io/python-novice-inflammation/11-debugging.html)
* [Scipy lecture notes: Debugging](https://lectures.scientific-python.org/advanced/debugging/index.html)
  by Gael Varoquaux (advanced level)


------------------------------------------------------------

## Footnotes ##

[^0]:

    If you do not have the access to the GitHub Classroom (e.g.,
    because you are not taking the PHY432 class) then you can do this
    exercise by cloning the activity repository yourself.


[^1]:

    Inside `ipython` you can also
    [run the Python debugger](https://ipython.org/ipython-doc/3/interactive/tutorial.html#debugging)
    using the `%pdb` magic, but this is a more advanced topic.

[^2]:

    At least two errors are hidden here.

[^3]:

    Just in case: To stop a running Python program, press CONTROL and C at the same
    time (`CONTROL + c` or written as `^C` in Unix documentation).


