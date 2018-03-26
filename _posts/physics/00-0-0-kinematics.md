---
layout: post
title: Kinematics
date: 2018-03-17
tags: physics classical-physics classical-mechanics
---
<!-- Make vectors bold rather than arrow headed --> $\renewcommand{\vec}[1]{\mathbf{#1}}$
Translational Kinematics describes the motion of objects through space over time. Using an object's [position](/position), velocity and acceleration vectors, it is possible to predict where it will be in the future and where it was in the past. Where an object gets that velocity/acceleration is what dynamics seeks to explain.

### Variable Acceleration
To calculate the motion of an object with continuous acceleration, simply refer to the definitions of velocity and acceleration:

$$\begin{align}
\vec{v}=\frac{d\vec{x}}{dt}\\
\vec{a}=\frac{d\vec{v}}{dt}
\end{align}$$

Integrating these equations we get:

$$\begin{align}
\vec{x}=\int\vec{v} \,dt+\vec{x}_0\\
\vec{v}=\int\vec{a} \,dt+\vec{v}_0
\end{align}$$

- $\vec{x}$ is the object's position as a function of time.
- $\vec{x}_0$ is the initial position, at $$t=0$$.
- $\vec{v}$ is the object's velocity as a function of time.
- $\vec{v}_0$ is the initial velocity, at $$t=0$$.
- $\vec{a}$ is the object's acceleration as a function of time.
- $t$ is time

<!--more-->

### Constant Acceleration
When acceleration is assumed to be constant, as is the case for many physical systems, the following kinematic equations can be derived:

<!-- #### Position Independent Equation
$$\begin{align}
\vec{v}&=\int\vec{a} \,dt+\vec{v}_0 \tag{integral def. of \(\vec{v}\)}\\
&=\vec{a}\int dt+\vec{v}_0 \tag{\(\vec{a}\) is constant}\\
&=\vec{a}t+\vec{v}_0
\end{align}$$ -->

<details>
<summary><strong>Position Independent Equation</strong></summary>
<p>$$\begin{align}
\vec{v}&=\int\vec{a} \,dt+\vec{v}_0 \tag{integral def. of \(\vec{v}\)}\\
&=\vec{a}\int dt+\vec{v}_0 \tag{\(\vec{a}\) is constant}\\
&=\vec{a}t+\vec{v}_0
\end{align}$$</p>
<p>$$\boxed{\vec{v}=\vec{v}_0+\vec{a}t}$$</p>
</details>

<!-- #### Velocity Independent Equation
$$\begin{align}
\vec{v}&=\vec{a}t+\vec{v}_0 \tag{\(\vec{x}\) independent Eq.}\\
\vec{x}&=\int\vec{v} \,dt+\vec{x}_0 \tag{integral def. of \(\vec{x}\)}\\
&=\int(\vec{a}t+\vec{v}_0) \,dt+\vec{x}_0 \\
&=\int\vec{a}t\,dt + \int\vec{v}_0 \,dt+\vec{x}_0 \\
&=\vec{a}\int t \,dt + \vec{v}_0t+\vec{x}_0 \tag{\(\vec{a}\) is constant}\\
&=\frac{\vec{a}t^2}{2}+\vec{v}_0t+\vec{x}_0
\end{align}$$

$$\boxed{\vec{x}=\frac{\vec{a}t^2}{2}+\vec{v}_0t+\vec{x}_0}$$ -->

<details>
<summary><strong>Velocity Independent Equation</strong></summary>
<p>$$\begin{align}
\vec{v}&=\vec{a}t+\vec{v}_0 \tag{\(\vec{x}\) independent Eq.}\\
\vec{x}&=\int\vec{v} \,dt+\vec{x}_0 \tag{integral def. of \(\vec{x}\)}\\
&=\int(\vec{a}t+\vec{v}_0) \,dt+\vec{x}_0 \\
&=\int\vec{a}t\,dt + \int\vec{v}_0 \,dt+\vec{x}_0 \\
&=\vec{a}\int t \,dt + \vec{v}_0t+\vec{x}_0 \tag{\(\vec{a}\) is constant}\\
&=\frac{\vec{a}t^2}{2}+\vec{v}_0t+\vec{x}_0
\end{align}$$</p>
<p>$$\boxed{\vec{x}=\vec{x}_0+\vec{v}_0t+\frac{\vec{a}t^2}{2}}$$</p>
</details>

<!-- #### Acceleration Independent Equation
$$\begin{align}
\vec{v}&=\vec{a}t+\vec{v}_0 \tag{\(\vec{x}\) independent Eq.}\\
\vec{a}&=\frac{\vec{v}-\vec{v_0}}{t}\\
\vec{x}&=\frac{\vec{a}t^2}{2}+\vec{v}_0t+\vec{x}_0 \tag{\(\vec{v}\) independent Eq.}\\
&=\frac{\frac{\vec{v}-\vec{v_0}}{t}t^2}{2}+\vec{v}_0t+\vec{x}_0\\
&=\frac{\vec{v_0}+\vec{v}}{2}t+\vec{x}_0\\
\end{align}$$

$$\boxed{\vec{x}=\frac{\vec{v_0}+\vec{v}}{2}t+\vec{x}_0}$$ -->

<details>
<summary><strong>Acceleration Independent Equation</strong></summary>
<p>$$\begin{align}
\vec{v}&=\vec{a}t+\vec{v}_0 \tag{\(\vec{x}\) independent Eq.}\\
\vec{a}&=\frac{\vec{v}-\vec{v_0}}{t}\\
\vec{x}&=\frac{\vec{a}t^2}{2}+\vec{v}_0t+\vec{x}_0 \tag{\(\vec{v}\) independent Eq.}\\
&=\frac{\frac{\vec{v}-\vec{v_0}}{t}t^2}{2}+\vec{v}_0t+\vec{x}_0\\
&=\frac{\vec{v_0}+\vec{v}}{2}t+\vec{x}_0\\
\end{align}$$</p>
<p>$$\boxed{\vec{x}=\vec{x}_0+\frac{\vec{v_0}+\vec{v}}{2}t}$$</p>
</details>

<!-- #### Time Independent Equation
$$\begin{align}
&\vec{v}=\vec{a}t+\vec{v}_0 \tag{\(\vec{x}\) independent Eq.}\\
&{\vec{a}}t=\vec{v}-\vec{v}_0\\
&\vec{x}=\frac{\vec{v_0}+\vec{v}}{2}t+\vec{x}_0 \tag{\(\vec{a}\) independent Eq.}\\
&2(\vec{x}-\vec{x}_0)=(\vec{v}+\vec{v}_0)t\\
\end{align}$$

$$\begin{align}
2\vec{a}\cdot(\vec{x}-\vec{x}_0)&=(\vec{v}+\vec{v}_0)\cdot\vec{a}t\\
&=(\vec{v}+\vec{v}_0)\cdot(\vec{v}-\vec{v}_0) \tag{foil dot product}\\
&=\vec{v} \cdot \vec{v} - \vec{v}_0 \cdot \vec{v}_0\\
&=\left \| \vec{v} \right \|^2-\left \| \vec{v}_0 \right \|^2\\
\end{align}$$

$$\boxed{\left \| \vec{v} \right \|^2 = 2\vec{a}\cdot(\vec{x}-\vec{x}_0)+\left \| \vec{v}_0 \right \|^2}$$ -->

<details>
<summary><strong>Time Independent Equation</strong></summary>
<p>$$\begin{align}
&\vec{v}=\vec{a}t+\vec{v}_0 \tag{\(\vec{x}\) independent Eq.}\\
&{\vec{a}}t=\vec{v}-\vec{v}_0\\
&\vec{x}=\frac{\vec{v_0}+\vec{v}}{2}t+\vec{x}_0 \tag{\(\vec{a}\) independent Eq.}\\
&2(\vec{x}-\vec{x}_0)=(\vec{v}+\vec{v}_0)t\\
\end{align}$$

$$\begin{align}
2\vec{a}\cdot(\vec{x}-\vec{x}_0)&=(\vec{v}+\vec{v}_0)\cdot\vec{a}t\\
&=(\vec{v}+\vec{v}_0)\cdot(\vec{v}-\vec{v}_0) \tag{foil dot product}\\
&=\vec{v} \cdot \vec{v} - \vec{v}_0 \cdot \vec{v}_0\\
&=\left \| \vec{v} \right \|^2-\left \| \vec{v}_0 \right \|^2\\
\end{align}$$</p>

<p>$$\boxed{\left \| \vec{v} \right \|^2 = 2\vec{a}\cdot(\vec{x}-\vec{x}_0)+\left \| \vec{v}_0 \right \|^2}$$</p>
</details>

### Book Keeping
There are a couple of things we can do to clean up this set of 4 equations before we display them all together.

#### Displacement vs. Position
While these equations describe the movement of an object in terms of its initial and current position, $\vec{x}_0$ and $\vec{x}$ respectively, it is common to think about kinematics in terms of **displacement** or change in distance instead. The change in distance $\Delta\vec{x}$ is denoted:

$$\Delta\vec{x}=\vec{x}-\vec{x}_0$$

#### Average Velocity
If we look at the acceleration independent equation, we can see it contains the expression $\frac{\vec{v_0}+\vec{v}}{2}$. As it turns out, when acceleration is constant, this expression is actually equivalent to the object's **average velocity** $\overline{\vec{v}}$:

<details>
<summary>Derivation</summary>
<p>$$\begin{align}
&\overline{\vec{v}}=\frac{\vec{x}-\vec{x}_0}{t} \tag{def. of \(\overline{\vec{v}}\)}\\
&\overline{\vec{v}}t=\vec{x}-\vec{x}_0\\
&\vec{x}-\vec{x}_0=\frac{\vec{a}t^2}{2}+\vec{v}_0t \tag{\(\vec{v}\) independent Eq.}\\
&\overline{\vec{v}}t=\frac{\vec{a}t^2}{2}+\vec{v}_0t\\
&\overline{\vec{v}}=\frac{\vec{a}t}{2}+\vec{v}_0\\
&\vec{v}=\vec{a}t+\vec{v}_0 \tag{\(\vec{x}\) independent Eq.}\\
&\vec{a}t=\vec{v}-\vec{v}_0\\
&\overline{\vec{v}}=\frac{\vec{v}-\vec{v}_0}{2}+\vec{v}_0=\frac{\vec{v_0}+\vec{v}}{2}
\end{align}$$</p>
</details>

$$\boxed{\overline{\vec{v}}=\frac{\vec{v_0}+\vec{v}}{2}}$$

#### Dot Product
When deriving the time independent kinematic equation, we used the dot product when manipulating the expressions $(\vec{v}+\vec{v}_0)\cdot \vec{a}$ and $(\vec{v}+\vec{v}_0)\cdot(\vec{v}-\vec{v}_0)$. We were justified in doing so because the dot product is both commutative and distributive.

The dot product of a vector with itself is that vector's **squared norm** and is often denoted as such:

$$\vec{v}\cdot\vec{v}=\left \| \vec{v} \right \|^2=v^2$$

#### The Kinematic Equations
Taking into account average velocity, the simpler dot product notation and using displacement instead of position, we can rewrite the kinematic equations for constant acceleration as:

$$\begin{gather}
&\vec{v}=\vec{v}_0+\vec{a}t \tag{\(\vec{x}\) independent}\\
&\Delta\vec{x}=\vec{v}_0t+\frac{\vec{a}t^2}{2} \tag{\(\vec{v}\) independent}\\
&\Delta\vec{x}=\overline{\vec{v}}t=\frac{\vec{v_0}+\vec{v}}{2}t \tag{\(\vec{a}\) independent}\\
&v^2 = v_0^2+2\vec{a}\cdot\Delta\vec{x} \tag{t independent}
\end{gather}$$

### Graphing
When the position, velocity and acceleration functions are graphed with respect to time, their graphs are related by the kinematic equations.

#### General Info
For any graph of $\vec{x}(t)$
-  Slope of the secant line created by two points is the average velocity during that time interval.
- Slope of line tangent to curve at time $$t$$ is the object's instantaneous velocity at $t$.

For any graph of $\vec{v}(t)$
-  Slope of the secant line created by two points is the average acceleration during that time interval.
- Slope of line tangent to curve at time $$t$$ is the object's instantaneous acceleration at $$t$$.
- Area under a region of the curve from $[a,b]$ is the object's displacement during $[a,b]$.

For any graph of $\vec{a}(t)$
- Area under a region of the curve from $[a,b]$ is the object's change in velocity during $[a,b]$.

#### An Object at Rest
![graphs](/assets/physics/kinematics/kinematics_at_rest.png?style=centerme)
- $\vec{x}(t) = c$, where c is a constant.
- $\vec{v}(t)=0$
- $\vec{a}(t)=0$

#### An Object with Constant Velocity
![graphs](/assets/physics/kinematics/kinematics_const_vel.png?style=centerme)
- $\vec{x}(t)$ is linear.
- $\vec{v}(t) = c$, where c is a constant.
- $\vec{a}(t)=0$

#### An Object with Constant Acceleraion
![graphs](/assets/physics/kinematics/kinematics_const_accel.png?style=centerme)
- $\vec{x}(t)$ is quadratic.
- $\vec{v}(t)$ is linear.
- $\vec{a}(t) = c$, where c is a constant.
