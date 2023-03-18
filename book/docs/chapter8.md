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

(python_advanced_features)=

# Chapter 8

## Overview

```{tip}
With this last lecture, our advice is to **skip it on first pass**,
unless you have a burning desire to read it.
```

It\'s here

1.  as a reference, so we can link back to it when required, and
2.  for those who have worked through a number of applications, and now
    want to learn more about the Python language

A variety of topics are treated in the lecture, including generators,
exceptions and descriptors.

## Iterables and Iterators

We\'ve {ref}`already said something <iterating_version_1>` about iterating in Python.

Now let\'s look more closely at how it all works, focusing in Python\'s
implementation of the `for` loop.

### Iterators

Iterators are a uniform interface to stepping through elements in a
collection.

Here we\'ll talk about using iterators---later we\'ll learn how to
build our own.

Formally, an *iterator* is an object with a `__next__` method.

For example, file objects are iterators .


The objects returned by `enumerate()` are also iterators

```{code-cell} ipython3
e = enumerate(['foo', 'bar'])
next(e)
```

```{code-cell} ipython3
next(e)
```

as are the reader objects from the `csv` module .

Let\'s create a small csv file that contains data from the NIKKEI index

### Iterators in For Loops

All iterators can be placed to the right of the `in` keyword in `for`
loop statements.

In fact this is how the `for` loop works: If we write

```python
for x in iterator:
    <code block>
```

then the interpreter

-   calls `iterator.___next___()` and binds `x` to the result
-   executes the code block
-   repeats until a `StopIteration` error occurs

So now you know how this magical looking syntax works

```python
f = open('somefile.txt', 'r')
for line in f:
    # do something
```

The interpreter just keeps

1.  calling `f.__next__()` and binding `line` to the result
2.  executing the body of the loop

This continues until a `StopIteration` error occurs.

### Iterables

You already know that we can put a Python list to the right of `in` in a
`for` loop

```{code-cell} ipython3
for i in ['spam', 'eggs']:
    print(i)
```

So does that mean that a list is an iterator?

The answer is no

```{code-cell} ipython3
x = ['foo', 'bar']
type(x)
```

```{code-cell} ipython3
:tags: [raises-exception]

next(x)
```

So why can we iterate over a list in a `for` loop?

The reason is that a list is *iterable* (as opposed to an iterator).

Formally, an object is iterable if it can be converted to an iterator
using the built-in function `iter()`.

Lists are one such object

```{code-cell} ipython3
x = ['foo', 'bar']
type(x)
```

```{code-cell} ipython3
y = iter(x)
type(y)
```

```{code-cell} ipython3
next(y)  
```

```{code-cell} ipython3
next(y)
```

```{code-cell} ipython3
:tags: [raises-exception]

next(y)    
```

Many other objects are iterable, such as dictionaries and tuples.

Of course, not all objects are iterable

```{code-cell} ipython3
:tags: [raises-exception]

iter(42)
```

To conclude our discussion of `for` loops

-   `for` loops work on either iterators or iterables.
-   In the second case, the iterable is converted into an iterator
    before the loop starts.

### Iterators and built-ins

Some built-in functions that act on sequences also work with iterables

-   `max()`, `min()`, `sum()`, `all()`, `any()`

For example

```{code-cell} ipython3
x = [10, -10]
max(x)
```

```{code-cell} ipython3
y = iter(x)
type(y)    
```

```{code-cell} ipython3
max(y)
```

One thing to remember about iterators is that they are depleted by use

```{code-cell} ipython3
x = [10, -10]
y = iter(x)
max(y)
```

```{code-cell} ipython3
:tags: [raises-exception]

max(y)
```

(name_res)=

## Names and Name Resolution

### Variable Names in Python

Consider the Python statement

```{code-cell} ipython3
x = 42
```

We now know that when this statement is executed, Python creates an
object of type `int` in your computer\'s memory, containing

-   the value `42`
-   some associated attributes

But what is `x` itself?

In Python, `x` is called a *name*, and the statement `x = 42` *binds*
the name `x` to the integer object we have just discussed.

Under the hood, this process of binding names to objects is implemented
as a dictionary---more about this in a moment.

There is no problem binding two or more names to the one object,
regardless of what that object is

```{code-cell} ipython3
def f(string):      # Create a function called f
    print(string)   # that prints any string it's passed

g = f
id(g) == id(f)
```

```{code-cell} ipython3
g('test')
```

In the first step, a function object is created, and the name `f` is
bound to it.

After binding the name `g` to the same object, we can use it anywhere we
would use `f`.

What happens when the number of names bound to an object goes to zero?

Here\'s an example of this situation, where the name `x` is first bound
to one object and then rebound to another

```{code-cell} ipython3
x = 'foo'
id(x)
```

```{code-cell} ipython3
x = 'bar'  # No names bound to the first object
```

What happens here is that the first object is garbage collected.

In other words, the memory slot that stores that object is deallocated,
and returned to the operating system.