---
layout: post
title: Taylor Series
date: 2019-01-25
tags: math calculus computer-science
---
Taylor series are a clever way of representing smooth functions as infinite polynomials. Doing this allows us to define important analytic functions (like $\sin x$ or $e^x$) in a way that encompasses the entire complex plane.

Moreover, the partial sums of these series provide a practical way of approximating the values of functions that are themselves infeasible/impossible to compute directly.

<!--more-->

## Definition
The **Taylor series** of a smooth (i.e. infinitely differentiable) complex function $f(z)$ centered at a number $a$ is the following power series:

$$\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n=f(a)+f'(a)(x-a)+\frac{f''(a)}{2!}(x-a)^2+\cdots$$

#### Maclaurin Series
When centered at the origin, i.e. $a=0$, the series is known as a **Maclaurin Series**:

$$\sum_{n=0}^\infty \frac{f^{(n)}(0)}{n!}x^n=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\cdots$$

## Analytic Functions
An function is **analytic** on some interval (or disc for the complex plane) when it equals its Taylor series on that interval:

$$f(x)=\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n$$

When a function is analytic on the entire complex plane it is called **entire**. Also it is important to note that while all analytic functions are smooth, the converse is not true. There are functions that can be infinitely differentiable yet are not equal to their Taylor series.

That said, most of the elementary functions we use in day to day mathematical parlance (i.e. $\tanh x$, $\log x$, $\sqrt x$, etc.) are analytic in some capacity if not entire.

## Taylor Polynomials
The $n$th partial sum of this power series is called the **$k$-th order Taylor polynomial** of $f(x)$:

$$\sum_{n=0}^k \frac{f^{(n)}(a)}{n!}(x-a)^n=f(a)+f'(a)(x-a)+\cdots+\frac{f^{(k)}(a)}{k!}(x-a)^k$$

In the same vein, the $k$th partial sum of a Maclaurin series is a $k$th order Maclaurin polynomial.

Note that while a Taylor series requires a function to be infinitely differentiable, an $n$th degree Taylor polynomial only requires it to be $n$-times differentiable.

## Taylor's Theorem & Remainder
Note that the higher the degree of the Taylor polynomial we take, the closer it is the actual function. Taylor's theorem quantifies this error, allowing us to make full use of Taylor polynomials for approximating the values of hard/impossible to compute functions.

If we have a $k$-times differentiable function $f(x)$, then we can write it in terms of its $k$th order Taylor polynomial $P_k(x)$ centered at a point $a$, and the remainder $R_k(x)$:

$$f(x)=P_k(x)+R_k(x)$$

We can characterize this remainder function in a variety of approximate and explicit ways. Each one having its own uses.

#### Peano Form
The Peano form of the remainder highlights that the error approaches zero the closer one is to the center point of the Taylor polynomial:

$$R_k(x)=h_k(x)(x-a)^k$$

*Where $\lim_{x\to a}h_k(x)=0$*.

#### Asymptotic Notation
Another way to view the remainder is via [asymptotic notation](\asymptotic-notation). In particular, we can characterize the order of convergence (i.e. to what degree our approximation is off) of a Taylor polynomial in the following way:

$$R_k(x)\in O(x^k)$$

#### Lagrange Form
While the above two forms only characterized the remainder term, we can go a step further and provide explicit formulas for it. If the function is not just $k$ but $k+1$ times differentiable, the remainder can also be expressed in mean-value (Lagrange) form:

$$R_k(x)=\frac{f^{(k+1)}(\xi)}{(k+1)!}(x-a)^{k+1}$$

*Where $a<\xi<x$ a-la the mean-value theorem.*

#### Integral Form
With a bit of calculus we can even rewrite the remainder as an integral:

$$R_k(x)=\int_a^x\frac{f^{(k+1)}(t)}{k!}(x-t)^k$$
