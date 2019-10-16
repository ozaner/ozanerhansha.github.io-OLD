---
layout: post
title: Linear (Ordinary) Differential Equations
date: 2019-10-15
tags: math analysis differential-equations
---
<!-- original date: 2018-05-28 -->

## Definition
An $n$th order linear differential equation (LDE) is one that can be expressed as a linear combination of differentiable functions of $t$ and derivatives of some function $y$ with respect to $t$ (up to its $n$th derivative):

$$a_0(t)y+a_1(t)y'+a_2(x)y''+\cdots+a_n(t)y^{(n)}=b(x)$$

Where $a_i(t)$, $b(t)$, and $y$ are differentiable functions of $t$.

<!--more-->

*The above refers to linear ODEs, with linear PDE's being linear combinations of a function's partial derivatives. This post deals only with the former.*

<!-- #### Explicit or Implicit (All ODEs)

#### Particular vs. General Solutions (All ODEs)
n initial conditions, general, particular -->

## Homogeneity
When $b(x)=0$, the linear differential equation is dubbed **homogeneous**. Further, every LDE has an **associated homogenous equation** found by setting $b(x)=0$.

Homogenous equations are an important subclass of LDEs as they are both easier to solve and, as we'll see below, are used in deriving solutions to non-homogenous LDEs.

#### Superposition of Solutions
Homogenous LDE's have the unique property that any linear combination, aka superposition, of its solutions is also a solution. That is to say, for any $k$ solutions to a homogenous LDE $y_i(t)$ and constants $c_i\in\mathbb R$ (or any field like $\mathbb C$) the following is also a solution:

$$y(x)=c_1y_1(x)+c_2y_2(x)+\cdots+c_ky_k(x)$$

We call this property linearity, or the **superposition principle**, and it immediately implies that the solution set $S$ to a homogenous differential equation forms a vector space $(S,+,\cdot)$ under function addition and scalar multiplication. As it turns out, the dimension of this vector space is equal to the order of the LDE.

## Extended Linearity
A useful fact, one that allows us to solve a wide variety of non-homogenous LDE's, is that the general solution $y(t)$ to any LDE can be written as:

$$y(t)=y_p(t)+y_c(t)$$

Where $y_p(t)$ is any particular solution to the LDE and $y_c(t)$ is the general solution of its associated homogenous equation.

## First Order LDEs
Note that any first order LDE can be rewritten in the following, more convenient, form:

$$y'+f(t)y=g(t)$$

<!-- *Where $f(t)=\frac{a_0(t)}{a_1(t)}$ and $g(t)=\frac{b(t)}{a_1(t)}$.* -->

*Note we can divide out the coefficient of $y'$ since the quotient of differentiable functions is differentiable.*

<!-- Before we consider the general solutions to first order LDE's, let us first rewrite them in a more convenient form:

$$y'+f(t)y=g(t)$$-->

### Homogeneous Case
A first order homogenous LDE is can be written in the following form:

$$y'=f(t)y$$

This is a [**separable equation**](/separable-equations) and thus its solution set, after some manipulation, is given by the following integral equation:

$$y(t)=Ce^{\int f(t)\mathop{dt}}$$

*Where $C$ is some arbitrary constant.*

<details><summary><strong>Proof</strong></summary>
The ODE $y'=f(t)y$ is separable, and so its equilibrium solutions are given by the roots of $y$, which is just $y=0$. The non-equilibrium solutions are given by:
$$\begin{align*}
y'=\frac{dy}{dt}&=f(t)y\tag{homogenous LDE}\\
\int\frac{dy}{y}&=\int f(t)\mathop{dt}\tag{separable ODE}\\
\ln y&=\int f(t)\mathop{dt} + C_1\tag{integration}\\
y&=e^{\int f(t)\mathop{dt} + C_1}\tag{exponentiation}\\
y&=C_2e^{\int f(t)\mathop{dt}}\\
\end{align*}$$

Notice that $C_2$ is a strictly positive constant over the reals (and non-zero over the complex numbers), but when we let it equal $0$ we arrive at the sole equilibrium solution. As such, we can express the entire solution set to the first order homogenous equation as:

$$\boxed{y=Ce^{\int f(t)\mathop{dt}}}$$

Where $C$ is some arbitrary constant.
</details>

<!-- The above equation is the **general solution** to any given first order homogeneous LDE. To arrive at a **particular solution**, that is solve for the constant $C$, one would need to be given an **initial condition** (i.e some pair $(x,y)$ on the function). -->

### General Case
The general form of a first order LDE is as follows:

$$y'+f(t)y=g(x)$$

The general solution of a first order LDE is given by:

$$y(t)=\frac{\int \mu(t)g(t)\mathop{dt}+C}{\mu(t)}=\frac{\int e^{\int f(t)\mathop{dt}}g(t)\mathop{dt}+C}{e^{\int f(t)\mathop{dt}}}$$

*Where $C$ is some arbitrary constant, and the **integrating factor** $\mu(t)=e^{\int f(t)\mathop{dt}}$.*

<details><summary><strong>Proof</strong></summary>
Ehh...
</details>

#### Examples
<details><summary><strong>Current through RL Circuit (Charging)</strong></summary>
A real world example of a first order LDE with constant coefficients can be found in considering the current of an RL circuit, which is given by Kirchhoff's loop law:

$$\mathcal{E}-IR-L\dfrac{dI}{dt}=0$$

<p><i>Where emf $\mathcal{E}$ and current $I$ are functions of time $t$, and resistance $R$ and inductance $L$ are constants.</i></p>

