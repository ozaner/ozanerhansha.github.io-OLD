---
layout: post
title: Big $O$ Notation
date: 2018-09-12
tags: math computer-science
---
Big $O,\Omega$ and $\Theta$ notation, collectively referred to as **Bachmann–Landau notation**, is a way to classify the limiting behavior of a particular function as (one of) its arguments tends towards a particular value or, most commonly, infinity.

Bachmann–Landau notation is most commonly used in describing the computational complexity (usually temporal, but also spatial) of certain algorithms. Ideally an algorithm will be of the order of a relatively slowly growing function (e.g $\log n$ grows slower than $n^2$) as they take less resources and thus are more feasible to compute.

This concept is strongly related to, and in fact can be phrased in, [Asymptotic Equivalence](\asymptotic-equivalence#relation-to-algorithmic-complexity).

## Big $O$
Given a function $g(x)$, we can think of $O(g(x))$ as the set of all functions whose limiting function is less than or equal to $g(x)$ up to some constant. We call this its **upper bound complexity**.

Big $O$ is the most common of the three notations, as computer scientists are most often concerned with **worst-case analysis** which relates to idea of an upper-bound.

#### Definition
A function $f(x)$ is on the order of $g(x)$, i.e $f(x)\in O(g(x))$, if the following holds:

$$f(x)\in O(g(x))\equiv (\exists k,x_0)\ x\ge x_0\rightarrow f(x)\le kg(x)$$

Or in English, if there exists some $x_0$ from which the output of $f(x)$ is at most $kg(x)$, where $k$ is some set constant.

#### Examples
- $5x^3\in O(x^3)$ Same most significant term (times a constant).
- $x^2\in O(x^3)$ Lower than most significant term.
- $2n^2\in O(n!+n)$ Lower than most significant term.
- $x^3\not\in\Omega(x^2)$ Can't grow faster than function.

## Big $\Omega$
While big $O$ notation gives the set of all functions that grow as fast or slower than a given function, big $\Omega$ gives the set of all functions that grow as fast or faster than a given function. We call this its **lower bound complexity**.

#### Definition
A function $f(x)\in\Omega(g(x))$, if the following holds:

$$f(x)\in\Omega(g(x))\equiv (\exists k,x_0)\ x\ge x_0\rightarrow f(x)\ge kg(x)$$

Or in English, if there exists some $x_0$ from which the output of $f(x)$ is at least $kg(x)$, where $k$ is some set constant.

#### Examples
- $2x^2\in\Omega(x^2)$ Same most significant term (times a constant).
- $x^3\in\Omega(x)$ Greater than most significant term.
- $n!\in\Omega(3n^2+2n)$ Greater than most significant term.
- $x^3\not\in\Omega(x^4)$ Can't grow slower than function.

## Big $\Theta$
Big $O$ and big $\Omega$ notation give the upper and lower bound complexity of a function respectively. Big $\Theta$ is the combination of both, meaning that if a function is big $\Theta$ of another function than they grow at the *same* speed, up to a constant. This is its **upper-lower bound complexity**.

While big $\Theta$ is the most descriptive of the 3 notations, it is not as popular as big $O$. This is a combination of laziness and real world problems in proving both the big $O$ and big $\Omega$ class of a particular algorithm.

#### Definition
A function $f(x)\in\Theta(g(x))$, if the following holds:

$$f(x)\in\Omega(g(x))\equiv (\exists k,x_0)\ x\ge x_0\rightarrow f(x)= kg(x)$$

Or in English, if there exists some $x_0$ from which the output of $f(x)$ is equal to $kg(x)$, where $k$ is some set constant.

We can also phrase it in terms of sastisfying both big $O$ and big $\Omega$ notation:

$$f(x)\in\Theta(g(x))\equiv f(x)\in O(g(x))\wedge f(x)\in\Omega(g(x))$$

#### Examples
- $2x^2\in\Omega(x^2)$ Same most significant term (times a constant).
- $x^3\in\Omega(x)$ Greater than most significant term.
- $n!\in\Omega(3n^2+2n)$ Greater than most significant term.

## Practical Considerations and Notation
Since in regards to computation finite blah blah $n$ isntead of $x$

## Other Notations

### Explicit Set Definitions
### Limit Definitions

|Symbol||   |   |   |
|---|---|---|---|---|
| s  |   |   |   |   |
|   |   |   |   |   |
|   |   |   |   |   |
