#Num Analysis

## Order of magnitude
We use $O(n^\alpha)$ to denote a variable that grows at rate $\alpha$. For example:

$$x_n=O(n^3)\implies \lim_{n\to\infty} \frac{x_n}{n^3}=c\not=0$$

Ex: Let $A$ be an $n\times n$ matrix and $\vec v$ an $n$-dim vector. Find the order of complexity of the following matrix multiplication:

$$A\cdot\vec v=
\begin{bmatrix}
    a_{11},&\cdots, &a_{1n}\\
    \vdots,&\ddots, &\vdots\\
    a_{n1},&\cdots, &a_{nn}\\
\end{bmatrix}\begin{bmatrix}
    a_{1}\\
    \vdots\\
    a_{n},\\
\end{bmatrix}$$

Each row requires $n$ multiplications and $n-1$ additions. So the complexity of all $n$ rows means that the time complexity of $A\cdot\vec v$ is:

$$n\cdot(n+(n-1))=2n^2-n=O(n^2)$$

When the time complexity of an numerical algorithm is polynomial, we call its **order of magnitude** the degree of that polynomial. In  this case this algorithm has a second order of magnitude.

## Order of Convergence
The **order of convergence** of a numerical algorithm is the degree of its error term (which will be a polynomial). Below is an example.

## Finite Difference Method
Used to approximate the derivative of a function $f(x)$. Consider the definition of the derivative:

$$f'(x)=\lim_{h\to 0}\frac{f(x+h)-f(x)}{h}$$

So it would seem that by simply choosing a small value of $h$, called the *step size*, we can approximate the derivative of $f$ at some point $x_0$. We can either add, or subtract for negative, $h$ to attain the *forward difference*:

$$f'(x_0)\approx\frac{f(x_0+h)-f(x_0)}{h}$$

or the average of adding and subtracting the two, *the central difference*:

$$f'(x_0)\approx\frac{f(x_0+h)-f(x_0-h)}{2h}$$

Which method is better? Assuming $f(x)$ is smooth, we can write the McLaurin series of both $f(x+h)$ and $f(x-h)$:

$$f(x+h)=f(x)+f'(x)h+\frac{f''(x)}{2!}h^2+\cdots$$
$$f(x-h)=f(x)-f'(x)h+\frac{f''(x)}{2!}h^2+\cdots$$

Now we see that the first method equals:

$$\frac{f(x+h)-f(x)}{h}=\underbrace{f'(x)}_{\text{derivative}}+\underbrace{\frac{f''(x)}{2!}h+\frac{f'''(x)}{3!}h^2+\cdots}_{\text{error(h)}}$$

As we can see the complexity of the error is linear in $h$:

$$\text{error(h)}\in O(h)$$

We call this *first order convergence*. However, when we compute the error of the central difference:

$$\frac{f(x+h)-f(x-h)}{2h}=\underbrace{f'(x)}_{\text{derivative}}+\underbrace{\frac{f'''(x)}{3!}h^2+\frac{f^{(5)}(x)}{5!}h^4+\cdots}_{\text{error(h)}}$$

In this case, the complexity of the error is quadratic in $h$:

$$\text{error(h)}\in O(h^2)$$

We call this a *second order convergence*. We can conclude then that with the same step-size $h$, the central difference method gives a better approximation than that of the forward difference, despite both methods having the same runtime complexity.

## Floating Point Standard
The floating point representation of a number $x\in\mathbb R$ has 3 parts:
- The **sign bit** $\sigma=\operatorname{sign}(x)$. The bit's value is given by $[x\lt 0]$.
- The **mantissa** ${(a_1a_2a_3a_4\cdots a_i)}_{2}$. This is the binary form of $|x|$ up to $i$ bits scaled such that it is between $0$ and $1$.
- The **exponential** $e=\log_2x$. This is how many binary places $x$ was scaled by to get the mantissa.

This means the formula for a floating point number with $n$ bits of precision is:

$$\operatorname{fl}(x)=\sigma\cdot(.a_1a_2a_3\cdots a_n)_ 2\cdot 2^e$$

#### Error
This approximation $\bar x$ introduces error in our representation of $x$. Recall that the absolute error is given by:

$$\text{absolute error}=x - \bar x$$

And the relative error is given by:

$$\text{relative error}=\frac{x - \bar x}{x}=\epsilon$$

Using this, we can bound the error introduced by the floating point standard:

$$\begin{align*}
\epsilon=\frac{x-\operatorname{fl}(x)}{x}&=\frac{\sigma\cdot(.000\cdots a_{n+1}a_{n+2}\cdots)_2\cdot 2^e}{\sigma\cdot(.a_1a_2a_3\cdots)_ 2\cdot 2^e}\\
&=\frac{(.000\cdots a_{n+1}a_{n+2}\cdots)_2 }{(.a_1a_2a_3\cdots)_ 2}
\end{align*}$$

*Note that the true binary representation of $x$ is an infinite bitstring.*

We can bound this error by considering $a_n$ to be equal to $1$ and setting the rest of the bits to $0$:

$$(.000\cdots a_{n+1}a_{n+2}\cdots)_2\le(.000\cdots 100\cdots)_ 2=2^{-n-1}$$

This gives us:

$$\epsilon=\frac{2^{-n-1}}{(.a_1a_2a_3\cdots)_ 2}\ge 2^{-n-1}$$

#### Double Prescision
Scientific computing mostly uses the $64$-bit double precision float which allocates $n=52$ bits to the mantissa. The minimum error of this or its **unit roundoff** is:
$$\epsilon=\frac{x-\operatorname{fl}(x)}{x}\ge2^{-53}\approx 10^{-16}$$
