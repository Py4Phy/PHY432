---
layout: default
title: Python — Variables, Expressions, and Python data types
parent: Python
nav_exclude: true
---

The [Python](https://www.python.org) programming language is used
widely in the sciences, the computational physics, biology, and
economics/quantitative finance
communities, and in big companies such as Google and Facebook.

For this class we are using **Python 3** (e.g. Python 3.8, 3.9, 3.10),
which is the current standard. A lot of older code is still only
available for Python 2.7 even though Python 2 is no longer officially
supported. (There are a number of sometimes subtle
incompatibilities between 2 and 3 but once you know Python 3 you will
have no problems dealing with Python 2 code if you really have to.)

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Resources ##

There are _many_ books available on Python. The resources below were listed because they are _easily accessible_.

* Official [Beginner's Guide to Python](https://www.python.org/about/gettingstarted/)
* Official [Python 3 Tutorial](https://docs.python.org/3/tutorial/)
* A Primer on Scientific Programming with Python, Hans Petter Langtangen. [chapters 1-5 PDF](https://hplgit.github.io/primer.html/doc/pub/half/book.pdf), Springer.  ISBN-13: 978-3662498866 (written in Python 2.7 but can be easily used with Python 3, too) [^0]
* [PHY432 Wiki: List of Python Tutorials]({{ site.wiki.url }}/Python-tutorials)

Keep the [Python documentation](https://www.python.org/doc/) close by
and have a look at [Python questions on StackOverflow](https://stackoverflow.com/questions/tagged/python).

## Getting started ...

### work directory

1. Open a terminal.
2. Create our "work directory" `~/PHY432/03_python`
3. `cd` into `~/PHY432/03_python`


### ipython

For interactive work we will use the [ipython](http://ipython.org) interpreter. Start it
in a terminal window with

{% highlight bash %}
ipython
{% endhighlight %}

Check that you are in the `~/PHY432/03_python` directory by typing in
ipython (note the percentage sign in `%pwd`):
{% highlight python %}
%pwd
{% endhighlight %}
You should see

~~~~~
Out[1]: '/Users/YOUR_USERNAME/PHY432/03_python'
~~~~~

or similar. 


### editor

You will also edit files with *your editor* (see the lesson on
[creating text files with a text editor]({{ site.baseurl }}{% link
modules/setup_unix/Unix_Shell.md
%}#creating-text-files-with-a-text-editor)). If you use a
point-and-click editor, make sure that you can [find the work
directory]({{ site.baseurl }}{% link modules/python/HelloWorld.md
%}#fn:1).

### python

We will run programs. It is convenient to do this in a second terminal
(and keep the one with `ipython` open).

1. open a second terminal
2. go to the work dir


## Python Fundamentals
Work interactively in `ipython`.

### Comments

Comments start with `#`
{% highlight python %}
# This is a comment.
# Comments are VERY useful

answer = 42     # code with trailing comment
{% endhighlight %}

### Variables and assignment

Variables have names:

{% highlight python %}
answer = 42
{% endhighlight %}

(Must start with letters or underscores, cannot contain spaces or
other reserved characters (e.g., operators).)

and content
{% highlight python %}
print(answer)
{% endhighlight %}
shows `42`

Pro Tip
{: .label .d-inline }

In interactive work, you can also just type the variable name to
see its content:
{: .d-inline }

{% highlight python %}
In [1]: answer = 42

In [2]: answer
Out[2]: 42
{% endhighlight %}



#### <span class="label" style="background: gray">Exercise</span> assignment
Try variable assignments

{% highlight python %}
counts = 33
half = 1/2
h_bar = 1.05457e-34
pi = 3.14159
h = 2 * pi * h_bar
label = "energy (MeV)"
2thirds = 2/3
one = 1.
symmetrical = True
threehalfpi = 0.5 - 0.5j
two pi = 0
{% endhighlight %}

Make sure that each variable contains what you expect.

Did you get a `SyntaxError`? Why?


### Variable types
Each variable has a **type**:

- [numeric types](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex):
  `int`, `float`, `complex`
- [text sequence type](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str) (string): `str`
- [boolean values](https://docs.python.org/3/library/stdtypes.html#boolean-values):
  `True` and `False`; in python, boolean values are returned from
  [truth value testing](https://docs.python.org/3/library/stdtypes.html#truth-value-testing)
- None-data type: `None` (no value or default)

Variables are *dynamically typed*, i.e., Python figures out by itself
what type it should be (different from languages such as C, C++,
Fortran, java).
{% highlight python %}
x = 42
x = 1.5
x = "something"
print(x)
{% endhighlight %}
will print `something`.


Determine the type of a variable with the
[type()](https://docs.python.org/3/library/functions.html#type)
function:

{% highlight python %}
type(counts)
{% endhighlight %}

returns `int`.

#### <span class="label" style="background: gray">Exercise</span> types
Determine the type of the variables from the previous activity:
`half`, `h_bar`, `h`, `label`, `one`, `symmetrical`, `threehalfpi`.

#### Type conversion
{% highlight python %}
float(42)     # --> 42.
int("42")     # --> 42
{% endhighlight %}

but
{% highlight python %}
float("pi")
{% endhighlight %}
raises a `ValueError`.

#### <span class="label" style="background: gray">Exercise</span> True or False
Work with your neighbor. Try the following code and figure out why the
following expressions return `True` or `False`:
{% highlight python %}
True
False
bool(True)
bool(False)
bool(0)
bool(1)
bool(2)
bool("True")
bool("true")
bool("False")
bool("")
bool(" ")
bool(None)
{% endhighlight %}

What rules does Python follow to determine the "truthiness" [^2] of an expression? 


### Expressions

Expressions in Python are formed from numbers, strings, ... and
variables using *operators*. The most commonly used operatores are:

* unary: `+x`, `-x`, `not x`
* binary

  * [comparison operators](https://docs.python.org/3/library/stdtypes.html#comparisons),
    e.g., `x == y`, `x != y`, `x > y`, `x <= y`, ...
	
    A comparison has a boolean value (`True` or `False`).

  * [numerical operators](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex),
    e.g., `x + y`, `x - y`, `x * y`, `x / y`, `x ** y` (power), `x //
    y` (floor division), `x % y` (remainder). 
	
    Also *in-place* operations, which combine numerical operation with
    assignment (`x += y` is the same as `x = x + y`)

* ternary (`x < y < z`, `x if y else z`)

Use parentheses `(` and `)` for grouping and change of precedence.

#### <span class="label" style="background: gray">Exercise</span> Expressions
Compute the temperature $$T$$ in Kelvin from a temperature in Fahrenheit
$$\theta = 100\,^\circ\mathrm{F}$$
using

$$
T = \frac{5}{9} (\theta - 32) + 273.15
$$

Write a program `tempconverter.py` that takes as input the
temperature in Fahrenheit $$\theta$$ and outputs $$T$$.


## Container data types
*Lists* ("arrays") and *tuples* are
[sequences](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)
and support a broad set of common operations. *Dictionaries* (dicts)
contain key-value pairs.[^1]

### Lists

A [list](https://docs.python.org/3/library/stdtypes.html#list) (uses
square brackets `[]` or `list()`):

{% highlight python %}
temperatures = [60.1, 78.3, 98.8, 97.1, 101.3, 110.0]
stuff = ["dog", 42, -1.234, "cat", [3, 2, 1]]
empty = []
two = [[], []]
{% endhighlight %}

Important list operations:

#### Indexing ####

Each element has an **index**:
```
temperatures = [60.1, 78.3, 98.8, 97.1, 101.3, 110.0]   elements
               |    |     |     |     |      |      |
               |  0 |   1 |   2 |   3 |    4 |    5 |   index
```

First element
{% highlight python %}
temperatures[0]
{% endhighlight %}

Arbitrary elements
{% highlight python %}
temperatures[3]
{% endhighlight %}

Note
{: .label .label-yellow .d-inline }

Python indices are **0-based**. 
{: .d-inline }

For example, the *third* element is at index *2*:
{% highlight python %}
temperatures[2]
{% endhighlight %}

**Negative indices** count from the last element to the first:

```
temperatures = [60.1, 78.3, 98.8, 97.1, 101.3, 110.0]   elements
               |    |     |     |     |      |      |
               |  0 |   1 |   2 |   3 |    4 |    5 |   index
               | -6 |  -5 |  -4 |  -3 |   -2 |   -1 |   negative index
```


Last element
{% highlight python %}
temperatures[-1]
{% endhighlight %}

Third element from the end
{% highlight python %}
temperatures[-3]
{% endhighlight %}


Python
[built-in function](https://docs.python.org/3/library/functions.html#built-in-functions)
to determine the *length of a list*:
[len()](https://docs.python.org/3/library/functions.html#len):
{% highlight python %}
len(temperatures)
{% endhighlight %}
gives 6.


#### Slicing ####
Slicing produces a new list by extracting a subset of elements as
determined by the "slice" _start:stop:step_. The general slicing syntax for a list `a`: 
{% highlight python %}
a[start:stop:step]
{% endhighlight %}
where 
- index `start` is *included* and 
- `stop` is *excluded*; 
- `start`, `stop`, `step` are each optional:
   - default for `start`: first element (index 0)
   - default for `stop`: after last element
   - default for `step` is 1, i.e., include every element. 

Negative values are also allowed for indices and negative step counts backwards.

First 3 elements
{% highlight python %}
temperatures[0:3]
temperatures[:3]
{% endhighlight %}
(`start` defaults to 0 and can be omitted).

Omitting parameters:
{% highlight python %}
temperatures[::2] == [60.1, 98.8, 101.3]
temperatures[2::2] == [98.8, 101.3]
temperatures[:2:2] == [60.1]
{% endhighlight %}

##### Example: slicing #####

A list with the first 6 letters of the English alphabet:
{% highlight python %}
letters = ['A', 'B', 'C', 'D', 'E', 'F']
{% endhighlight %}
```
+---+---+---+---+---+---+
|'A'|'B'|'C'|'D'|'E'|'F'|  elements 
+---+---+---+---+---+---+
| 0 | 1 | 2 | 3 | 4 | 5 |  index
+---+---+---+---+---+---+
|-6 |-5 |-4 |-3 |-2 |-1 |  index
+---+---+---+---+---+---+
```

Refer to the schema above to understand which part of the list the
following slices extract:
{% highlight python %}
letters[:3] == ['A', 'B', 'C']
letters[0:3] == ['A', 'B', 'C']
letters[1:3] == ['B', 'C']
letters[-3] == 'D'
letters[-3:-1] == ['D', 'E']
letters[-3:] == ['D', 'E', 'F']
letters[1::2] == ['B', 'D', 'F']
{% endhighlight %}




##### <span class="label" style="background: gray">Exercise</span> extracting from lists

1. extract the letter 'E' from `letters` 
1. extract the letter 'E' from `letters` (in a different way)
1. extract the letters 'C', 'D' from letters
1. extract the letters 'A', 'D' from `letters`
1. extract the letters 'E', 'F' from `letters` (use negative indices)
1. extract the letters 'D', 'E' from `letters` (use negative indices)
1. extract the second element from `stuff`
1. extract the first two values from `temperatures`
1. extract the second-but last  value from `temperatures`
1. extract the last two values from `temperatures`
1. extract the last element of the last element from `stuff` (should
   be `1`)
1. What do you get from `stuff[3:4]`? (Should be an animal)
1. What do you get from `stuff[3:3]`? What is the length of the new list? 
1. BONUS: reverse the order of `temperatures` (note the `step`
   argument)


#### List manipulation
Lists are
[mutable](https://docs.python.org/3/library/stdtypes.html#mutable-sequence-types),
which means that they can be *changed*:
{% highlight python %}
stuff = []              # empty list
stuff.append("dog")     # append
stuff.append("mouse")
stuff[1] = 42           # replace element
stuff.extend([-1.234, "cat", [3, 2, 1]])  # extend with sequence
print(stuff)
{% endhighlight %}

gives `['dog', 42, -1.234, 'cat', [3, 2, 1]]` as above.

You can also *replace parts of a list* (continuing):
{% highlight python %}
stuff[1:3] = ['python', 'swallow']
stuff[-1:] = ['Hund', 'Python', 'Schwalbe', 'Katze']
print(stuff)
{% endhighlight %}

gives `['dog', 'python', 'swallow', 'cat', 'Hund', 'Python',
'Schwalbe', 'Katze']` (note that the last list was inserted).

One can also *insert into a list* without deleting an element by
assigning to an empty slice:
{% highlight python %}
stuff[2:2] = ['parrot', 'llama']
print(stuff)
{% endhighlight %}

gives `['dog', 'python', 'parrot', 'llama', 'swallow', 'cat', 'Hund', 'Python', 'Schwalbe', 'Katze']`.

As a more explicit alternative to `stuff[2:2] = ['parrot', 'llama']` one can use
{% highlight python %}
stuff.insert(2, 'parrot')
stuff.insert(3, 'llama')
{% endhighlight %}




### Tuples

A [tuple](https://docs.python.org/3/library/stdtypes.html#tuple) is a
list-like container("sequence"), defined by comma `,` (but often
parentheses are added for clarity or when defining a 1-tuple or an
empty tuple) or use `tuple()`:

{% highlight python %}
point = -3, 5
point = (-3, 5)
onetuple = ("lonely", )
empty = ()
{% endhighlight %}

Indexing and slicing
[works the same way as for lists]((https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range))
but tuples are *immutable*:

{% highlight python %}
In [18]: point[0] = 4
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-18-14b93c6014c9> in <module>()
----> 1 point[0] = 4

TypeError: 'tuple' object does not support item assignment
{% endhighlight %}

Often used for compact assignment statements
{% highlight python %}
x, y, z = 0, 0, 1
{% endhighlight %}


### Dictionaries

A [dict](https://docs.python.org/3/library/stdtypes.html#dict) is a
mutable container with arbitrary (constant) keys (uses curly braces
`{}` or `dict()`):

{% highlight python %}
ages = {'Einstein': 42, 'Dirac': 31, 'Feynman': 47}
{% endhighlight %}

Access elements by key:
{% highlight python %}
ages['Dirac']
{% endhighlight %}
prints `31`.

Create new entries on the fly:
{% highlight python %}
ages['Heisenberg'] = 1932 - 1901
{% endhighlight %}

The content of a dict has no defined order (unlike lists and tuples):
{% highlight python %}
In [21]: print(ages)
{'Einstein': 42, 'Dirac': 31, 'Heisenberg': 31, 'Feynman': 47}
{% endhighlight %}


------------------------------------------------------------

## Footnotes ##

[^0]:

     An older book by the same author is freely available for ASU
     students but is written in Python 2. The concepts are still valid
     but the syntax may differ in some cases:

     [Python Scripting for Computational
     Science](http://www.springerlink.com/content/978-3-540-73915-9/),
     Hans Petter Langtangen. Texts in Computational Science and
     Engineering, Volume 3, 2008. Springer. DOI:
     [10.1007/978-3-540-73916-6](https://doi.org/10.1007/978-3-540-73916-6)
     (free access to the
     [PDF](https://link-springer-com.ezproxy1.lib.asu.edu/book/10.1007%2F978-3-540-73916-6)
     through the ASU Library — requires ASU login)



[^1]:
     There are more container types available in Python (e.g.,
     [set](https://docs.python.org/3/library/stdtypes.html#set) and
     the
     [collections](https://docs.python.org/3/library/collections.html)
     module in the Standard Library) but understanding *list*,
     *tuple*, and *dict* will already get you a long way.

[^2]:

     See, for instance, YouTube:[Truthiness](https://www.youtube.com/watch?v=Hiifw2fLJ4M) (in Python)

