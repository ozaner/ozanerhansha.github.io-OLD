---
layout: post
title: Position
date: 2018-03-15
tags: physics classical-physics classical-mechanics
---
The position of a particle or object in **space** is defined as a point on an n-dimensional **Cartesian coordinate system**. This point can equivalently be thought of as a vector.

### Classical Physics
In classical physics, a position or displacement $\vec{x}$ is a 3-dimensional vector with components $\left(x,y,z\right)$.

*Position is used to refer to a specific point in a coordinate space while displacement refers to the distance traveled from an initial point (usually this point is the origin making position and displacement equivalent)*

The magnitude of displacement, or net **distance**, is calculated the same as any other vector:

$$\left|\vec{x}\right|=\sqrt{x^2+y^2+z^2}$$

#### Displacement Function
An object's position can be described as a function of time, $\vec{x}(t)$. This position function would thus map from time to 3D-space:

$$\vec{x}:\mathbb{R}\rightarrow \mathbb{R}^3$$

Taking the derivative of an object's displacement function with respect to $t$ provides the object's [velocity]() function, $\vec{v}(t)$:

$$\frac{\mathrm{d}}{\mathrm{d}t}\vec{x}(t)=\vec{v}(t)$$

<!--more-->

<!-- Click [here]() for a list of the repeated time derivatives of displacement. -->

### Relativity
In relativity, position is only invariant in a particular non-inertial reference frame. This necessitates a notion of position that is invariant with respect to space-time. This 4-dimensional position (3 spatial dimensions and 1 time) is called 4-position, or more commonly as an **event**.

An event is defined as a 4-dimensional vector with components $\left(t,x,y,z\right)$. Relativity shows that events that occur at the same time in one reference frame, don't necessarily happen at the same time in another. This is known as **relativity of simultaneity**.

In special relativity the distance between two positions is not invariant in different reference frames. This brings us to the **spacetime interval**. The spacetime interval, $(\Delta s)^2$ between two events stays constant in all reference frames:

$$(\Delta s)^2=(c\Delta t)^2-(\Delta x)^2-(\Delta y)^2-(\Delta z)^2$$

### Quantum Mechanics
In quantum mechanics, the state of a particle is given, and completely described, by its **wavefunction** $\psi(\mathbf{x}, t)$. With $\mathbf{x}$ being a point in 3-space and $t$ being a point in time. $\psi$ returns a complex valued probability amplitude.

$$\psi:\mathbb{R^4}\rightarrow \mathbb{C}$$

The probability of observing a particle, in the one dimensional case, at position $x$ at time $t$ is given by $\left \vert \psi \right \vert^2$. This implies that for a given time $t$:

$$\int_{-\infty}^{\infty}\left | \psi(x) \right |^2 dx=1$$

Because the particle has to be somewhere in space, the probabilities must sum to 1. We integrate from $-\infty$ to $\infty$ since the particle is a wave spread out over all of space. With some vector calculus, this can extended to the 3D case we see in the real world.