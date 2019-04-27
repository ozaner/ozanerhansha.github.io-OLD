Midterm April 23, one page cheat sheet, calculator is allowed

## Gaussian Quadrature
The idea is to use a higher order polynomial than linear (trapezoid) or quadratic (Simpson) to interpolate the function and integrate. To deal with the Runge phenomenon, we don't use equally distributed interpolation points.

#### Case I node
We have n+1 nodes, where n=0 so there is one node. We want to approximate:

...

don't get the derivation but the Guassian numerical integral for n=0, i.e. 1 point:

$$\int_{-1}^1f(x)\ dx\approx f(x)\cdot 2$$

#### Case 2 nodes
We have n+1 nodes, where n=1 so 2 nodes. We want to approximate the inegral of:

$$\int_{-1}^1f(x)\ dx\approx f(x_0)\cdot w_0+f(x_1)\cdot w_1$$

What are the 4 unknowns, such that the formula is as acuurate as possible? We have:

$$f(x)=c_1+c_2x+c_3x^2+c_4x^3$$

We make a system of 4 equations:

$$\begin{align*}
\int_{-1}^1f(x)\ dx&=\int_{-1}^1 c_1+c_2x+c_3x^2+c_4x^3\ dx\\
&=w_0(c_0+c_2x_0+c_3x^2_0+c_4x^3_0)\\
&+w_1(c_1+c_2x_1+c_3x^2_1+c_4x^3_1)\\
\end{align*}
$$

...

For n=1, 2 pts, we can approxiamte the integral from [-1,1] of f(x) by the following:

$$\int_{-1}^1 f(x)\ dx\approx f\left(-\sqrt{\frac{1}{3}}\right)\cdot 1+f\left(\sqrt{\frac{1}{3}}\right)\cdot 1$$

#### General case
In general to find the n+1 weights and nodes that make the following the closest:

$$\int_{-1}^1f(x)\ dx\approx\sum_{i=0}^n f(x_i)\cdot w_i$$

We find the $x_i$ and $w_i$ such that the following equation is exactly true:

$$\int_a^b p(x)\ dx=\sum_{i=0}^n p(x_i)\cdot w_i$$

where $p(x)$ is a polynomial of degree $2n+1$:

$$p(x)=c_0+c_1x+c_2x^2+\cdots c_{2n+1}x^{2n+1}$$

Our equations are:

$$w_0+w_1+\cdots w_n=\int_{-1}^1 1\ dx=2$$
$$w_0x_0+w_1x_1+\cdots w_nx_n=\int_{-1}^1 x\ dx=0$$
$$w_0x_0^2+w_1x_1^2+\cdots w_nx_n^2=\int_{-1}^1 x^2\ dx=\frac{2}{3}$$
$$\cdots$$
$$w_0x_0^{2n+1}+w_1x_1^{2n+1}+\cdots w_nx_n^{2n+1}=\int_{-1}^1 x^{2n+1}\ dx$$

For this class we'll only need the following weights and nodes (for n=0,1,2) using the Gussian-Legandre method is:

$$f(0)\cdot 2$$
$$f\left(-\sqrt{\frac{1}{3}}\right)+f\left(\sqrt{\frac{1}{3}}\right)$$
$$\frac{5}{9}f\left(-\sqrt{\frac{3}{5}}\right)+\frac{8}{9}f(0)+\frac{5}{9}f\left(\sqrt{\frac{3}{5}}\right)$$

Look online for the weights and nodes for other n.

#### Change of interval of integration

$$\int_a^b f(x)\ dx=\frac{b-a}{2}\int_{-1}^1$$


## IVPs
An IVP is a differential equation:

$$y'(x)=f(x,y(x))$$

along with an initial condition

$$y(x_0)=y_0$$

A solution to an IVP is a function $y(x)$ that satisfies both conditions

#### Properties
An ODE may not be stable and it may not have a unique solution. When this is the case...

Stability definition: We say that the IVP is *well-conditioned* on an interval $[x_0,T]$ if:

$$\partial_yf(x,y)<0$$

For all $x_0\le x\le T$

And unstable when it is positive.

## Midterm 2
- Poly Interpolation in Lagrange/Newton form
- Error estimate of poly interpolation
- Piecewise interpolation (error?)  
---
- Trapezoid/Simpson Method (Composite)
- Error estimate for ^
- Gauss(-Lagrange) Integral formulas for n=0,1,2,3


For a peicewise interpolation, when awsked to give p(x) give just that, a peicewose function with the curly braces and each line/quadratic for whatever intervals

quadratic piecewise needs n+1 nodes where n is even.

The error for an interpolating line at some $x$:

