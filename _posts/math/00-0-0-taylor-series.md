---
layout: post
title: Taylor Series
date: 2019-01-25
tags: math calculus computer-science
---
Taylor series are a clever way of representing smooth (i.e. infinitely differentiable) functions as infinite polynomials. Doing this allows us to define important analytic functions (like $\sin x$ or $e^x$) in a way that encompasses the entire complex plane.

Moreover, the partial sums of these series provide a practical way of approximating the values of functions that are themselves infeasible/impossible to compute directly.

<!--more-->

## Definition
The **Taylor series** of a smooth (i.e. infinitely differentiable) real, or complex, function $f(x)$ centered at a number $a$ is the following power series:

$$\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n=f(a)+f'(a)(x-a)+\frac{f''(a)}{2!}(x-a)^2+\cdots$$

#### Maclaurin Series
When centered at the origin, i.e. $a=0$, the series is known as a **Maclaurin Series**:

$$\sum_{n=0}^\infty \frac{f^{(n)}(0)}{n!}x^n=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\cdots$$

## Analytic Functions
A function $f$ is **analytic** over some interval of the reals/disc of the complex numbers when it equals its Taylor series in that domain:

$$f(x)=\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n$$

When a function is analytic on the entire complex plane it is called **entire**.

A Taylor series can fail to be analytic in a variety of ways, like by not being convergent, converging to a value different from that of the function, or just not being smooth. This means that there are infinitely differentiable functions that don't equal their Taylor series.

That said, most of the elementary functions we use in day to day mathematical parlance (i.e. $\tanh x$, $\log x$, $\sqrt x$, etc.) are analytic in some capacity if not entire.

## Taylor Polynomials
The $k$th partial sum of this power series is called the **$k$th order Taylor polynomial** of $f(x)$:

$$\sum_{n=0}^k \frac{f^{(n)}(a)}{n!}(x-a)^n=f(a)+f'(a)(x-a)+\cdots+\frac{f^{(k)}(a)}{k!}(x-a)^k$$

In the same vein, the $k$th partial sum of a Maclaurin series is a $k$th order Maclaurin polynomial.

Note that while a Taylor series requires a function to be infinitely differentiable, a $k$th degree Taylor polynomial only requires it to be $k$-times differentiable.

## Taylor's Theorem & Remainder
Note that the higher the degree of the Taylor polynomial we take, the closer it is the actual function. Taylor's theorem quantifies this error, allowing us to make full use of Taylor polynomials for approximating the values of hard/impossible to compute functions.

If we have a $k$-times differentiable function $f(x)$, then we can write it in terms of its $k$th order Taylor polynomial $P_k(x)$ centered at a point $a$, and the remainder $R_k(x)$:

$$f(x)=P_k(x)+R_k(x)$$

We can characterize this remainder function in a variety of approximate and explicit ways. Each one having its own uses.

#### Peano Form
The Peano form of the remainder highlights that the error approaches zero the closer the function is evaluated to the center point $a$ of the Taylor polynomial:

$$R_k(x)=h_k(x)(x-a)^k$$

*Where $\lim_{x\to a}h_k(x)=0$*.

#### Lagrange Form
If $f$ has a continuous $k+1$ order derivative, we can give a more explicit remainder using the mean value theorem:

$$R_k(x)=\frac{f^{(k+1)}(c)}{(k+1)!}(x-a)^{k+1}$$

*Where $a<c<x$ a-la the mean-value theorem.*

#### Integral Form
With a bit of calculus we can even rewrite Lagrange remainder as an integral:

$$R_k(x)=\int_a^x\frac{f^{(k+1)}(t)}{k!}(x-t)^k\ dt$$


#### Asymptotic Notation
Another way to view the remainder is via [asymptotic notation](\asymptotic-notation). In particular, we can characterize the order of convergence (i.e. to what degree our approximation is off) of a Taylor polynomial in the following way:

$$R_k(x)\in O(x^{k+1}),\ \ \ x\to a$$

This is assuming the $k+1$ order derivative is nonzero. In reality the order of convergence may be even higher:

$$R_k(x)\in O(x^p),\ \ \ x\to a$$

*where $f^{(p)}(a)$ is the first non zero derivative after $k$.*