<p>Rearranging the terms and isolating, we can put it in a more familiar form:</p>

$$\frac{R}{L}I+\dfrac{dI}{dt}=\frac{\mathcal{E}}{L}$$

We can solve this the same way we solve any first order linear differential equation. First we find the integrating factor:

$$e^{\int R/L\;dt}=Ce^{Rt/L}$$

Multiplying the equation by the integrating factor, and canceling out the constant of integration:
$$\frac{R}{L}e^{Rt/L}I+e^{Rt/L}\dfrac{dI}{dt}=\frac{\mathcal{E}}{L}e^{Rt/L}$$

Integrating both sides (recognizing the product rule on the LHS):
$$\int \left(\frac{R}{L}e^{Rt/L}I+e^{Rt/L}\dfrac{dI}{dt}\right)\;dt=\int\left(\frac{\mathcal{E}}{L}e^{Rt/L}\right)\;dt$$

$$\begin{align}
Ie^{Rt/L}&=\frac{L}{R}\cdot\frac{\mathcal{E}}{L}e^{Rt/L}+C\\
&=\frac{\mathcal{E}}{R}e^{Rt/L}+C
\end{align}$$

Now we can just solve for $I$:

$$I=\frac{\frac{\mathcal{E}}{R}e^{Rt/L}+C}{e^{Rt/L}}$$

Assuming the current $I$ is $0$ at $t=0$, we can solve for $C$:

$$\begin{align}
0&=\frac{\frac{\mathcal{E}}{R}e^{R(0)/L}+C}{e^{R(0)/L}}\\
&=\frac{\frac{\mathcal{E}}{R}e^{0}+C}{e^{0}}\\
&={\frac{\mathcal{E}}{R}+C}\\
\rightarrow C&=-\frac{\mathcal{E}}{R}
\end{align}$$

Plugging this back into the equation and doing some more manipulations we find:

$$\begin{align}
I&=\frac{\frac{\mathcal{E}}{R}e^{Rt/L}-\frac{\mathcal{E}}{R}}{e^{Rt/L}}\\
&=\frac{\mathcal{E}}{R}\frac{e^{Rt/L}-1}{e^{Rt/L}}\\
&=\frac{\mathcal{E}}{R}\left(1-\frac{1}{e^{Rt/L}}\right)\\
&=\frac{\mathcal{E}}{R}\left(1-e^{-Rt/L}\right)\\
\end{align}$$

And so, we can conclude that the current $I(t)$ in an RL circuit as a function of time is given by:

$$\boxed{I(t)=\frac{\mathcal{E}}{R}\left(1-e^{-Rt/L}\right)}$$
</details>

<details><summary><strong>Current through RL Circuit (Discharging)</strong></summary>
Notice that as time increases the current asymptotes, specifically:

$$\begin{align}
\lim_{t\rightarrow\infty}{I(t)}&=\lim_{t\rightarrow\infty}\frac{\mathcal{E}}{R}\left(1-e^{-Rt/L}\right)\\
&=\lim_{t\rightarrow\infty}\frac{\mathcal{E}}{R}\left(1-\frac{1}{e^{Rt/L}}\right)\\
&=\frac{\mathcal{E}}{R}\left(1-0\right)\\
&=\frac{\mathcal{E}}{R}
\end{align}$$

The current in an RL circuit after it has been fully charged and the source of emf has been removed is given by Kirchhoff's loop law:

$$-IR-L\dfrac{dI}{dt}=0$$

We can rearrange the first order homogeneous LDE above as so:

$$\frac{dI\big/dt}{I}=-\frac{R}{L}$$

Integrating both sides with respect to $t$ and noticing the derivative of $\ln$ on the left hand side:

$$\int\left(\frac{dI\big/dt}{I}\right)dt=-\int\left(\frac{R}{L}\right)\ dt$$

$$\ln |I|=-\frac{R}{L}t+C$$

Exponentiating both sides with $e$ we get:

$$I=e^{-Rt/L+C}$$

Remembering that at $t=0$ the current is at its peak (i.e $I=\frac{\mathcal{E}}{R}$), we can solve for $C$:

$$\begin{align}
\frac{\mathcal{E}}{R}&=e^{-R(0)/L+C}\\
&=e^C\\
\rightarrow C&=\ln\frac{\mathcal{E}}{R}
\end{align}$$

Plugging this back into our equation for $I$ and doing some manipulations we find:

$$\begin{align}
I&=e^{-Rt/L+\ln\mathcal{E}/R}\\
&=e^{-Rt/L}e^{\ln\mathcal{E}/R}\\
&=e^{-Rt/L}\frac{\mathcal{E}}{R}\\
\end{align}$$

Thus we can conclude that the current $I(t)$ as a function of time though a discharging RL circuit is given by:

$$\boxed{I(t)=\frac{\mathcal{E}}{R}e^{-Rt/L}}$$
</details>


<!-- ## Second Order Solution

### Homogeneous w/ Constant Coefficients

<details><summary><strong>Proof</strong></summary>
</details>

#### Real Roots
#### Complex Roots
#### Multiplicity of Roots -->

## $n$th order LDEs
Higher order LDE's are not solvable in general, and can only be solved in particular cases or with particular assumptions. Below are two such methods:

- **Constant coefficient LDEs** can be solved via the *method of undetermined coefficients*.
- **Constant coefficient homogenous LDE's** can be solved by solving their *characteristic polynomial*.

<!-- One such example are homogenous LDE's with constant coefficients, which can be solved in a manner similar to that of the second order case detailed in the previous section. -->