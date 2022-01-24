---
layout: default
title: Modularization in Python
parent: Python
nav_exclude: true
---


Re-using code is key to writing maintainable and correct code. We
already learnt how to package code into [functions]({{ site.baseurl
}}/{% link modules/python/functions.md %}#functions). Now we learn how
to package functions into [modules](#modules).

We will also talk about [objects](#objects) because everything in
Python is an "object". Objects are a more general approach to
"packaging code into re-usable units".

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Modules

Modules and packages are "libraries" for Python code. You will use
them constantly to use existing code or to re-use your own code. 

When working with notebooks it is especially useful to modularize
tested code *outside* the notebook and then only import your module in
the notebook.

* [modules]({{ site.baseurl }}{% link modules/python/modules_packages.md %})
* [packages]({{ site.baseurl }}{% link modules/python/modules_packages.md %}#packages)


## Objects

Objects (created in Python with the `class` statement, and hence often
also called *classes*) combine data and code into a single unit.  An
object contains data (held in variables that are called *attributes*)
and it also contains functions (called *methods*) that know how to
operate on the data in the object.

Python is an *object oriented* (OO) language and objects are
everywhere --- in fact *everything* is an object in Python so anything
you lear about objects applies to everything in Python.


* [objects]({{ site.baseurl }}{% link modules/python/objects.md %})



