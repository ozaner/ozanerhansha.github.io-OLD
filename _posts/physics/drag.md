---
layout: post
title: Drag Force
date: 2018-03-27
tags: physics classical-physics classical-mechanics
---
### General Info
The drag force, or fluid friction, is a force that opposes the motion of an object through a fluid/gas, similar to dry [friction](\friction). It can also be used to describe the resistance between a fluid in another fluid.

When the fluid is air, we refer to the force as aerodynamic drag or "air resistance." When it's water we call it hydrodynamic drag.
$\renewcommand{\vec}[1]{\mathbf{#1}}$
<!--more-->

#### Non-Conservative Force
Like friction, the drag force is a non-conservative force meaning the work done by it is path dependent. And, also like friction, drag converts some energy into heat, thus it does not conserve mechanical energy.

### Drag Equation
The magnitude of the drag force is given by:

$$F_D=\frac{\rho C_D A v^2}{2}$$

- $F_D$ is the magnitude of the drag force.
- $\rho$ is density of the fluid.
- $C_D$ is the drag coefficient of the fluid.
- $A$ is the cross-sectional area of the object (or more accurately an orthographic projection of the object onto a plane perpendicular to the velocity).
- $v$ is the magnitude of the velocity.

The direction of drag is opposite to that of the object's velocity:

$$\hat{\vec{F_D}}=-\hat{\vec{v}}$$

Combining these two equations, we can write the drag force as:

$$\vec{F_D}=\frac{-\rho C_D A v^2}{2}\hat{\vec{v}}=\frac{-\rho C_D A\|\vec{v}\|}{2}\vec{v}$$

#### Power to Overcome Drag
We can find the power required to overcome the drag force by the dot product of drag and the velocity of the object. Since

$$P_d=\vec{F_D}\cdot\vec{v}=\frac{\rho v^3C_DA}{2}$$

#### Terminal Velocity


### Drag Coefficient
