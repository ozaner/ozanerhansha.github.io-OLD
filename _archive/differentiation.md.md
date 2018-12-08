---
layout: post
title: Derivatives
date: 2018-09-01
tags: math calculus
---

## Definition

<!--more-->

## Partial Derivatives

## Notation
Differentiation has a variety of different notations, most of which are used in different contexts.

### Leibniz's Notation
#### First Order Derivatives
When a function $f(x)$ is set equal to a variable $y$, its derivative with respect to a variable $x$ can be written as either:

$$\frac{dy}{dx}=\frac{d}{dx}f(x)$$

#### Higher Order Derivatives
The $n$th derivative of $f(x)$ with respect to $x$ is denoted:

$$\frac{d^ny}{dx^n}=\frac{d^n}{dx^n}f(x)$$

This notation can be illustrated from the following, and certainly not rigorous, symbolic manipulation:

$$\frac{d}{dx}\left(\frac{dy}{dx}\right)=\frac{d^2y}{d^2x^2}=\frac{d^2y}{(dx)^2}\rightarrow\frac{d^2y}{dx^2}$$

And higher order derivatives would follow much the same.


#### Uses
This representation evokes the idea that the derivative is ratio between infinitesimal quantities. This is however is nothing but a useful fiction.

Also notice that Leibniz's notation is particularly useful in describing partial derivatives as the variable the derivative is taken with respect to is prominently displayed on the bottom.

<!-- $$\underbrace{\frac{d}{dx}\biggl(\cdots\biggl(\frac{d}{dx}}_{n-1}\biggl(\frac{dy}{dx}\biggr)\biggr)\cdots\biggr)=
\underbrace{\frac{d}{dx}\biggl(\cdots\biggl(\frac{d}{dx}}_{n-2}\biggl(\frac{d^2y}{(dx)^2}\biggr)\biggr)\cdots\biggr)=\cdots=\frac{d^{n}y}{(dx)^{n}}$$ -->

### Lagrange's Notation
#### 1st, 2nd, and 3rd Order Derivatives
Given a function $f(x)$ of one variable $x$, it's successive derivatives can be denoted:

$$f'(x),\ f''(x),\ f'''(x),\ \cdots$$

#### Higher Order Derivatives
Clearly this notation will prove to be unwieldly past even the $3$rd derivative. To resolve this, the following notation can be used to represent the $n$th derivative of $f(x)$ with respect to $x$:

$$f^{(n)}(x)$$

With the special case $f^{(0)}(x)=f(x)$, allowing for more flexibility in expressions that vary the order of the derivative.
#### Multiple Variables


#### Uses
While this notation can represent partial derivatives by the use of subscripts, it is better suited to functions of a single variable. Where this notation really shines is in representing the $n$th derivative of a given function. Indeed, virtually all mentions of power or Taylor series' will use this notation over Leibniz's.

### Newton's Notation
