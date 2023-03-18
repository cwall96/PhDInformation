---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

(python_by_example)=

# Chapter 3 

## Overview

We\'re now ready to start learning the Python language itself.

In this lecture, we will write and then pick apart small Python
programs.

The objective is to introduce you to basic Python syntax and data
structures.

Deeper concepts will be covered in later lectures.

You should have read the {ref}`lecture <getting_started>` on getting started with Python before beginning this one.

## The Task: Plotting a White Noise Process

Suppose we want to simulate and plot the white noise process
$\epsilon_0, \epsilon_1, \ldots, \epsilon_T$, where each draw
$\epsilon_t$ is independent standard normal.

In other words, we want to generate figures that look something like
this:

```{glue:} test_program_1_updated
```

(Here $t$ is on the horizontal axis and $\epsilon_t$ is on the vertical
axis.)

We\'ll do this in several different ways, each time learning something
more about Python.

We run the following command first, which helps ensure that plots appear
in the notebook if you run it on your own machine.

```{code-cell} ipython3
%matplotlib inline
```

## Version 1

(ourfirstprog)=

Here are a few lines of code that perform the task we set

```{code-cell} ipython3
import numpy as np
import matplotlib.pyplot as plt

ϵ_values = np.random.randn(100)
plt.plot(ϵ_values)
plt.show()
```

```{code-cell} ipython3
:tags: [remove-cell]

# This is duplicated as a way to use glue functionality
fig, ax = plt.subplots()
plt.plot(ϵ_values)
plt.show()
```

```{code-cell} ipython3
:tags: [remove-cell]

from myst_nb import glue
glue("test_program_1_updated", fig, display=False)
```

Let\'s break this program down and see how it works.

(import)=

