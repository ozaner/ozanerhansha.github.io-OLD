---
layout: post
title: Circles in the Lp Norm
tags: math
---
## What is a Circle?
A circle is simply the set of points that are an equal distance, **equidistant**, from a certain central point:

![circlepoints](https://www.mathsisfun.com/sets/images/set-of-points.gif?style=centerme)

If we set the origin as our center point, we can find the distance between it and another point on a flat plane via:

$$d=\sqrt {x^2+y^2}$$

Where $x$ and $y$ are the coordinates of the point, and $d$ is the point's distance from the origin.

This idea of distance extends to any number of dimensions, and we can accommodate for it by simply adding another squared term for every new dimension:

$$\left | x \right |=\sqrt {x_1^2+x_2^2+x_3^2+\cdots}$$

In the above definition we have some point, or **vector**, called $x$. The vector's length, or **magnitude**, is denoted $\left | x \right |$. The components of the vector are denoted $x_1$ to $x_n$ where $n$ is the vector's dimensionality.

## Taxicab Metric
But there's a big assumption in our definition of the circle: distance. While we usually use what's called the Euclidean norm (the formula used above), there are other valid notions of distance we could have used instead.

Take, for example, the taxicab metric:

$$\left | \left | x \right | \right |1 = \left | x_1 \right |+\left | x_2 \right | + \left | x_3 \right | + \cdots$$

*Notice we didn't use the notation $|x|$ because this isn't the standard definition of distance. The new notation will be explained further down below*

The equation above describes distance in the way you'd encounter it in a big city, like Manhattan (in fact this metric is also referred to as *Manhattan distance*). You can't move through buildings, so you move across avenues (x axis) and streets (y axis):

![taxicab dist](http://bloggity.nurdz.com/wp-content/uploads/2015/01/Manhattan.png?style=centerme)

*The green line represents the standard Euclidean distance, while the blue, red, and yellow lines all represent the taxicab distance.*

Notice that there are multiple paths that give the same minimum distance in the taxicab metric (yellow, red and blue all have the same length), while the Euclidean metric has only one shortest path.

## $L^p$ Metric
As it turns out, the taxicab metric and the Euclidean metric can both be generalized into a new type of metric: the $L^p$ Norm:

$$\left | \left | x \right | \right |p = \left( \left | x_1 \right |^p + \left | x_2 \right |^p + \left | x_3 \right |^p + \cdots \right )^{\frac{1}{p}}$$

The magnitude of a vector in the $L^2$ norm, for example would look like this:

$$\begin{align*}
\left | \left | x \right | \right |2 &= \left( \left | x_1 \right |^2 + \left | x_1 \right |^2 + \left | x_1 \right |^2 + \cdots \right )^{\frac{1}{2}} \\
&= \left(x_1^2 + x_2^2 + x_3^2 + \cdots \right )^{\frac{1}{2}} \\
& = \sqrt {x_1^2+x_2^2+x_3^2+\cdots}
\end{align*}$$

Would you look at that, the Euclidean metric is the same thing as the $L^2$ norm. The same can be done with the taxicab, or $L^1$, metric:

$$\begin{align*}
\left | \left | x \right | \right |1 &= \left( \left | x_1 \right |^1 + \left | x_1 \right |^1 + \left | x_1 \right |^1 + \cdots \right )^{\frac{1}{1}} \\
&= \left(\left | x_1 \right | + \left | x_2 \right | + \left | x_3 \right | + \cdots \right )^{1} \\
& = \left | x_1 \right | + \left | x_2 \right | + \left | x_3 \right | + \cdots
\end{align*}$$

## Circles in $L^p$ Space
Going back to our definition of a circle, if we graph all the points that are equidistant from each other using these new metrics, we get some interesting results:



#### Fractional P
What's also interesting, but should make some intuitive sense, is that if we graph circles of fractional p we get shapes that are more and more concave as opposed to convex

## π ≠ π?

## Why 2?
<!-- #### Orientation
The circle is symmetrical on all sides, it has total rotational symmetry. The other norms, however are not. So what?
Well in nature, it shouldn't matter what direction I walk -->

#### Minimum Circle Constant


#### Nature


Goes along with the others but, appears how distyance work sin the real world. only natural taht we use it here
