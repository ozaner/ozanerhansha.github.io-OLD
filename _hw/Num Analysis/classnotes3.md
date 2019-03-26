## Least Square Data Fitting
Given a set of points in $\mathbb R^2$:

$$S=\{(x_i,y_i)\}_{i=1}^n$$

we want a function $f$ such that $f(x_i)\approx y_i$. With such a function, the error at the $i$th point is:

$$\epsilon_i=f(x_i)-y_i$$

The **root mean square error** of all points is

$$E=\sqrt{\frac{1}{n}\sum_{i=1}^n\epsilon_i^2}=\sqrt{\frac{1}{n}\sum_{i=1}^n(f(x_i)-y_i)^2}$$

The least square data fitting problem, then, is to find a function $f$ that minimizes that error $E$. Also, note that minimizing the above expression is equivalent to minimizing:

$$E^2n=\sum_{i=1}^n\epsilon_i^2=\sum_{i=1}^n(f(x_i)-y_i)^2$$

#### Linear Least Square
Consider $f$ of the form:

$$f(x)=mx+b$$

Now our task is to find $m$ and $b$ such that we minimize the following function $G$:

$$G(m,b)=\sum_{i=1}^n(mx_i+b-y_i)^2$$

We do this by setting $G$'s partial derivatives to $0$:

$$\frac{\partial G}{\partial m}=\sum_{i=1}^n2x_i(mx_i+b-y_i)=0$$

$$\begin{align*}
\frac{\partial G}{\partial b}&=\sum_{i=1}^n2\left(mx_i+b-y_i\right)=0\\
&=\sum_{i=1}^nmx_i+\sum_{i=1}^nb-\sum_{i=1}^ny_i\\
&=m\sum_{i=1}^nx_i+nb-\sum_{i=1}^ny_i\\
&\rightarrow m\sum_{i=1}^nx_i+nb=\sum_{i=1}^ny_i\\
\end{align*}$$

blah blah

#### More General LS Problem
Consider a linear combination a set of basis functions $\phi_i(x)$:

$$f(x)=a_1\phi_1(x)+a_2\phi_2(x)+\cdots$$

For example polynomials would use the basis $\{1,x,x^2,\cdots\}$. This results in a function $G$ which we must minimize:

$$G(a_1,a_2,\cdots)=\sum_{i=1}^n(a_1\phi_1(x_i)+a_2\phi_2(x_i)+\cdots-y_i)^2$$

To do this we set $G$'s partial derivatives to $0$:

$$\frac{\partial G}{\partial a_j}=2\sum_{i=1}^n(a_1\phi_1(x_i)+a_2\phi_2(x_i)+\cdots-y_i)=0$$

$$A\vec a=\vec b$$

## Polynomial Interpolation
Given a set of points $(x_i,y_i)$ give a polynomial $p(x)$ that fits all these points exactly.

It can be used to approximate a function $f$. If we have a set of known points of $f$ we can find an interpolating polynomial and then plug in our desired value.

#### Linear Interpolation
Given two points $(x_0,y_0), (x_1,y_1)$ the linear polynomial passing through them is:

$$p(x)=\frac{(x_1-x)y_0+(x-x_0)y_1}{x_1-x_0}$$

*Plug $x_0,x_1$ in to see why this works.*

#### Quadratic Interpolation
Given three points $(x_0,y_0)_ {i=0}^2$ the quadratic polynomial passing through them is:

$$p(x)=y_0L_0(x)+y_1L_1(x)+y_2L_2(x)$$

Where

$$L_0(x)=\frac{(x-x_1)(x-x_2)}{(x_0-x_1)(x_0-x_2)}$$

*Notice that plugging in $x_1,x_2$ return $0$, while $x_0$ returns $1$*

And the same for $L_1$ and $L_2$:

$$L_1(x)=\frac{(x-x_0)(x-x_2)}{(x_1-x_0)(x_1-x_2)}$$
$$L_2(x)=\frac{(x-x_0)(x-x_1)}{(x_2-x_0)(x_2-x_1)}$$

We call $L_1,L_2,L_3$ the quadratic Lagrange polynomials. They have the following property:

$$L_i(x_j)=\begin{cases}
1,\ \ \ \ \  i=j\\
0,\ \ \ \ \  i\not=j
\end{cases}$$

From here it is simple to see why we defined the quadratic interpolation as we did.

#### General Interpolation
In general, the $n$th degree polynomial interpolation given $n+1$ points is:

$$p(x)=y_0L_0(x)+\cdots+y_nL_n(x)$$

Where $L_i$ is the $n$th degree Lagrange polynomial:

$$L_0(x)=\frac{(x-x_1)(x-x_2)\cdots(x-x_n)}{(x_0-x_1)(x_0-x_2)\cdots(x_0-x_n)}$$

and in general:

$$L_i(x)=\prod_{j=0\\j\not=i}^n\frac{x-x_j}{x_i-x_j}$$

#### Complexity
2(n-2) additions, 2(n-3) multiplications per Lagrange polynomial, this times n-1 polynomials, n-1 multiplications of $y_i$ and $n-2$ additions of these terms.

4n^2-12n+7=O(n^2), not horrible I suppose.

Doing it by simply solving an $n$th degree polynomial via a linear system as opposed to using Lagrange polynomials is an $O(n^3)$ solution.
