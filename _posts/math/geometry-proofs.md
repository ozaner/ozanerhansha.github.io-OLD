---
layout: post
title: Miscellaneous Geometry Proofs
date: 2018-09-03
tags: math geometry
---
A collection of geometry proofs too specific to include in any other page. These proofs assume Euclidean real space $\mathbb{R}^3$.

<!--more-->

<p></p>
<details>
<summary><h3 class="inline">Distance from a Point to a Sphere</h3></summary>
Let's call the first point $\mathbf{P}$ and the point on the sphere closest to it $\mathbf{Q}$. This would make the distance between the point and sphere $\|\mathbf{P}-\mathbf{Q}\|$.
<p></p>

Notice that wherever $\mathbf{Q}$ is on the sphere, its distance from the center of the sphere $\mathbf{C}$ is equal to the radius $r$. This is the very definition of a sphere.
<p></p>

This means that the distance we are trying to find is:

$$\mathbf{P}-\mathbf{Q}=(\mathbf{P}-\mathbf{C})-r\mathbf{\hat{Q}}$$

because moving from $\mathbf{P}$ to $\mathbf{Q}$ is the same as moving from $\mathbf{P}$ to the center $\mathbf{C}$ and backtracking a radius' length in $\mathbf{Q}$'s direction.

<p></p><img src="/assets/math/point_to_sphere.png?style=centerme" style="width:300px;"><p></p>

However, because we are only concerned with the <i>distance</i> between the point and the sphere and not the <i>displacement</i> we can say:

$$\|\mathbf{P}-\mathbf{Q}\|=\|(\mathbf{P}-\mathbf{C})-r\mathbf{\hat{Q}}\|$$

We can simplify this further by noticing that because the vectors $(\mathbf{P}-\mathbf{C})$ and $r\mathbf{\hat{Q}}$ are pointed in the same direction, the following holds:

$$\begin{align}
\|(\mathbf{P}-\mathbf{C})-r\mathbf{\hat{Q}}\|
&=\left|\|(\mathbf{P}-\mathbf{C})\|-\|r\mathbf{\hat{Q}}\|\right| \\
&=\left|\|(\mathbf{P}-\mathbf{C})\|-r\right|
\end{align}$$

Thus shortest distance $d$ from a point $\mathbf{P}$ to a sphere with center $\mathbf{C}$ is independent of the actual point closest to the sphere and is given by the following:

$$d=\left|\|\mathbf{P}-\mathbf{C}\|-r\right|$$

<i>Note that this formula works even if $\mathbf{P}$ is inside the sphere. The inside of the absolute value will result in a negative distance, but that becomes positive once the absolute value is evaluated.</i>

It is the sphere's total symmetry which allows us to make the above statement. Computing the distance between a point and some arbitrary surface would be more difficult.
