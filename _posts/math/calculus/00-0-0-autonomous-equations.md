---
layout: post
title: Autonomous Differential Equations
date: 2019-08-10
tags: math calculus
---

## Definition
An ODE is called **autonomous** if it is independent of it's independent variable $t$. That is, an explicit $n$th order autonomous differential equation is of the following form:

$$\frac{d^ny}{dt}=f(y,y',y'',\cdots,y^{(n-1)})$$

ODEs that *are* dependent on $t$ are called **non-autonomous**. And a system of autonomous ODEs is called an **autonomous system**.

<!--more-->

### Solvability
Despite this general definition, only first order autonomous equations are solvable in general. Second order autonomous equations are reducible to first order ODEs and can be solved in specific cases. Autonomous equations of higher orders, however, are no more solvable than any other ODE.

## First Order Equations
### General Solution
Recall that any explicit first order autonomous equation:

$$\frac{dy}{dt}=h(y)$$

is [**separable**](/separable-equations) and so, their solution sets are given by the **equilibrium points**, i.e. the roots of $h(y)$, as well as the solutions to the following integral equation:

$$\int\frac{1}{h(y)}\,dy=t+C$$

*Where $C$ is the constant of integration.*

### Behavior of Solutions
*The next 3 section only regard real valued solutions and ODEs.*

Recall that a continuous function $f(y)$ can only change signs after passing through a zero. However, due to the Picard–Lindelöf theorem, no non-equilibrium solution $y$ to the ODE $f(y)$ can pass through an equilibrium point. This means their derivative can't pass through zero, and so the solution is always increasing/decreasing:

<!-- And so, all non-equilibrium solutions are not only bound by their surrounding equilibrium solutions, but must also be monotone functions: -->

![time](/assets/math/autonomous-equations/behavior1.png?style?=centerme){:width="550px"}


Further, all non-equilibrium solutions approach the nearest equilibrium point or, if none bound it, approach infinity:

![time](/assets/math/autonomous-equations/behavior.png?style?=centerme)

And so, more formally, for any solution $y(t)$ to an autonomous equation $f(y)$ we have the following for an arbitrary point $t_0$ in solution's domain:
- if $f(y(t_0))=0$ then $y(t)$ is a equilibrium solution.
- if $f(y(t_0))>0$ then $y(t)$ is increasing and, as $t\to\infty$, tends to the first equilibrium solution greater than $y(t_0)$ or, if none exist, tends to $\infty$.
- if $f(y(t_0))<0$ then $y(t)$ is decreasing and, as $t\to\infty$, tends to the first equilibrium solution lesser than $y(t_0)$ or, if none exist, tends to $-\infty$.

*Note that the limiting behavior is reversed when $t\to-\infty$, we can see this by simply negating the ODE. Also note that this behavior only applies to solutions that satisfy Picard–Lindelöf.*

### Phase Line
A simple consequence of autonomous ODE's being time independent is that the slopes of the slope field are the same for any time $t$:

![time](/assets/math/autonomous-equations/time-invariance.png?style?=centerme){:width="550px"}

As a result, the graph is redundant in the x-axis and can be encapsulated by a 1-Dimensional line parallel to the y-axis. A simplified version of such a plot is called a **phase line**:

![triple](/assets/math/autonomous-equations/triple-graph.png?style?=centerme)

As we can see, the phase line denotes the equilibrium solutions (i.e. the roots of $f(y)$) with a filled in circle while denoting the intervals with increasing/decreasing solutions (i.e. the intervals where $f(y)$ is above/below the $y$-axis) with an up/down arrow.

Phase lines are useful tools in visualizing the properties of particular solutions to autonomous equations. Just by seeing where a solution falls in it, we can tell whether it is increasing, decreasing, or an equilibrium solution. We can also surmise its limiting behavior by seeing whatever equilibrium solution the arrow points to and, if there is none, we know it grows unbounded.

### Classification of Equilibria
As a quick refresher, the equilibria of an ODE can be put into three catagories:

- **Stable**: Solutions sufficiently close to this equilibrium will asymptotically approach it as $t\to\infty$. 
- **Unstable**: Solutions sufficiently close to this equilibrium will diverge from it. 
- **Semi-stable**: Solutions sufficiently close on one side of this equilibrium will asymptotically approach it as $t\to\infty$, but solutions on the other side will diverge from it.

Thanks to limiting behavior of solutions we discussed earlier, classifying the equilibria of an autonomous equation is as easy as spotting the pattern on its phase line:

![equilibria](/assets/math/autonomous-equations/equilibria.png?style?=centerme)

If the surrounding arrows of an equilibrium point point towards it, it is stable (a sink). If they point away from it, it is unstable (a source). And if they point in any other combination, it is semi-stable (a node).

#### First Derivative Test
For any equilibrium point $y_0$ of an autonomous ODE $f(y)$ we have the following:

- if $f'(y_0)>0$ then $y_0$ is stable.
- if $f'(y_0)<0$ then $y_0$ is unstable.
- if $f'(y_0)=0$ then the test gives us no information.


## Second Order Equations
### Order Reduction
A useful method of solving second order autonomous ODEs is expressing them as first order ODEs. We do this by first letting $v=y'$ so that we have:

$$\frac{d^2y}{dt^2}=f(y,v)$$

Now note that, due to the chain rule, we can write:

$$\frac{d^2y}{dt^2}=\frac{dv}{dy}\frac{dy}{dt}=\frac{dv}{dy}v$$

Allowing us to express our original equation as the following first order ODE:

$$\frac{dv}{dy}v=f(y,v)$$

If this ODE is solved, we'll be left with a solution $v(y)$ which we can then use to solve the following first order autonomous equation:

$$\frac{dy}{dt}=v(y)$$

*If we make certain assumptions about the function $f$, like it being separable or dependent only on $y$, we can obtain more [explicit solutions](https://calculus.subwiki.org/wiki/Second-order_first-degree_autonomous_differential_equation).*