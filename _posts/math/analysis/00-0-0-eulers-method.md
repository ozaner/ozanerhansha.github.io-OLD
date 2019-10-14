---
layout: post
title: Euler's Method
date: 2019-09-19
tags: math analysis algorithms differential-equations
---
<!-- First wrote it on date: 2019-07-13, gave up on proving LTE and GTE (for now) the day its posted-->

**Euler's method** is a numerical method used to compute the solution of a first order IVP at a particular point. While not very accurate compared to other methods, it's simplicity makes it a common starting point for students learning numerical analysis. Indeed, it is *the* prototypical numerical algorithm, and serves as a useful starting point in understanding and defining more effective methods.

<!--more-->

Informally, the method works by starting at some initial value $t_0$ then tracing a path of $n$ piecewise lines, each of whose slopes are given by the differential equation, until the desired input $t_n$ is reached. In other words, we follow the slope field at fixed steps from our initial value to our desired value:

![img](/assets/math/eulers-method.PNG?style=centerme)

*The slope field and solution to $y'=2y-1$ with $y(0)=1$ along with an Euler's method approximation.*

This method falls under the broader class of *Runge-Kutta* methods. Below we will describe it in greater detail, along with its implementation and error, measured both locally and globally.

## Formal Description
Given a first order IVP:

$$\frac{dy}{dt}=f(t,y),\,\,\,\,\,\,\,\,\,\,\,\,y(t_0)=y_0$$

we want to approximate $y(t)$ for some value $t$. First we split the interval $[t_0,t]$ into $n$ subintervals, giving us $n+1$ equally spaced nodes:

$$\begin{align*}
t_{i+1}&=t_i+h\\
&=t_0+h(i+1)
\end{align*}$$

*Where $h=\frac{t-t_0}{n}$. Note that this means $t=t_n$.*

The more nodes we have, the smaller the **step size** $h$ is, and the more accurate our approximation will be. Using these values of $t_i$, we then perform the following iteration to compute approximate values of $y(t_i)$, denoted $y_i$, at the nodes:

$$y_{i+1}=y_i+hf(t_i,y_i)$$

At the $n$th and final iteration, we compute $y_n$ which is our approximation of $y(t_n)$.

<details>
<summary><strong>Derivation</strong></summary>
<!-- <p style="background-color: #d1ecfa;"> -->
    Recalling that <a href="/taylor-series-polynomials">Taylor polynomials</a> can serve as approximations of analytical functions, we'll try using one to approximate $y$ at the next time step $t_1=t_0+h$. Below is the resulting Taylor expansion of $y$ centered at $t_0$:

    $$y(t_1)=y(t_0+h)=y(t_0)+\frac{y'(t_0)}{1!}h+\frac{y''(t_0)}{2!}h^2+\cdots$$

<!-- Note that $t_1-t_0=h$, which is just the step size. Plugging this in, and grouping the other terms together, we get:

$$y(t_1)=y(t_0)+y'(t_0)h+\frac{y''(t_0)}{2!}h^2+\cdots$$ -->

    We can plug in $f(t,y(t))$ for $y'(t)$ but, as we don't have expressions for the higher derivatives of $y$, we'll cut our approximation short at the first two terms. This gives us the following 1st degree Taylor polynomial:

    $$y(t_1)\approx y(t_0)+hf(t_0,y(t_0))$$

    Now we have an approximation of $y(t_1)$ which we'll call $y_1$. Using $(t_1,y_1)$ as our new initial point, we can use the same procedure to approximate $y(t_2)$ and likewise dub it $y_2$. We keep doing this until we reach $y_n$ which will be our approximation of $y(t_n)$ aka $y(t)$. This procedure of repeated approximations is given by the following iteration:

    $$y_{i+1}=y_i+hf(t_i,y_i)$$
<!-- </p> -->
</details>


<!-- <details>
<summary><h3 class="inline">Example</h3></summary>
</details> -->

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

## Truncation Error
Recall from the derivation given above that Euler's method is simply an iterative version of $y(t)$'s 1st order Taylor polynomial. The error incurred by this truncation is dubbed the **truncation error**. This type of error is independent of the precision of our machine, as opposed to round-off error.

### Local Truncation Error (LTE)
The **local truncation error (LTE)** is the error made in one iteration, assuming there was no error previously. Denoted $\tau_i$, it's given by:

$$\tau_i=y(t_i)-y(t_{i-1})$$

As it turns out the *order of convergence* of the LTE is 2. That is to say, the LTE is quadratic with respect to the step size $h$:

$$\tau_i=O(h^2)$$

<details>
<summary><strong>Proof</strong></summary>
While an intuitive reasoning of this fact is easy to show, a real proof of this for any step $i$ is quite complicated and so we'll shelve it for now.
</details>
<p></p>

This result leads to to the next, more complete, view of truncation error. Put roughly: using $\frac{1}{2}$ the step size $h$, gives us $\frac{1}{4}$ the LTE.

### Global Truncation Error (GTE)
The **global truncation error (GTE)** is the error made over the entire iteration of Euler's method so far. In other words, it is the collective effect of all the LTE's up to this step. Denoted $e_i$, it's given by:

$$e_i=y(t_i)-y_i$$

The *order of convergence* of the GTE, and thus of Euler's method, is 1. That is to say that the GTE is linear with respect to $h$.

$$e_i=O(h)$$

<details>
<summary><strong>Proof</strong></summary>
It is intuitive to see this as a result of summing the quadratic LTE's for each step but again, a real proof of this for any step $i$ is complicated and so we'll shelve it for now.
</details>
<p></p>

This is the main error result of Euler's method. Put roughly: using $\frac{1}{2}$ step size $h$, gives us $\frac{1}{2}$ the GTE.

## Variations
### System of ODEs
Euler's method works equally well for a system of first order ODEs. Given the system $\mathbf f(t,\mathbf y)$ and the initial condition $\mathbf y(t_0)=\mathbf y_0$ we have:

$$\mathbf y_{i+1}=\mathbf y_i+h\mathbf f(t_i,\mathbf y_i)$$

Also note that we can reduce any $n$th order ODE to a system of first order ODE's by considering each derivative a separate variable.

### Backwards Euler's Method
A common variation on Euler's method is the following iteration:

$$y_{i+1}=y_i+hf(t_{i+1},y_{i+1})$$

You'll notice that the next iteration of the method $y_{i+1}$ appears on both sides of the equation. This makes the backwards Euler's method an *implicit method*, and $y_{i+1}$ will have to be solved for algebraically for a specific function $f$ before it can be used.

### Variable Step Size
Another variation is found by using a different step size $h_i$ at every iteration:

$$y_{i+1}=y_i+h_{i+1}f(t_i,y_i)$$

Smaller step sizes are more accurate yet more computationally intensive. Thus, it would be desirable to use small step sizes (and thus preserve accuracy) when the function is changing rapidly and bigger ones when it isn't. Here's a [paper](https://www.sciencedirect.com/science/article/pii/S0377042711003682) on the topic.