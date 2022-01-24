---
layout: default
title: Python
has_children: true
has_toc: false
nav_exclude: true
---

![python logo](https://www.python.org/static/img/python-logo.png)
{: .float-right }
For this class, you should know [Python](https://www.python.org). In
particular, you should know all about the basic building blocks and
concepts of this programming language as summarized below. Each
section has a link to a longer page (with exercises) that you can use
for review.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Python interpreter and the first program ##

See [Hello World]({{ site.baseurl }}{% link
modules/python/HelloWorld.md %}) to review:

* using the `python` and `ipython` interpreter
* writing a Python program with your editor
* executing a Python program from the command line
  ```bash
  python program.py
  ```

## Variables, expressions, data types ##

See [Variables, expressions, data types]({{ site.baseurl }}{% link
modules/python/variables_expressions_datatypes.md %}) to review:

* comments in Python (`#`)
* variables and assignments
  * naming
  * assignment operator `=`
  * outputting values with `print()`
  * dynamic typing
* simple variable types
  * numeric types: `int`, `float`, `complex`
  * text sequence (string): `str`
  * boolean values `True` and `False`, truthiness in Python
  * None-data type: `None`
  * casting (type conversion)
* expressions
  * operators
  * precedence
* container data types (with `len()`)
  * lists `list()`, `[1, 2, ...]`
    * indexing `a[3]`, `a[-1]` (zero-based!)
	* slicing `a[start:stop]`, `a[start:stop:step]`
	* mutable
  * tuples `tuple()`, `(1, 2, ...)`, `1, 2, ...` (at least one comma)
    * indexing
	* slicing
	* immutable
	* tuple assignment `a, b = -2, 3`
  * dictionaries `dict()`, `{key: value, key: value, ...}`
    * item access `d[key] --> value`
	* no order
	* mutable

## Flow Control ##

See [Flow Control]({{ site.baseurl }}{% link modules/python/flowcontrol.md %})
to review:

* code blocks, indentation, and white space
* loops
  * `for` loop
    * iteration over sequences `for x in ["one", "two", "three"]:`
	* iterating with `range()`: `for x in range(10):`
	* list comprehensions: `squares = [x*x for x in range(10)]`
  * `while` loop: `while <expression>:`
  * loop control with `break` and `continue`
* conditional: `if <expression> ... elif <expression> ... else`

## Functions ##
See [Functions]({{ site.baseurl }}{% link modules/python/functions.md
%}) to review:

* *defining* a function (`def f(...)`)
  * `return` value
  * doc string
  * arguments
  * keyword arguments (with default values)
* *calling* a function `value = f(...)` 

