---
layout: post
title: Linear (Ordinary) Differential Equations
date: 2018-05-28
tags: math calculus
---
## Definition
An $n$th order linear differential equation (LDE) is one that can be expressed as a linear combination of differentiable functions of $x$ and derivatives of some function $y$ with respect to $x$ (up to its $n$th derivative):

$$a_0(x)y+a_1(x)\dfrac{\mathrm{d}y}{\mathrm{d}x}+a_2(x)\dfrac{\mathrm{d}^2y}{\mathrm{d}x^2}+\cdots+a_n(x)\dfrac{\mathrm{d}^ny}{\mathrm{d}x^n}=b(x)$$

Where $a_{i\in\mathbb{N}_n}(x)$, $b(x)$, and $y$ are differentiable functions of $x$.

*The above refers to linear ODEs. Linear PDE's are linear combinations of a function's partial derivatives.*

<!--more-->

#### Homogeneity
When $b(x)$ (which is called the **constant term** despite it not necessarily being a constant) equals $0$, the linear differential equation is considered **homogeneous**.

<!-- ## Linear Differential Operator -->

<!-- ## Vector Space -->

## First Order Solution
First order LDE's are usually written in **explicit form**, meaning the $\dfrac{\mathrm{d}y}{\mathrm{d}x}$ term is isolated from all other variables & constants:

$$a_0(x)y+a_1(x)\dfrac{\mathrm{d}y}{\mathrm{d}x}=b(x)$$

$$\dfrac{\mathrm{d}y}{\mathrm{d}x}=\frac{b(x)-a_0(x)y}{a_1(x)}$$

Noticing that $-\frac{a_0(x)}{a_1(x)}$ and $\frac{b(x)}{a_1(x)}$ are two arbitrary differentiable functions, we can simply relabel them $f(x)$ and $g(x)$ respectively:

$$\dfrac{\mathrm{d}y}{\mathrm{d}x}=f(x)y+g(x)$$

### Homogeneous Case
A first order homogeneous LDE is one in which the constant term $g(x)$ is equal to $0$:

$$\dfrac{\mathrm{d}y}{\mathrm{d}x}=f(x)y$$

Dividing both sides by $y$, we find:

$$\frac{\mathrm{d}y\big/\mathrm{d}x}{y}=f(x)$$

Notice that the left hand side is the derivative of $\ln y$. So, if we integrate both sides we find:

$$\begin{align}
\int\left(\frac{\mathrm{d}y\big/\mathrm{d}x}{y}\right)\mathrm{d}t=\int f(x)\ \mathrm{d}t\\
\ln y+C=\int_0^x f(x)\ \mathrm{d}t
\end{align}$$

Notice that we only need one constant of integration for both integrals. As such, we can denote the lack of the constant in the right hand side's integral by making it an definite integral from $0$ to $x$. Now exponentiating $e$ to both sides gives us our final answer:

$$\begin{align}
e^{\ln y+C}=e^{\int_0^x f(x)\ \mathrm{d}t}\\
e^{\ln y}e^C=e^{\int_0^x f(x)\ \mathrm{d}t}\\
ye^C=e^{\int_0^x f(x)\ \mathrm{d}t}\\
y=\frac{1}{e^C}e^{\int_0^x f(x)\ \mathrm{d}t}\\
\end{align}$$

Noticing that $\frac{1}{e^C}$ is just an arbitrary constant, we can simply relabel it $C$ giving us our final answer:

$$\boxed{y=Ce^{\int_0^x f(x)\ \mathrm{d}t}}$$

The above equation is the solution to any given first order homogeneous LDE. To solve for the constant $C$ one would need to be given an **initial condition** (i.e some pair $(x,y)$ on the function).

### General Case

## Second Order Solution

## Examples

<details><summary><h3 class="inline">Current through RL Circuit (Charging)</h3></summary>
A real world example of a first order LDE with constant coefficients can be found in considering the current of an RL circuit, which is given by Kirchhoff's loop law:

$$\mathcal{E}-IR-L\dfrac{\mathrm{d}I}{\mathrm{d}t}=0$$

*Where emf $\mathcal{E}$ and current $I$ are functions of time $t$, and resistance $R$ and inductance $L$ are constants.*

Rearranging the terms and isolating the derivative, we can put it in a more familiar form:

$$\frac{R}{L}I+\dfrac{\mathrm{d}I}{\mathrm{d}t}=\frac{\mathcal{E}}{L}$$

We can solve this the same way we solve any first order linear differential equation. First we find the integrating factor:

$$e^{\int R/L\;\mathrm{d}t}=e^{Rt/L}$$

Multiplying the equation by the integrating factor:
$$\frac{R}{L}e^{Rt/L}I+e^{Rt/L}\dfrac{\mathrm{d}I}{\mathrm{d}t}=\frac{\mathcal{E}}{L}e^{Rt/L}$$

Integrating both sides (recognizing the product rule):
$$\int \left(\frac{R}{L}e^{Rt/L}I+e^{Rt/L}\dfrac{\mathrm{d}I}{\mathrm{d}t}\right)\;\mathrm{d}t=\int\left(\frac{\mathcal{E}}{L}e^{Rt/L}\right)\;\mathrm{d}t$$

$$\begin{align}
Ie^{Rt/L}&=\frac{L}{R}\cdot\frac{\mathcal{E}}{L}e^{Rt/L}+C\\
&=\frac{\mathcal{E}}{R}e^{Rt/L}+C
\end{align}$$

Solving for $I$ we find:

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

<details><summary><h3 class="inline">Current through RL Circuit (Discharging)</h3></summary>
Notice that as time increases the current asymptotes, specifically:

$$\begin{align}
\lim_{t\rightarrow\infty}{I(t)}&=\lim_{t\rightarrow\infty}\frac{\mathcal{E}}{R}\left(1-e^{-Rt/L}\right)\\
&=\lim_{t\rightarrow\infty}\frac{\mathcal{E}}{R}\left(1-\frac{1}{e^{Rt/L}}\right)\\
&=\frac{\mathcal{E}}{R}\left(1-0\right)\\
&=\frac{\mathcal{E}}{R}
\end{align}$$

The current in an RL circuit after it has been fully charged and the source of emf has been removed is given by Kirchhoff's loop law:

$$-IR-L\dfrac{\mathrm{d}I}{\mathrm{d}t}=0$$

We can rearrange the first order homogeneous LDE above as so:

$$\frac{\mathrm{d}I\big/\mathrm{d}t}{I}=-\frac{R}{L}$$

Integrating both sides with respect to $t$ and noticing the derivative of $\ln$ on the left hand side:

$$\int\left(\frac{\mathrm{d}I\big/\mathrm{d}t}{I}\right)dt=-\int\left(\frac{R}{L}\right)\ \mathrm{d}t$$

$$\ln |I|=-\frac{R}{L}t+C$$

Exponentiating both sides with $e$ we find:

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
