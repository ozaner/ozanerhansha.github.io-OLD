---
layout: post
title: Bisection Method
date: 2019-02-23
tags: computer-science algorithms math
---

The **bisection method** is a numerical root-finding algorithm. The sequence this algorithm produces is guaranteed to converge to a root, albeit relatively slowly, assuming the initial conditions were satisfied.

## Preconditions
The algorithm takes a real-valued, continuous function $f$ and two values $a$ and $b$ such that:

$$f(a)f(b)<0$$

*i.e. $f(a)$ and $f(b)$ have different signs.*

as well as some tolerance $\text{tol}$ that our approximate root $c$ should fall within:

$$|c-a|=|c-b|\le\text{tol}$$

an alternative to measuring how far $c$ is from

## Pseudocode

1. $c:=\frac{a+b}{2}$
2. if $c-a$