$$|f(x)-p_1(x)|\le\frac{|(x-x_0)(x-x_1)|}{2!}\max_{\xi\in[x_0,x_1]}|f''(\xi)|$$

Then we can find the max of *that* bound by finding the $x$ that maximizes that function to get an error bound.

For an error bound on a peicewise interpolation, we find the max bound of all peices then pick the greatest one.

For a quadratic interpolation it is much the same:

$$|f(x)-p_2(x)|\le\frac{|(x-x_0)(x-x_1)(x-x_2)|}{3!}\max_{\xi\in[x_0,x_1]}|f'''(\xi)|$$

## Eulers method
Given an IVP: $y'(t)=f(t,y(t))$ and $y(t_0)=y_0$ we need to find the function $y(t)$. We want the approximate values of $y(t)$ over some interval $[a,b]$ (where $a=t_0$). First we split $[a,b]$ into $n$ subintervals (which means we have $n+1$ nodes):

$$a=t_0<t_1<\cdots<t_n=b$$

We then perform the following iteration to compute the values of $y(t)$ at the nodes:

$$y_{i+1}=y_ih_if(t_i,y_i)$$

where $h_i$ is the step size (distance between nodes):

$$h_i=x_{i+1}-x_i$$

*technically, the Euler method has a constant step size. This is a more general version of it.*

#### Example
So if we wanted to find $y(2)$ given an IVP of $y'(t)=f(t,y)$ and $y(0)=y_0$ we simply use Euler's method with $n$ sub intervals (the higher $n$ is the greater the accuracy) on the interval $[0,2]$.

#### Local Error
The **local truncation error** (LTE) of the Euler method. Let $y(t)$ be the exact solution of the ODE. The LTE of the Euler method at $t_i$ is given by:

$$LTE(t_{i+1}=y(t_{i+1})-y(t_i)-h_if(t_i,y(t_i))$$

Note that when $i=0$ we get:

$$LTE(t_1)=y(t_1)-\underbrace{y(t_0)+h_0f(t_0,y_0)}_{=y_1}$$

#### Local Error Complexity
We can rephrase the LTE at $t_i$ by using $y$'s Taylor expansion:

$$y(t_i+h_i)=y(t_i)+y'(t_i)h_i+\frac{y''(t_i)}{2}h_i^2+\cdots$$

We have:

$$LTE(t_{i+1})=\left[y(t_i)+y'(t_i)h_i+\frac{y''(t_i)}{2}h_i^2+\cdots\right]-y(t_i)-h_if(t_i,y(t_i))$$

Canceling we arrive at:

$$LTE(t_{i+1})=\frac{y''(t_i)}{2}h_i^2+\frac{y'''(t_i)}{3!}h_i^3+\cdots=O(h_i^2)$$

As we can see, the only way to minimize the LTE is to use smaller $h_i$ (we can't change the solution and thus can't change its higher derivatives).

#### Global Error
The global error is approximately equal to the sum of the local error at each step:

$$GTE\approx\sum_{i=0}^nLTE(t_{i+1})=O(nh_i^2)$$

If the step size is constant then $nh=b-a$. The global error  complexity is then:

$$|y(b)-y_n|=O(h)$$

## Taylor series method
Use to improve euler method.

$$y(t_{i+1})=y(t_i+h_i)=y(t_i)+y'(t_i)h_i+\frac{y''(t_i)}{2}h_i^2+\cdots$$

for example, if we want a method whose $LTE=O(h_i^3)$ then we use the following iteration:

$$y(t_{t+1})\approx y(t_i)+h_iy'(t_i)+\frac{h_i^2}{2}y''(t_i)$$

Notice we took the first 3 terms from the expansion, meaning our error is $O(h_i^3)$. This method requires that we have the first $n$ derivatives of $y$.

To find $y''(t_i)$

$$y''(t)=\frac{d}{dt}[y'(t)]=\frac{d}{dt}f(t,y(t))=\frac{\partial f}{\partial t}+\frac{\partial f}{\partial y}y'=\frac{\partial f}{\partial t}+\frac{\partial f}{\partial y}f(t,y(t))$$

*note the chain rule in the total derivative on the right hand side.*

Using the general derivation we have a better iteration:

$$y_{i+1}= y_i+h_if(t_i,y_i)+\frac{h_i^2}{2}\left[\frac{\partial f}{\partial t}+\frac{\partial f}{\partial y}\cdot f\right]_ {(t_i,y_i)}$$

So, given some initial condition $y(t_0)=y_0$ and function $y'(t)=f(t,y(t))$, we can solve for a method by splitting the intervals up and computing the partial derivatives.
