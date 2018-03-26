---
layout: post
title: Friction
date: 2018-03-26
tags: physics classical-physics classical-mechanics
---
$\renewcommand{\vec}[1]{\mathbf{#1}}$
Dry Friction is a force that opposes the motion of two surfaces that slide against each other. This force is proportional to the normal force (that is the total force perpendicular to the direction of motion) of the object.

#### Where does Friction come from?
The frictional force is not fundamental and is instead a useful abstraction of the complex electromagnetic interactions between two surfaces that come into contact with each other. These force created by these interactions can, in a variety of cases, be thought of as a singular force that is proportional to the normal force.

![complexfriction](/assets/physics/friction_between_surfaces.jpg?style=centerme){:width="450px"}

#### Intuition and Newton's First Law
The frictional force is responsible for filling the gap between our everyday intuition of motion (that it eventually stops) and Newton's first law (that an object in motion remains in motion, unless acted upon by an outside force). The 'outside force' that retards motion in the case many of everyday objects is indeed friction.

### Amontons Laws of Dry Friction
The empirical laws that govern friction were (re)discovered by French physicist Guillaume Amontons:

- **Amontons' First Law**: The force of friction is directly proportional to the applied load.
- **Amontons' Second Law**: The force of friction is independent of the apparent area of contact.
- Amontons' Third Law (**Coulomb's Law of Friction**): Kinetic friction is independent of the sliding velocity.

<!--more-->

### Coefficient of Friction
The proportionality constant of the frictional force and the normal force is called the coefficient of static/kinetic friction and are denoted $\mu_s$ and $\mu_k$ respectively. This constant differs depending on the 2 surfaces involved and, as a result of being a abstract approximation of complex interactions, cannot be derived from first principles and are instead measured empirically.

Below are some common coefficients of static and kinetic friction:
![table](http://hadron.physics.fsu.edu/~crede/TEACHING/PHY2048C/Calendar/W6_D1/Friction%20Coefficients_files/friction-coeffs.gif){:width="600px"}

## From Static to Kinetic Friction
There are two types of friction: static friction which acts on an object at rest, and kinetic friction which acts on an object in motion. When the force of static friction reaches a maximum, kinetic friction takes over:

![graph](http://3.bp.blogspot.com/-5pk-uJYub_Y/VFe1UdylnYI/AAAAAAAAFoI/8NyK6iU-GFo/s1600/graph-static-kinetic-friction.png?style=centerme){:width="500px"}

### Static Friction
An object at rest on a surface will resist motion on the surface until a certain maximum force has been reached. The magnitude of that max force is given by:

$$F_{s,max}=\mu_sN$$

- $F_{s,max}$ is the magnitude of the maximum force of static friction.
- $\mu_s$ is the coefficient of static friction.
- $N$ is the magnitude of the normal force on the object (the force normal to the object's direction of motion).

At any other point before that max force has been reached, the force of static friction cancels out the opposing forces parallel to the surface:

$$\vec{F_s}=\vec{F_{\parallel}}$$

The force parallel to the surface is simply the total force applied minus the normal force which is orthogonal to the surface:

$$\vec{F_{\parallel}}=\vec{F_{net}}-\vec{N}$$

- $\vec{F_\parallel}$ is the force parallel to the surface.
- $\vec{F_{net}}$ is the total force applied to the object.
- $\vec{N}$ is the normal force on the object.

Static friction is pointed in the opposite direction of the parallel force (so it can cancel out):

$$\frac{\vec{F_s}}{\vec{\|F_s\|}}=-\frac{\vec{F_{\parallel}}}{\|\vec{F_{\parallel}}\|}$$

#### Angle of Repose
When an object is placed on a ramp, the object will overcome static friction and slide down the ramp at some angle $\theta$. As it turns out the tangent of this angle is equivalent to the coefficient of static friction:

$$\tan \theta = \mu_s$$

![angle of repose](https://upload.wikimedia.org/wikipedia/commons/8/85/Free_body.svg?style=centerme)

<details><summary>Derivation</summary><p>$$\begin{align*}
N=-mg\cos\theta \tag{force normal to the ramp}\\
\mu_sN=-mg\sin\theta \tag{static friction at the moment of Slipping}\\
-\mu_smg\cos\theta=-mg\sin\theta\\
\mu_s=\frac{\sin\theta}{\cos\theta}=\tan\theta
\end{align*}$$

$$\boxed{\tan\theta=\mu_s}$$</p></details>

### Kinetic Friction
An object in motion on a surface will experience kinetic friction that is proportional to the normal force on the object and independent of its velocity. The magnitude of this force is given by:

$$F_{k}=\mu_kN$$

- $F_{k}$ is the magnitude of the force of static friction.
- $\mu_k$ is the coefficient of kinetic friction.
- $N$ is the magnitude of the normal force on the object.

Kinetic friction is pointed in the opposite direction of the object's velocity:

$$\frac{\vec{F_k}}{\|\vec{F_k}\|}=-\frac{\vec{v}}{\|\vec{v}\|}$$

- $\vec{F_k}$ is the force of kinetic friction.
- $\vec{v}$ is the object's velocity.

#### Non-Conservative Force and Thermal Energy
Friction is non-conservative force, meaning that the work done by kinetic friction is dependent on the path taken. Friction also causes heat energy to be released into the system, meaning it does not conserve mechanical energy.

To calculate the thermal energy created by kinetic friction, a line integral through the path taken must be used:

$$E_{th}=\int_C\vec{F_k}(\vec{x})\cdot d\vec{x}$$

- $\vec{F_k}$ is the force of kinetic friction.
- $\vec{x}$ is the position of the object.
- $C$ is the path the object took.
