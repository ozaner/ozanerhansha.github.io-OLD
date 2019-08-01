---
layout: post
title: Euler's Method
date: 2019-07-13
tags: math calculus algorithms
---
**Euler's method** is a numerical method used to compute the solution of a first order IVP at a particular point. While not very accurate compared to other methods, it's simplicity makes it a common starting point for students learning numerical analysis. Indeed, it is *the* prototypical numerical algorithm, and serves as a useful starting point in understanding and defining more effective methods.

<!--more-->

Informally, the method works by starting at some initial value $t_0$ then tracing a path of $n$ piecewise lines, each of whose slopes are given by the differential equation, until the desired input $t_n$ is reached. In other words, we follow the slope field at fixed steps from our initial value to our desired value:

![img](/assets/math/eulers-method.PNG?style=centerme)

*The slope field and solution to $y'=2y-1$ along with an Euler's method approximation.*

This method falls under the broader class of *Runge-Kutta* methods. Below we will describe it in greater detail, along with its implementation and error, measured both locally and globally.

## Formal Description
Given a first order IVP:

$$\frac{dy}{dt}=f(t,y),\,\,\,\,\,\,\,\,\,\,\,\,y(t_0)=y_0$$

we want to approximate $y(t)$ for some value $t$. First we split the interval $[t_0,t]$ into $n$ subintervals, giving us $n+1$ equally spaced nodes:

$$\begin{align*}
t_{k+1}&=t_k+h\\
&=t_0+h(k+1)
\end{align*}$$

*Where $h=\frac{t-t_0}{n}$. Note that this means $t_n=t$.*

The more nodes we have, the smaller the **step size** $h$ is, and the more accurate our approximation will be. Using these values of $t_k$ We then perform the following iteration to compute approximate values of $y(t_k)$ at the nodes, denoted $y_k$:

$$y_{k+1}=y_k+hf(t_k,y_k)$$

*Where $y_0$ is given by the initial condition.*

At the $n$th and final iteration, we compute $y_n$ which is our approximation of $y(t)$.

<details>
<summary><h3 class="inline">Derivation</h3></summary>
<!-- <p style="background-color: #d1ecfa;"> -->
    Recalling that <a href="/taylor-series-polynomials">Taylor polynomials</a> can serve as approximations of analytical functions, we'll try using one to approximate $y$ at the next time step $t_1=t_0+h$. Below is the resulting Taylor expansion of $y$ centered at $t_0$:

    $$y(t_1)=y(t_0+h)=y(t_0)+\frac{y'(t_0)}{1!}h+\frac{y''(t_0)}{2!}h^2+\cdots$$

<!-- Note that $t_1-t_0=h$, which is just the step size. Plugging this in, and grouping the other terms together, we get:

    $$y(t_1)=y(t_0)+y'(t_0)h+\frac{y''(t_0)}{2!}h^2+\cdots$$ -->

    We can plug in $f(t,y(t))$ for $y'(t)$ but, as we don't have expressions for the higher derivatives of $y$, we'll cut our approximation short at the first two terms. This gives us the following 1st degree Taylor polynomial:

    $$y(t_1)\approx y(t_0)+hf(t_0,y(t_0))$$

    Now we have an approximation of $y(t_1)$ which we'll call $y_1$. Using $(t_1,y_1)$ as our new initial point, we can use the same procedure to approximate $y(t_2)$ and likewise dub it $y_2$. We keep doing this until we reach $y_n$ which will be our approximation of $y(t_n)$ aka $y(t)$. This procedure of repeated approximations is given by the following iteration:

    $$y_{k+1}=y_k+hf(t_k,y_k)$$
<!-- </p> -->
</details>


<details>
<summary><h3 class="inline">Example</h3></summary>
</details>

## Implementation
### Pseudocode
Given a differential equation $f(t,y)$, the initial values $t_0$ and $y_0$, the number of steps $n$, and the desired input $t_n$ to be evaluated:

1. $h:=\frac{t_n-t_0}{n}$
2. $t:=t_0$
3. $y:=y_0$
4. **repeat** $n$ times:<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$t:=t+h$
    <br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$y:=y+hf(t,y)$
5. **return** $y$

<!-- 1. $h:=\frac{t-t_0}{n}$
2. $y:=y_0$
3. **for** $i$ from $1$ to $n$:<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$y:=y+hf(t_0+ih,y)$
4. **return** $y$ -->

### Python
````python
def eulers_method(f,t0,y0,n,tn):
    h = (tn-t0)/n
    t,y = t0,y0
    for _ in range(1,n):
        t = t + h
        y = y + h*f(t,y)
    return y
````

### Matlab
This Matlab function outputs not just $y_n$ but also optionally outputs a vector $T$ of all the intermediate $t_i$ values and a corresponding vector $Y$ of all the $y_i$ values.
````matlab
function [y,T,Y] = eulers_method(f,t0,y0,n,tn)
    h = (tn-t0)/n;
    T = linspace(t0,tn,n+1);
    Y = y0 ; zeros(n);
    for i = 1:n
        Y(i+1) = Y(i) + h*f(T(i),Y(i));
    end
    y = Y(n+1);
end
````

## Error Analysis
### Local Truncation Error (LTE)
The **local truncation error (LTE)** is the error made in single iteration of Euler's method. That is to say, the LTE at step $i$ is the difference between $y(t_i)$ and it's approximation $y_i$:

$$LTE_i=y(t_i)-y_i$$

We can phrase the LTE in terms of [asymptotic notation](/asymptotic-notation) further by plugging in Taylor expansion of $y(t_i)$, as referenced in the derivation section:

$$\begin{align*}
LTE&=y(t_i)-y_i\\
&=y(t_i)-y(t_{i-1})-hf(t_{i-1},y(t_{i-1}))
\end{align*}$$

### Global Truncation Error (GTE)


## Variations
- varied step size
- backwards eulers method (implicit) [in this context eulers method is referred to as the forward eulers method]

# From classnotes num analysis

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