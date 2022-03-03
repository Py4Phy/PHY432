---
layout: default
title: "Projectile with linear air resistance"
parent: Ordinary Differential Equations
nav_exclude: true
---

After implementing a number of
[integrators for ODEs]({{ site.baseurl }}{% link modules/ODEs/integrators.md %}) we are now in the position to solve some practical problems:

- projectile movement with air resistance (this lecture)
- realistic movement of a spinning baseball (next lecture)

## Linear air resistance

For the problem that you should solve during the class, get the
notebook[^1]
[11-ODE-lineardrag-students.ipynb]({{ site.nbviewer.resources }}/11_ODE_applications/11-ODE-lineardrag-students.ipynb)
and see notebook
[11-ODE-lineardrag.ipynb]({{ site.nbviewer.resources }}/11_ODE_applications/12-ODE-lineardrag.ipynb)
for the full solution.[^2]



## Resources ##

* _Computational Modelling_: Chapter **3**

{% comment %}
* See Homework [Assignment 9 (pdf)]({{ site.assignments.fileurl }}/assignment_09/assignment_09.pdf)
  for a summary of *Baseball Physics*, extensions to the physical
  model (including the velocity-dependence of the quadratic drag
  coefficient and the "drag crisis" around typical baseball
  velocities), and links to the literature.
{% endcomment %}

------------------------------------------------------------

#### Footnotes



[^1]:

     As usual, `git pull` the resources repository
     [{{ site.resources.shortname }}]({{ site.resources.url }}) to get a
     local copy of the notebook. Then **copy the notebook and all other
     code into your work directory** in order to complete the exercises.

[^2]:

     Notebook will be posted after class; in the meantime look at the
     student notebook.
