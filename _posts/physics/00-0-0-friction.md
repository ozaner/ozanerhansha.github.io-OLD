---
layout: post
title: Friction
date: 2018-03-26
tags: physics
# classical-mechanics
---
## General Info
**Dry friction** is a force that opposes the motion of two solid surfaces that slide against each other. This force is proportional to the normal force of the object.

#### Where does Friction come from?
The frictional force is not fundamental and is instead a useful abstraction of the complex electromagnetic interactions between two surfaces that come into contact with each other. The sum total of the forces created by these interactions can, in a variety of cases, be thought of as a singular force that is proportional to the normal force.

![complexfriction](/assets/physics/friction_between_surfaces.png?style=centerme){:width="450px"}

#### Intuition and Newton's First Law
The frictional force is responsible for filling the gap between our everyday intuition of motion (that it eventually stops) and Newton's first law (that an object in motion remains in motion, unless acted upon by an outside force). The 'outside force' that retards motion in the case many of everyday objects is indeed friction.
$\renewcommand{\vec}[1]{\mathbf{#1}}$
<!--more-->

![xkcd](https://imgs.xkcd.com/comics/experiment.png?style=centerme)
<center><i>Relevant xckd</i></center>

## Amontons' Laws of Dry Friction
The empirical laws that govern friction were (re)discovered by French physicist Guillaume Amontons:

- **Amontons' First Law**: The force of friction is directly proportional to the applied load.
  - The more an object is pushed into a surface (normal force) the more it interacts with that surface (friction).
- **Amontons' Second Law**: The force of friction is independent of the apparent area of contact.
  - While more surface area means more interactions with the surface (friction), having more area means the applied load is more distributed, offsetting the increase in area.
- Amontons' Third Law (**Coulomb's Law of Friction**): Kinetic friction is independent of the (magnitude of the) sliding velocity.
  - Kinetic friction takes over after static friction has been overcome and object starts to move, but once its in motion friction is constant.

## From Static to Kinetic Friction
There are two types of friction: static friction which acts on an object at rest, and kinetic friction which acts on an object in motion. When the force of static friction reaches a maximum, kinetic friction takes over:

![graph](/assets/physics/friction_graph.png?style=centerme){:width="500px"}

### Static Friction
An object at rest on a surface will resist motion on the surface until a certain maximum force has been reached. The magnitude of that max force is given by:

$$F_{s,max}=\mu_sN$$

- $F_{s,max}$ is the magnitude of the maximum force of static friction.
- $\mu_s$ is the coefficient of static friction.
- $N$ is the magnitude of the normal force on the object (the component of the total force on the object that is normal to the plane it's resting on).

At any other point before that max force has been reached, the force of static friction is equal in magnitude and opposite in direction to the component of the total force on the object that is parallel to the plane it's resting on, effectively canceling out any acceleration across the surface:

$$\vec{F_s}=-\vec{F_{\parallel}}$$

- $\vec{F_s}$ is the force of static friction.
- $\vec{F_\parallel}$ is the total force on the object parallel to the surface.

This parallel force can be described in terms of the normal force which is orthogonal to the surface:

$$\vec{F_{\parallel}}=\vec{F_{net}}-\vec{N}$$

- $\vec{F_{net}}$ is the total force applied to the object.
- $\vec{N}$ is the normal force on the object.

#### Work done by Static Friction
Notice that because static friction cancels out all motion across a particular surface, the force does not do any work (at least from the reference frame of the two surfaces).

### Kinetic Friction
An object in motion on a surface will experience kinetic friction that is proportional to the normal force on the object and independent of its velocity. The magnitude of this force is given by:

$$F_{k}=\mu_kN$$

- $F_{k}$ is the magnitude of the force of static friction.
- $\mu_k$ is the coefficient of kinetic friction.
- $N$ is the magnitude of the normal force on the object.

Kinetic friction is pointed in the opposite direction of the object's velocity:

$$\hat{\vec{F_k}}=-\hat{\vec{v}}$$

- $\hat{\vec{F_k}}$ is the unit vector of the object's velocity.
- $\hat{\vec{v}}$ is the unit vector of the object's velocity.

Putting these together we find that the force of kinetic friction is:

$$\vec{F_{k}}=-\mu_kN\hat{\vec{v}}=\frac{-\mu_kN}{\|\vec{v}\|}\vec{v}$$

*Note that this does not violate Coulomb’s Law of Friction as that refers only to the magnitude of kinetic friction.*

#### Non-Conservative Force and Thermal Energy
Friction is a non-conservative force, meaning that the work done by kinetic friction is dependent on the path taken. Friction also causes heat energy to be released into the system, meaning it does not conserve mechanical energy.

To calculate the thermal energy created by kinetic friction, a line integral through the path taken must be used:

$$E_{th}=\int_C\vec{F_k}(\vec{x})\cdot d\vec{x}$$

- $\vec{F_k}(\vec{x})$ is a vector field of the force of kinetic friction.
- $\vec{x}$ is the position of the object.
- $C$ is the path the object took.

## Coefficient of Friction
The proportionality constant between the frictional force and the normal force is called the coefficient of static/kinetic friction and is denoted $\mu_s$ and $\mu_k$ respectively. This constant differs depending on the 2 surfaces involved and, as a result of being a abstract approximation of complex interactions, cannot be derived from first principles and is instead measured empirically.

Below are some common coefficients of static and kinetic friction:
![table](http://hadron.physics.fsu.edu/~crede/TEACHING/PHY2048C/Calendar/W6_D1/Friction%20Coefficients_files/friction-coeffs.gif?style=centerme){:width="600px"}

![xkcd](https://imgs.xkcd.com/comics/mu.png?style=centerme)
<center><i>Yet another relevant xckd</i></center>

### Angle of Repose
When an object is placed on a ramp, the object will overcome static friction and slide down the ramp at some angle $\theta$. As it turns out, the tangent of this angle is equivalent to the coefficient of static friction:

![angle of repose](https://upload.wikimedia.org/wikipedia/commons/8/85/Free_body.svg?style=centerme)

<details><summary>Derivation</summary><p>

$$\begin{align*}
N=mg\cos\theta \tag{force normal to the ramp}\\
F_s=\mu_sN=mg\sin\theta \tag{static friction at the moment of slipping}\\
\mu_smg\cos\theta=mg\sin\theta\\
\mu_s=\frac{\sin\theta}{\cos\theta}=\tan\theta
\end{align*}$$</p></details>

$$\boxed{\tan\theta=\mu_s}$$
