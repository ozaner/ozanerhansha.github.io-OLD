---
layout: post
title: Euler's Method
date: 2019-07-13
tags: math calculus algorithm numerical-analysis
---
**Euler's method** is a numerical method used to compute the solution of a first order IVP at a particular point. While not very accurate compared to other methods, it's simplicity makes it a common starting point for students learning numerical analysis, as well as defining more effective methods of solving IVPs.

<!--more-->

Informally, the method works by starting at some initial value $t_0$ then tracing a path of $n$ piecewise tangent lines whose slopes are given by the differential equation until the desired input $t_n$ is reached. In other words, we follow the slope field at fixed steps from our initial value to our desired value:

![img](/assets/math/eulers-method.PNG?style=centerme)

*The slope field of $y'=2y-1$ w/ initial condition $y(0)=1$. The solution $y$ is overlayed, as well as the Euler's method approximation of $y(1)$ with $\delta t=0.1$*

This method falls under the broader class of *Runge-Kutta* methods. Below we will describe it in greater detail, along with its implementation and error, measured both locally and globally.

## Formal Description
Given a first order differential equation with initial condition:

$$\frac{dy}{dx}=f(x,y),\,\,\,\,\,\,\,\,\,\,\,\,y(t_0)=y_0$$

*if $y_n<y_0$ then the step size has to be negative.*

## Implementation
### Pseudocode

### Python

### Matlab


##### From classnotes num analysis
## Eulers method
Given an IVP: $y'(x)=f(x,y(x)$ and $y(x_0)=y_0$ we need to find the function $y(x)$. We want the approximate values of $y(x)$ over some interval $[a,b]$ (where $a=x_0$). First we split $[a,b]$ into $n$ subintervals (which means we have $n+1$ nodes):

$$a=x_0<x_1<\cdots<x_n=b$$

We then perform the following iteration to compute the values of $y(t)$ at the nodes:

$$y_{i+1}=y_i+h_if(x_i,y_i)$$

where $h_i$ is the step size (distance between nodes):

$$h_i=x_{i+1}-x_i$$

*technically, the Euler method has a constant step size. This is a more general version of it.*

#### Example
So if we wanted to find $y(2)$ given an IVP of $y'(t)=f(t,y)$ and $y(0)=y_0$ we simply use Euler's method with $n$ sub intervals (the higher $n$ is the greater the accuracy) on the interval $[0,2]$.

#### Local Error
The **local truncation error** (LTE) of the Euler method. Let $y(t)$ be the exact solution of the ODE. The LTE of the Euler method at $x_i$ is given by:

$$LTE(x_{i+1}=y(x_{i+1})-y(x_i)-h_if(x_i,y(x_i))$$

Note that when $i=0$ we get:

$$LTE(x_1)=y(x_1)-\underbrace{y(x_0)+h_0f(x_0,y_0)}_{=y_1}$$

#### Local Error Complexity
We can rephrase the LTE at $x_i$ by using $y$'s Taylor expansion:

$$y(x_i+h_i)=y(x_i)+y'(x_i)h_i+\frac{y''(x_i)}{2}h_i^2+\cdots$$

We have:

$$LTE(x_{i+1})=\left[y(x_i)+y'(x_i)h_i+\frac{y''(x_i)}{2}h_i^2+\cdots\right]-y(x_i)-h_if(x_i,y(x_i))$$

Canceling we arrive at:

$$LTE(x_{i+1})=\frac{y''(x_i)}{2}h_i^2+\frac{y'''(x_i)}{3!}h_i^3+\cdots=O(h_i^2)$$

As we can see, the only way to minimize the LTE is to use smaller $h_i$ (we can't change the solution and thus can't change its higher derivatives).

Big picture: the LTE of the Euler Method is $O(h^2)$ for uniform intervals.

#### Global Error
The global error is approximately equal to the sum of the local error at each step:

$$GTE\approx\sum_{i=0}^nLTE(x_{i+1})=O(nh_i^2)$$

If the step size is constant then $nh=b-a$. Thus, the global error is:

$$|y(b)-y_n|=O(h)$$