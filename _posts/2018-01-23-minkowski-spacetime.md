---
layout: post
title: Minkowski Spacetime
tags: physics
---
## What is Spacetime?
Before we talk about Minkowski Spacetime, we need to address what it means to combine space and time.

Imagine the Earth orbiting the sun. At every point in time it will be in a different point in its orbit:

![orbit2D](https://www.pitt.edu/~jdnorton/teaching/HPS_0410/chapters/spacetime/planet3d.gif?style=centerme)

If we stack these slices of time in a third (temporal) dimension, it would look like this:

![orbit3D](https://www.pitt.edu/~jdnorton/teaching/HPS_0410/chapters/spacetime/planet4d.gif?style=centerme)

<!-- *It looks similar to euler's formula, $e^{i\theta}=\cos \theta + i\sin\theta$, with space being the complex plane and time being the angle $\theta$. The imaginary part will come in handy later.* -->

This is an example of a 3D spacetime. It has 2 dimensions of space and 1 of time. Our universe has 3 space and 1 time dimension, making our spacetime (referred to as *Minkowski Spacetime*) 4 dimensional.

<!--more-->

#### Why do this?
Spacetime serves as a useful mathematical and intuitive model of the universe that we can use to reason about physics, particularly Einstein's special relativity. Indeed, it was Einstein's former teacher [Hermann Minkowski](https://en.wikipedia.org/wiki/Hermann_Minkowski) that came up with spacetime as a tool to understand his pupil's breakthrough theory.

## Definition
Formally speaking, Minkowski spacetime (which I'll simply refer to as *spacetime*) is an [algebraic structure](\2017\05\21\abstract-algebra) that represents space purely in mathematical terms. In particular it is a 4D [vector space](https://en.wikipedia.org/wiki/Vector_space).

Points in this space are represented by vectors and are referred to as **events**. The naming stems from the fact that these points represents both moments in time as well as locations in space.

<!-- Remove link to vector space wikipedia -->
<!-- *If you don't know what a vector space is, I've written a post about it [here](\2018\01\20\vector-spaces).* -->

An event, usually denoted $s$, is represented by a 4D vector where $x,y,z,t$ are real numbers:

$$s=(x,y,z,ict)$$

You may have noticed that the last coordinate, which corresponds to time, is multiplied by a factor of $ic$. $i$, as we know, is the imaginary unit and multiplying it by time makes the fourth coordinate an imaginary number. The fourth coordinate always being an imaginary number means that spacetime consists of 3 real spatial dimensions and one imaginary temporal dimension.

$c$ represents the speed of light (299,792,458 m/s) and when multiplied by a time value (like seconds) it gives the distance a photon would travel in that time. This is necessary to convert from time units to length units. It wouldn't really make sense to have a position vector with different units for dimensions, as we'll see...

#### An Example
Say you walk 2m forward out of your house, walk 3 meters to the right, and jump (an impressive) 1 meter into the air. Let's also say that at the moment you were 1 meter in the air, 6 seconds had passed.

Setting the event of you leaving your house as the origin, the coordinates of the event of you jumping in the air are:
* x = 2m (forward)
* y = 3m (to the right)
* z = 1m (in the air)
* t = 6s (had passed since you left the house)

Thus that event in spacetime is represented by the ordered quadruplet:

$$\begin{align*}
  s &= (2,3,1,6\text{c}i) \\
  &= (2,3,1,1.80i\times 10^9) \\
\end{align*}$$

Note that the time coordinate is much bigger in magnitude due to how large the speed of light is.

In this framework you can, loosely, consider 1 second to be equivalent to 299,792,458 imaginary meters.

## Proper Distance
The distance between two points in space is given as such:

$$\Delta d=\sqrt{(\Delta x)^2+(\Delta y)^2+(\Delta z)^2}$$

Where $\Delta x,\Delta y,\Delta z$ represent the distance between the two $x/y/z$ coordinates of the two points. (i.e $\Delta x = x_2 - x_1$)

But special relativity tells us that space and time are relative and so it might be useful to have a notion of 'distance' for events in space*time* and not just space.

This analogue is called **proper distance** (denoted $\Delta s$) and we obtain it just like we did the one above. Square each coordinate, add them together, and take that sum's square root:

$$\Delta s=\sqrt{(\Delta x)^2+(\Delta y)^2+(\Delta z)^2-\text{c}^2(\Delta t)^2}$$

This measure of 'distance' is similar to the standard spatial one, barring the strange looking last term $-\text{c}^2(\Delta t)^2$. Upon further consideration, however, this term makes just as much sense as the others:

$$\begin{align*}
(x)^2&=x^2 \\
(y)^2&=y^2 \\
(z)^2&=z^2 \\
(i\text{c}t)^2&=i^2\text{c}^2t^2=-\text{c}^2 t^2
\end{align*}$$

#### An Example
Say you fly a spaceship 3000km into space from earth (the origin), let's call that the y-axis, in the span of 1ms (this is a very fast spaceship).

So since earth is the origin these are the change in coordinates:
* $\Delta x = 0m$
* $\Delta y = 4000km = 4000000m$
* $\Delta z = 0m$
* $\Delta t = 1ms = .01s$

Thus the proper distance between the origin and that event in spacetime is:

$$\begin{align*}
  \Delta s &= \sqrt{0^2+(3.0\times 10^6)^2+0^2+((.01)\text{c}i)^2} \text{ meters} \\
  &= \sqrt{(4.0\times 10^6)^2+(2.997i\times 10^6)^2} \text { meters} \\
  &= \sqrt{(4.0\times 10^6)^2-(2.997\times 10^6)^2} \text { meters} \\
  &= 2.65\times 10^6 \text { meters} \\
\end{align*}$$

Remember this distance isn't through space but spacetime, so it doesn't have quite the same meaning as you may first think.

#### Proper Time
If you take a good look at the formula for proper distance you'll notice a problem: What if radicand is negative?

Take the example of jumping in the air form earlier. If we use the proper distance formula with it we get:

$$\begin{align*}
  \Delta s &= \sqrt{2^2+3^2+1^2+(6\text{c}i)^2} \text{ meters} \\
  &= \sqrt{4+9+1+(1.799i\times 10^9)^2} \text { meters} \\
  &= \sqrt{4+9+1-(1.799\times 10^9)^2} \text { meters} \\
  &= \sqrt{-3.236\times 10^{18}} \text { meters} \\
  &= 1.799i\times 10^9 \text { meters} \\
\end{align*}$$

While we did accept the idea of imaginary time earlier, we cannot accept an imaginary proper distance. I mean the whole point was to get rid of the imaginary part right? So where did we go wrong? Well as it turns out, spacetime is a bit more complicated than I first led on (how surprising).

Two events in spacetime have the property of being either spacelike seperated or timelike seperated. The difference between them is essentially whether the two events could be causally connected (they are close enough to be affected by a particle traveling at the speed of light). See [light cones](https://en.wikipedia.org/wiki/Light_cone) for more.

The proper distance is the formula used for *spacelike* separated events. Another quantity, known as [proper time](https://en.wikipedia.org/wiki/Proper_time), is used to measure the length between two *timelike* events in spacetime.

## Asides
What I've described in this post is a very basic notion of spacetime and how one may codify events in it. There are many more aspects of spacetime and events in it like 4-velocities (the spacetime equivalent to velocity), 4-accelerations, proper time, Lorentz transformations, etc.

Also note that our normal notion of distance and time still apply to spacetime. All that's different is the fact that space and time are not invariant. That is to say, the regular old spatial *distance* between two events can change depending on your reference frame, but the *proper distance* between them is constant in all reference frames.

#### Regarding Imaginary Time
You may have felt a little uneasy when I introduced time as being an "imaginary 4th dimension" of spacetime or a second being equivalent to 299,792,458 imaginary meters. If so, you aren't alone. Physicists aren't so fond of concepts like imaginary time and so they've devised ways of getting around that, namely with something called a [metric signature](https://en.wikipedia.org/wiki/Metric_signature).

This has its benefits but, for our purposes, Minkowski spacetime is easier to understand if we consider time to be an imaginary dimension. It melds well with the definition of proper length.

Moreover, I think considering time as an imaginary dimension provides a useful analogy for its ephemeral nature. We can't *move* through time like we can through space. This is analogous to us not being able to directly measure imaginary quantities like we can with real ones.

<!-- #### Regarding Vector Spaces
Also while Minkowski Spacetime is generally considered a vector space, if the set of values that the coordinates come from aren't frost he same Field of numbers (the space coordinates come from the real numbers and the time coordinate comes from the imaginary numbers) then it technically can't be considered a vector space. This is another blow to the imaginary time version of spacetime. -->
