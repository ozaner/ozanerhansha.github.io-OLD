Midterm April 23, one page cheat sheet, calculator is allowed

## Gaussian Quadrature
The idea is to use a higher order polynomial than linear (trapezoid) or quadratic (Simpson) to interpolate the function and integrate. To deal with the Runge phenomenon, we don't use equally distributed interpolation points.

#### Case I node
We have n+1 nodes, where n=0 so there is one node. We want to approximate:

...

don't get the derivation but the Guassian numerical integral for n=0, i.e. 1 point:

$$\int_{-1}^1f(x)\ dx\approx f(x)\cdot 2$$

#### Case 2 nodes
We have n+1 nodes, where n=1 so 2 nodes. We want to approximate the inegral of:

$$\int_{-1}^1f(x)\ dx\approx f(x_0)\cdot w_0+f(x_1)\cdot w_1$$

What are the 4 unknowns, such that the formula is as acuurate as possible? We have:

$$f(x)=c_1+c_2x+c_3x^2+c_4x^3$$

We make a system of 4 equations:

$$\begin{align*}
\int_{-1}^1f(x)\ dx&=\int_{-1}^1 c_1+c_2x+c_3x^2+c_4x^3\ dx\\
&=w_0(c_0+c_2x_0+c_3x^2_0+c_4x^3_0)\\
&+w_1(c_1+c_2x_1+c_3x^2_1+c_4x^3_1)\\
\end{align*}
$$

...

For n=1, 2 pts, we can approxiamte the integral from [-1,1] of f(x) by the following:

$$\int_{-1}^1 f(x)\ dx\approx f\left(-\sqrt{\frac{1}{3}}\right)\cdot 1+f\left(\sqrt{\frac{1}{3}}\right)\cdot 1$$

#### General case
In general to find the n+1 weights and nodes that make the following the closest:

$$\int_{-1}^1f(x)\ dx\approx\sum_{i=0}^n f(x_i)\cdot w_i$$

We find the $x_i$ and $w_i$ such that the following equation is exactly true:

$$\int_a^b p(x)\ dx=\sum_{i=0}^n p(x_i)\cdot w_i$$

where $p(x)$ is a polynomial of degree $2n+1$:

$$p(x)=c_0+c_1x+c_2x^2+\cdots c_{2n+1}x^{2n+1}$$

Our equations are:

$$w_0+w_1+\cdots w_n=\int_{-1}^1 1\ dx=2$$
$$w_0x_0+w_1x_1+\cdots w_nx_n=\int_{-1}^1 x\ dx=0$$
$$w_0x_0^2+w_1x_1^2+\cdots w_nx_n^2=\int_{-1}^1 x^2\ dx=\frac{2}{3}$$
$$\cdots$$
$$w_0x_0^{2n+1}+w_1x_1^{2n+1}+\cdots w_nx_n^{2n+1}=\int_{-1}^1 x^{2n+1}\ dx$$

For this class we'll only need the following weights and nodes (for n=0,1,2) using the Gussian-Legandre method is:

$$f(0)\cdot 2$$
$$f\left(-\sqrt{\frac{1}{3}}\right)+f\left(\sqrt{\frac{1}{3}}\right)$$
$$\frac{5}{9}f\left(-\sqrt{\frac{3}{5}}\right)+\frac{8}{9}f(0)+\frac{5}{9}f\left(\sqrt{\frac{3}{5}}\right)$$

Look online for the weights and nodes for other n.

#### Change of interval of integration

$$\int_a^b f(x)\ dx=\frac{b-a}{2}\int_{-1}^1$$

#### Example

Approximate
