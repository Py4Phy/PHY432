---
layout: default
title: Jupyter
nav_exclude: true
---

In the [Introduction to Python]({{ site.baseurl }}{% link
modules/python/python.md %}) we worked with the `python` interpreter or
in `ipython`. Our in- and output was completely text
based. Furthermore, we could either run a program that we wrote in our
editor or we could use the REPL in the interpreter, which provides a
very linear and sequential means to execute code.

For interactive data exploration and developing smaller projects it
can be very convenient to combine text, code, and graphical output in
one document. Such a document is often called a *notebook*.

<a href="https://jupyter.org"><img
src="https://jupyter.org/assets/logos/rectanglelogo-greytext-orangebody-greymoons.svg"
width="40%" style="float: right" alt="Jupyter logo" title="Project Jupyter" /></a>

In Python, the [**Jupyter** project](https://jupyter.org/) (which was
born from ipython) provides a browser-based notebook
environment. Currently two interfaces are available, the "classic"
notebook and the modern JupyterLab. You can use either one but in the
following we will use the traditional (and simpler) notebook.



<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Classic Jupyter notebook

Launch the classic Jupyter notebook interface in your web browser[^1]:

{% highlight bash %}
jupyter notebook
{% endhighlight %}


## How to use the notebook

Basic Jupyter notebook commands:

* Look at the **Help** menu! (see also the
  [Jupyter Notebook Online Help](http://nbviewer.jupyter.org/github/ipython/ipython/blob/3.x/examples/Notebook/Index.ipynb))
* A notebook has
  [two modes](http://nbviewer.jupyter.org/github/ipython/ipython/blob/3.x/examples/Notebook/Notebook%20Basics.ipynb#Modal-editor)
  * **edit mode**:
    * green box around a cell: you can type into the cell
    * enter edit mode by pressing `Enter` (or `Return`) or click on a
      cell
  * **command mode**:
    * gray box around a cell (you *cannot* type into a cell!)
    * keys perform many different actions (don't type randomly...),
      e.g., cursor keys move up/down, `c` copies a cell, `shift +
      enter` evaluates a cell.
	* enter command mode by pressing `ESC` or clicking outside a
      cell's area
* Evaluate a cell: in command mode (gray cells with blue side bar):  `shift + return`
* Change a cell type: menu (*code* is Python, *Markdown* is text in
  [Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
  format)

## Resources
* [Jupyter notebook
  documentation](https://jupyter-notebook.readthedocs.io/en/latest/?badge=latest)
* [JupyterLab Documentation](https://jupyterlab.readthedocs.io/en/stable/)  

----------

## Footnotes

	

[^1]:

    If you have problems launching the notebook interface on Mac OS X,
    try

         jupyter notebook --ip=127.0.0.1

    If problems persist, search the internet for the error message and ask for help.




