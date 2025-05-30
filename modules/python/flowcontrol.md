---
layout: default
title: Flow control
parent: Python
nav_exclude: true
---

**Flow control** is essential for any programming language as this is
the means by which a program can make decisions and repeat pieces of
code. Without flow control, Python would not be more than a
calculator.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

We are continuing from [the previous lesson]({{ site.baseurl }}/{%
link modules/python/variables_expressions_datatypes.md %}) in the "work
directory" `~/PHY432/03_python`. We will use `ipython` and your text
editor.


### Loops

Computers are excellent at repeating instructions. Looping constructs
are used to repeat a block of code for a fixed number of iterations or
until a given condition is met.

#### The `for` loop

The ``for`` statement executes a code block (the "body" of the
for-loop) once for each item in a sequence:

{% highlight python %}
for VARIABLE in SEQUENCE:
    # for-block
    ...   
{% endhighlight %}

* **White-space indentation** demarcates a **block**: Convention: Use
  4 spaces for each indentation level (not TABS)
* `VARIABLE` is set to each item of `SEQUENCE` in turn. You can use
  `VARIABLE` in the loop body.
* `SEQUENCE` can be a list, tuple, string, ... any "iterable".


**Example**: Convert all the measured temperatures from Fahrenheit to
Kelvin, using a
[for loop](https://docs.python.org/3/tutorial/controlflow.html#for-statements).

Create a python program `temperatures.py`
{% highlight python %}
# temperature conversion

temperatures = [60.1, 78.3, 98.8, 97.1, 101.3, 110.0]
for theta in temperatures:
   T = (theta - 32) * (5/9) + 273.15
   print(T)
   
print("Conversion complete")
{% endhighlight %}

and run it[^0]
{% highlight bash %}
python temperatures.py
{% endhighlight %}

to yield

~~~~~
288.76111111111106
298.8722222222222
310.26111111111106
309.31666666666666
311.65
316.4833333333333
Conversion complete
~~~~~


##### <span class="label" style="background: gray">Exercise</span> for loop #####

1. create `temperature.py` as above and run it
2. modify `temperature.py` so that the results are stored in a new
   list `temp_Kelvin`

##### Loops with `range()` #####

The
[range()](https://docs.python.org/3/library/functions.html#func-range)
"function" provides "standard" (as in e.g., C) for-loop behavior:

`range(stop)` iterates through 0, 1, 2, ..., stop-1

{% highlight python %}
for i in range(7):
    print(i)
{% endhighlight %}
and gives `0 1 ... 5 6` whereas `range(start, stop, step)` iterates through start, start+step,
start+2*step, ... with the last element less than stop:
{% highlight python %}
for i in range(1, 7, 2):
    print(i)
{% endhighlight %}
yielding `1 3 5`.


##### <span class="label" style="background: gray">Exercise</span> `range()` #####

Add code to `temperatures.py` (below) to print a
table of the temperature in F and in K side by side by iterating
through the lists `temperatures` and `temp_Kelvin`
simultaneously.

Hints:
* You can use `len()` and `range()`[^2]
* Assign individual values to variables `T_K` and `theta_F` and print each line with the format `print("{0:6.1f} F   {1:6.1f} K".format(theta_F, T_K))`.


{% highlight python %}
# temperature conversion

temperatures = [60.1, 78.3, 98.8, 97.1, 101.3, 110.0]
temp_Kelvin = []
for theta in temperatures:
   T = (theta - 32) * (5/9) + 273.15
   temp_Kelvin.append(T)

# show T in F and K side by side
# ...

{% endhighlight %}

##### List comprehensions (advanced)

We often have to generate a list from computed values as the example
`T` above. Instead of starting with an empty list and appending
values, we can also use a [**list
comprehension**](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions):
the following code does the same as the one above:

{% highlight python %}
# temperature conversion: list comprehension

temperatures = [60.1, 78.3, 98.8, 97.1, 101.3, 110.0]
temp_Kelvin = [(theta - 32) * (5/9) + 273.15 for theta in temperatures]
{% endhighlight %}

We write a `for` loop inside the list brackets where the "body" of the
loop consists of a single expression that typically uses the list
variable. It results in concise code that also generally executes much
faster. 

##### <span class="label" style="background: gray">Exercise</span> Generate values from -10 to 10 in steps of 0.25

Perform this activity using *pair programming*[^3].

We often need a range of values at arbitrary step size, e.g., for plotting a function. The
`range()` function only provides integer numbers. Find a way to
generate a list of numbers from `start=-10` to `stop=10` (exclusive)
with `step=0.25`, i.e., `[-10., -9.75, -9.5, ..., 9.5, 9.75]`.

Put your code into file `grid.py` and store your list in the variable `x_grid`.

(You can use list comprehensions. Think about how to use `range()` and
how to use the integers to generate the floating point numbers.)



#### The `while` loop

The
[while loop](https://docs.python.org/3/reference/compound_stmts.html#while)
(see also the
[while loop in the Python Tutorial](https://docs.python.org/3/tutorial/introduction.html#first-steps-towards-programming))
iterates over a code block until an expression (the "condition") evaluates to `False`:

{% highlight python %}
while condition:
   # while-block
   ...
{% endhighlight %}

The while loop may execute zero times if `condition` is immediately
`False`. It may also run an infinite number of times when the
condition is always `True`.

**Example**: The program `countup.py` will run until `t` has exceeded a preset
value `tmax`:

{% highlight python %}
# countup.py

tmax = 10.
t, dt = 0, 2.

while t <= tmax:
   print("time " + str(t))
   t += dt
print("Finished")
{% endhighlight %}

##### <span class="label" style="background: gray">Exercise</span> reading input

A common problem is to read multiple inputs from a user until a
specific input signals the end of input. The `while` loop works well
in this case:

{% highlight python %}
# read data until empty input

data = []
x = input()
while x != "":
    data.append(x)
    x = input()
    
print("data = {}".format(numbers))
{% endhighlight %}

Write a program `alternatesum.py` that computes the "alternating sum"

$$
A = \sum_{k=0}^{N-1} (-1)^k a_k
$$

from user input of $$N$$ numbers $$a_k, 0 \le k < N$$. Your program should

1. read numbers from input until an empty line is encountered;
2. store the numbers in a list `numbers`;
3. calculate; the "alternating sum" `numbers[0] - numbers[1] +
   numbers[2] - numbers[3] + ...` and store it in a variable `asum`. (You can
   also print `asum`.)



##### Example (optional): Fibonacci sequence

The program `fibonacci.py` will compute the [Fibonacci
series](http://mathworld.wolfram.com/FibonacciNumber.html)

$$
F_n = F_{n-1} + F_{n-2} \quad\text{with}\ F_1 = F_2 = 1
$$

up to `Fmax`:

{% highlight python %}
# fibonacci.py

Fmax = 100
a, b = 0, 1

while b < Fmax:
   print(b, end=' ')
   a, b = b, a+b
print()
{% endhighlight %}

*Before running* `fibonacci.py`, let's try to **anticipate what the code
will do**. We will then run the code. If we get the expected results
then, great!, otherwise: try to figure out why.

<!-- <p class="note"> -->
<em>Anticipating results and comparing to the run afterwards is the
scientific method applied to programming. It is essential if you
want to become a good programmer.</em>
<!-- </p> -->

### Conditionals

Any programming language needs to be able to make decisions. Python
has the
[if](https://docs.python.org/3/tutorial/controlflow.html#if-statements) statement.

**Example**: Consider an implementation of the [Heaviside step function](http://mathworld.wolfram.com/HeavisideStepFunction.html)

$$
\Theta(x) = \begin{cases}
  0 & x < 0 \\
  \frac{1}{2} & x = 0\\
  1 & x > 0
  \end{cases}
$$

as `heaviside.py`

{% highlight python %}
# Heaviside step function

x = 3
theta = None
if x < 0:
   theta = 0.
elif x == 0:
   theta = 0.5
else:
   theta = 1.

print("Theta(" + str(x) + ") = " + str(theta))
{% endhighlight %}


#### <span class="label" style="background: gray">Exercise</span> Step function

Run `heaviside.py` for various values of `x` (at least -3, 0, 3) and
test the output against the mathematical definition.

#### <span class="label" style="background: gray">Exercise</span> Guessing game I

Write a program `guessinggame.py` that takes a single number `guess`
as input and compares it to a preset integer number
`secret_number`. Tell the player if their guess was "too low", "too
high", or that they "guessed the number". You can start with the code
below:

{% highlight python %}
# guessinggame.py

secret_number = 42
guess = int(input("Guess the number: "))

# add more code here...
{% endhighlight %}

BONUS: If you want to enhance this code you can try to generate a
random number using the
[random.randint()](https://docs.python.org/3/library/random.html#random.randrange)
function. (You will learn more about *importing modules* and
*functions* later in this lesson.)

{% highlight python %}
import random

number = random.randint(1, 1000)  # secret integer number between 1 and 1000
{% endhighlight %}


#### <span class="label" style="background: gray">Exercise</span> Guessing game II
Perform this activity using *pair programming*[^3].

Enhance the simple guessing game from the previous exercise with the
following feature:

* Let the player guess repeatedly. Count the number of guesses and print
  them once the player guesses correctly.
   
As before, provide feedback to the user if the number was bigger than the
secret number ("Too big!") or smaller ("Too small!").

You *may* use the following *incomplete* code as a starting point:

{% highlight python %}
# guess.py

import random

secret_number = random.randint(1, 1000)  # secret integer number between 1 and 1000

n_guesses = 0
guess = int(input("Guess the number between 1 and 1000: "))

# add code
   
print(f"Congratulations, you guessed the number {secret_number} in {n_guesses} guesses")
{% endhighlight %}

*Bonus question:* What is the optimal general strategy to guess the
number in this game? How many guesses do you need at most? Calculate
the optimal number of guesses and tell the user if they could have
done better.

### Changing the flow: `break` and `continue`

Normal flow can be *changed* with the `break` and the `continue`
statement by "stepping out" of the current code block.

#### `break`
The `break` statement ends a `for` or `while` loop.

The following example reads data from input until the special word "STOP" is encountered:

{% highlight python %}
data = []
while True:
    x = input()
    if x == "STOP":
        break
    data.append(x)

print(data)
{% endhighlight %}

The `for` loop can also have an `else` clause that is only executed
when the loop exits normally (i.e., *not* via a `break`). We will use
this feature when checking for convergence of algorithms, using a
pattern similar to the following:

{% highlight python %}
for step in range(maxiter):
   value, convergence_criterion = do_calculation()
   if abs(convergence_criterion) < tolerance:
      break   # converged, use value
else:
   print("Calculation did not converge after {} steps.".format(maxiter))

print(value)

{% endhighlight %}


#### `continue`

The `continue` statement immediately starts the next loop iteration.

The following example only prints something every 10 steps:
{% highlight python %}
for step in range(100):
    if step % 10 != 0:
       continue
    print("step = {}".format(step))
{% endhighlight %}

We can use it in parsing content to skip empty lines:
{% highlight python %}
text = "On the first line my true love\n  \n  brought to me\n\n\nOne python snake\n  in a directory tree.\n"
print(text)
for line in text.split('\n'):
    line = line.strip()  # remove leading and trailing white space
    if not line:
       continue
    print("line: ", line)
{% endhighlight %}






------------------------------------------------------------

## Footnotes ##

[^0]:
     Remember, in `ipython` you can also run the program with
     `%run temperatures.py`.

[^1]:
     There are more container types available in Python (e.g.,
     [set](https://docs.python.org/3/library/stdtypes.html#set) and
     the
     [collections](https://docs.python.org/3/library/collections.html)
     module in the Standard Library) but understanding *list*,
     *tuple*, and *dict* will already get you a long way.

[^2]:
     If you already know how to solve the problem with `len()`,
     `range()`, and indexing, try to figure out how to do it more
     elegantly with the
     [zip()](https://docs.python.org/3/library/functions.html#zip)
     function 

[^3]:

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
     2. Sit next to each other at one desk. (When doing this exercise virtually: Share a Zoom Breakout room.)
     3. [Flip a coin](https://www.random.org/coins/?num=1&cur=60-usd.0100c-washington)
        to decide who will start out as the *navigator* and who will
        be the *driver*.     
     4. Decide whose laptop you are going to use. (Virtually: The *driver* will share their screen and type and run code.)
     5. Switch roles every ~5 minutes. (Virtually: Maintain roles for one exercise (or switch if feasible, e.g., if you can quickly exchange code via a remote repository).)

