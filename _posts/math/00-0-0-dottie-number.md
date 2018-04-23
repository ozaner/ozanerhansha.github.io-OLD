---
layout: post
title: The Dottie Number
date: 2018-04-16
tags: math
---
The Dottie number, which I will denote as $\textbf{d}$, is the only real solution to the following equation:

$$\cos x=x$$

![graph](https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/Dottie_number.svg/800px-Dottie_number.svg.png?style=centerme){:width="440px"}

The above is what's known as a transcendental equation. Equations like these usually return transcendental numbers and indeed $\textbf{d}$ is transcendental. It's decimal expansion is as follows:

$$\textbf{d}=0.7390851332151606...$$

*The Dottie number is sequence [A003957](https://oeis.org/A003957) in the OEIS.*

<!--more-->

### Fixed Point
$\textbf{d}$ is what's called a fixed point of $\cos x$, because the cosine function maps $\textbf{d}$ to itself. As a result, repeatedly taking the cosine of $\textbf{d}$ returns the same result:

$$\cos \textbf{d} = \textbf{d} \implies \underbrace{\cos\circ\cos\circ\cdots\circ\cos}_{n\text{ compositions}}\ \textbf{d}=\textbf{d}$$

$\textbf{d}$ is the $\cos$ function's only real fixed point, but there exists infinitely many solutions to $\cos z=z$ for the complex numbers. Those solutions, however, are not attractors.

### Universal Attractor
What's interesting about $\textbf{d}$ is that it's not just the real fixed point of $\cos$ but also its **universal fixed point attractor**. That is to say, if you take the cosine of any real number and repeatedly take the cosine of the result, you will always approach $\textbf{d}$:

$$\forall x\in\mathbb{R} \left(\lim_{n\to\infty} \underbrace{\cos\circ\cos\circ\cdots\circ\cos}_{n\text{ compositions}}\ x=\textbf{d}\right)$$

In fact, the above is true for a certain range of the complex numbers as well. This range forms the [*Julia Set*](https://en.wikipedia.org/wiki/Julia_set) of $\cos z$.

<details>
<summary><h3 class="inline">Proof of Transcendence </h3></summary>

<h4>LWT</h4><p>
To prove $\textbf{d}$'s transcendence, we'll need to make use of the <b><a href="https://en.wikipedia.org/wiki/Lindemann%E2%80%93Weierstrass_theorem">Lindemann–Weierstrass theorem</a></b> (LWT) which states:

$$\forall x\in \mathbb{A}\left(x\not= 0\implies e^x\notin\mathbb{A} \right)$$

Or in English: $e$ to the power of any non-zero algebraic number is not algebraic (i.e transcendental).
</p>

<h4>Lemma 1</h4><p>
The proof will be easier if we first establish the following identity:

$$\begin{align*}
\sin^2 \textbf{d}+\cos^2 \textbf{d} = 1 \tag{Pythagorean theorem}\\
\sin^2 \textbf{d}+ \textbf{d}^2 = 1 \tag{\(\textbf{d}\) is a fixed point}\\
\sin \textbf{d} = \sqrt{1-\textbf{d}^2}
\end{align*}$$
</p>

<h4>The Proof</h4><p>
Now we can prove $\textbf{d}$'s transcendence using Lemma 1 and LWT:

$$\begin{align*}
e^{i\textbf{d}}&=\cos \textbf{d} + i \sin \textbf{d} \tag{Euler's formula}\\
&=\textbf{d}+i\sin \textbf{d} \tag{\(\textbf{d}\) is a fixed point}\\
&=\textbf{d}+i\sqrt{1-\textbf{d}^2} \tag{Lemma 1}
\end{align*}
$$

$$\boxed{e^{i\textbf{d}}=\textbf{d}+i\sqrt{1-\textbf{d}^2}}$$

Let us assume that $\textbf{d}$ is algebraic. If this is the case then:

$$\left(\textbf{d}+i\sqrt{1-\textbf{d}^2}\right) \in \mathbb{A}$$

This is because it consists solely of algebraic numbers $\left(\textbf{d},i,1\right)$ and basic algebraic operations $\left(+,-,\times,x^2,\sqrt{x}\right)$ and thus must be root of a polynomial with rational coefficients (i.e algebraic).<p></p>

However, also assuming $\textbf{d}$ is algebraic, LWT tells us:

$$e^{i\textbf{d}}\notin \mathbb{A}$$

Since the right side of the boxed equation is algebraic yet LWT guarantees that the left side is transcendental (because $i\textbf{d}$ is algebraic), we are left with a contradiction. Meaning our initial assumption, that $\textbf{d}$ is algebraic, was false. Via <i>reductio ad absurdum</i> we can conclude:

$$\begin{align}
&e^{i\textbf{d}}=\textbf{d}+i\sqrt{1-\textbf{d}^2} \tag{Euler's formula}\\
&e^{i\textbf{d}}\notin \mathbb{A} \tag{LWT}\\
&\left(\textbf{d}+i\sqrt{1-\textbf{d}^2}\right) \in \mathbb{A} \tag{def. of algebraic number}\\
\therefore\ &\hline{\textbf{d}\notin \mathbb{A}} \tag{q.e.d}\\
\end{align}$$

</p></details>

### Kaplan's Series
[Kaplan](https://www.maa.org/sites/default/files/Kaplan2007-131105.pdf) proved that $\textbf{d}$ is equivalent to the following series:

$$\textbf{d} = \sum_{n=0}^{\infty}\ g^{\left(n\right)}\left(\frac{\pi}{2}\right)\frac{\left(-\pi\right)^n}{2^nn!}$$

Where the $g^{\left(n\right)}$ is the $n$th derivative of $f^{-1}$:

$$g^{\left(n\right)}\left(x\right)=\frac{d^n}{dx^n}f^{-1}\left(x\right)$$

and $f^{-1}$ is the inverse of the function $f$ which is defined as:

$$f\left(x\right)=x-\cos x$$

*We define it in this roundabout way because there is no explicit definition of $f^{-1}\left(x\right)$. This makes the construction of Kaplan's series all the more interesting.*

Written out, the series looks something like this:

$$\textbf{d} = \frac{\pi}{4} - \frac{\pi^3}{768} - \frac{\pi^5}{61440} - \frac{43\pi^7}{165150720} - \cdots$$

We can write this more succinctly (and as Kaplan originally proved) as so:

$$\textbf{d} = \sum_{n=0}^{\infty}a_n\pi^{2n+1}$$

Where $a_n$ is a sequence of rational numbers found by solving the above equation.

<!-- Proof of Kaplan's Series -->
<details>
  <summary><h3 class="inline">Proof of Kaplan's Series</h3></summary>
  <h4>Taylor Series of $f^{-1}$</h4>
  <p>
    To start off with, consider a function $f$ that is defined as such:

    $$f\left(x\right)=x-\cos x$$

    Kaplan was able to construct his series by noticing a few interesting properties of this function and it's inverse $f^{-1}$ (which has no explicit definition). The first of which was it's zero:

    $$\begin{align}
    f\left(\textbf{d}\right)&=\textbf{d}-\cos \textbf{d}\\
    &= \textbf{d}-\textbf{d}\\
    &= 0
    \end{align}$$

    This implies the following about $f^{-1}$ it's inverse:

    $$f^{-1}\left(0\right) = \textbf{d}$$

    And before we move on let's rename $f^{-1}$ to $g$ to make things less cluttered:

    $$f^{-1}\left(x\right) = g\left(x\right)$$

    We now have an expression for $\textbf{d}$. It is simply the value of $g\left(0\right)$. We currently do not have an explicit definition for $g\left(x\right)$ but we can create one via a Taylor series:

    $$g\left(x\right)=\sum_{n=0}^{\infty}g^{\left(n\right)}\left(c\right)\frac{\left(x-c\right)^n}{n!}$$

    - $g^{\left(n\right)}\left(x\right)$ is the $n$th derivative of $g\left(x\right)$
    - $c$ is the point we are constructing the Taylor series about. Since we are letting $n\to\infty$ the choice of constant won't affect the outcome.
  </p>

  <!-- Fixed Point -->
  <h4>Fixed point of $f$ and $g$</h4>
  <p>
    So now let us choose a value of $c$ that will be easy to compute. Notice that:

    $$\begin{align}
    f\left(\frac{\pi}{2}\right)&=\frac{\pi}{2}-\cos \frac{\pi}{2}\\
    &= \frac{\pi}{2}-0\\
    &= \frac{\pi}{2}
    \end{align}$$

    This means that $\frac{\pi}{2}$ is a fixed point of $f$ and that the following is also true of its inverse $g$:

    $$g\left(\frac{\pi}{2}\right)=\frac{\pi}{2}$$
  </p>

  <!-- nth Derivative of f -->
  <h4>$n$th derivative of $f$</h4>
  <p>
    Also notice that finding the $n$th derivative of $f$ at $\frac{\pi}{2}$ is simple:

    $$\begin{align}
    f\left(x\right)&=x-\cos x\\
    f'\left(x\right)&=1+\sin x\\
    f''\left(x\right)&=\cos x\\
    &\vdots\\
    \left(\forall n>1\right)\ f^{(n)}\left(x\right)&=\frac{d^{n-2}}{dx^{n-2}}\cos x
    \end{align}$$

    Because the derivatives of $\cos x$ are cyclical, we only need to evaluate the next 3 derivatives after $f''\left(\frac{\pi}{2}\right)$. Doing this we can see the pattern:

    $$f^{(n)}\left(\frac{\pi}{2}\right)=\{\frac{\pi}{2}, 2,0,-1,0,1,0,-1,\cdots\}$$
  </p>

  <!-- nth Derivative of g -->
  <h4>$n$th derivative of $g$</h4>
  <p>
    Now knowing the $n$th derivative of $f$ at $\frac{\pi}{2}$, we can calculate the $n$th derivative of $g$ at $\frac{\pi}{2}$:

    $$\begin{align}
    f\left(g\left(x\right)\right)=x \tag{inverse func.}\\
    f'\left(g\left(x\right)\right)g'\left(x\right)=1 \tag{chain rule}\\
    g'\left(x\right)=\frac{1}{f'\left(g\left(x\right)\right)}
    \end{align}$$

    We can use the chain and product rules repeatedly to find the $n$th derivative of $g$. The second derivative, for example, can be computed by differentiated both sides of the above equation:

    $$\begin{align}
    f'\left(g\left(x\right)\right)g'\left(x\right)=1\\
    f'(g(x))g''(x) + f''(g(x))g'(x)^2 = 0\\
    f'(g(x))g''(x) = - f''(g(x))g'(x)^2\\
    g''(x) = \frac{-f''(g(x))g'(x)^2}{f'(g(x))}
    \end{align}$$

    <i>Repeated use of the chain rule can be generalized via the <a href="https://en.wikipedia.org/wiki/Faà_di_Bruno%27s_formula">Faà di Bruno's formula.</a></i>
  </p>

  <h4>Solving the Taylor Series</h4>
  <p>
    Using $\frac{\pi}{2}$ as our value of $c$, because $g^{(n)}(\frac{\pi}{2})$ is easy to compute, we can rewrite the Taylor series for $g$ as so:

    $$g\left(x\right)=\sum_{n=0}^{\infty}g^{\left(n\right)}\left(\frac{\pi}{2}\right)\frac{\left(x-\frac{\pi}{2}\right)^n}{n!}$$

    Since we are solving for $g(0)$ which equals $\textbf{d}$ we can plug it into the above series to arrive at:

    $$\textbf{d}=\sum_{n=0}^{\infty}g^{\left(n\right)}\left(\frac{\pi}{2}\right)\frac{\left(-\pi\right)^n}{2^nn!}$$

    Now we just have to solve for each of the terms in this sequence.

    <details>
      <summary>The zeroth term is equal to:</summary>
      $$g\left(\frac{\pi}{2}\right)\frac{\left(-\pi\right)^0}{2^00!}=\frac{\pi}{2}$$
    </details>

    <details>
      <summary>The first term is equal to:</summary>
      $$g'\left(\frac{\pi}{2}\right)\frac{\left(-\pi\right)^1}{2^11!}=\frac{-\pi}{4}$$

      Because $g'\left(\frac{\pi}{2}\right)$ can be found by plugging $\frac{\pi}{2}$ into the equation we solved earlier:

      $$\begin{align}
      g'\left(\frac{\pi}{2}\right)&=\frac{1}{f'\left(g\left(\frac{\pi}{2}\right)\right)}\\
      &=\frac{1}{f'\left(\frac{\pi}{2}\right)}\\
      &=\frac{1}{2}\\
      \end{align}$$
    </details>

    <details>
      <summary>The second term equals:</summary>

      $$g''\left(\frac{\pi}{2}\right)\frac{\left(-\pi\right)^2}{2^22!}=0$$

      Because $g''\left(\frac{\pi}{2}\right)$ can be found as such:

      $$\begin{align}
      g''(x) &= \frac{-f''(g(x))g'(x)^2}{f'(g(x))}\\
      &=\frac{-f''(\frac{\pi}{2})g'(\frac{\pi}{2})^2}{f'(\frac{\pi}{2})}\\
      &=-\frac{0 (\frac{1}{2})}{2}\\
      &=0
      \end{align}$$
    </details>

    Putting these terms together we find the following sequence:

    $$\textbf{d} = \frac{\pi}{2} - \frac{\pi}{4} + 0 - \frac{\pi^3}{768} + 0 - \frac{\pi^5}{61440} - \cdots$$

    One thing to note here are that all the even derivatives of $g(\frac{\pi}{2})$ are always $0$ meaning we can ignore all the even terms of the sequence.
    <p></p>
    Another thing to note is that we can simplify the first two terms in the series:

    $$\frac{\pi}{2}-\frac{\pi}{4}=\frac{\pi}{4}$$

    This allows us to rewrite the series as such:

    $$\textbf{d} = \frac{\pi}{4} - \frac{\pi^3}{768} - \frac{\pi^5}{61440} - \cdots$$

    This is what allows us (and Kaplan) to state the following:

    $$\textbf{d} = \sum_{n=0}^{\infty}a_n\pi^{2n+1}$$

    Where $a_n$ is a sequence of rational numbers.
    <p></p>

    <i>As a side note, to prove this we assumed that $g$ was infinitely differentiable which is required to created a Taylor series for it. This is in fact true, but it just wasn't proved above.</i>
  </p>
</details>

### Approximating the Dottie Number
#### Solve Kaplan's series
One way is to simply calculate a specified number of terms in Kaplan's series and sum them.

$$\begin{align}
\textbf{d} \approx \frac{\pi}{4} &= 0.7\color{red}{854\cdots}\\
\textbf{d} \approx \frac{\pi}{4} - \frac{\pi^3}{768} &= 0.7\color{red}{450\cdots}\\
\textbf{d} \approx \frac{\pi}{4} - \frac{\pi^3}{768} - \frac{\pi^5}{61440} &= 0.7\color{red}{400\cdots}\\
\textbf{d} \approx \frac{\pi}{4} - \frac{\pi^3}{768} - \frac{\pi^5}{61440} - \frac{43\pi^7}{165150720} &= 0.739\color{red}{2\cdots}
\end{align}$$

While this can provide a decent approximation, it is a very time consuming process and doesn't allow the approximator to skip ahead to a desired accuracy (i.e to within .01%). Moreover while this series converges to $\textbf{d}$, it does so relatively slowly. To get just 17 decimal places of accuracy, one would need to solve for 25 terms of the series:

$$\textbf{d}\approx 0.73908 51332 15160 64\color{red}{570 711495 ...}$$

#### Taylor Series of Cosine
Another way to approximate $\textbf{d}$ is to simply substitute Taylor polynomials of $\cos x$ for $\cos x = x$ and solve for the zero of the resulting polynomial:

$$\cos x = 1 - \frac{x^2}{2!} + \frac{x^4}{4!}- \frac{x^6}{6!}+\cdots$$

For the **second** degree Taylor polynomial:
$$1-\frac{x^2}{2!}=x \\
-\frac{x^2}{2}-x+1=0$$

Using the quadratic formula we find:

$$x = \sqrt{3}-1 = 0.73\color{red}{205\cdots}$$

For the **fourth** degree Taylor polynomial:
$$1-\frac{x^2}{2!}+\frac{x^4}{4!}=x \\
\frac{x^4}{24}-\frac{x^2}{2}-x+1=0$$

Using the [quartic formula](https://en.wikipedia.org/wiki/Quartic_function#General_formula_for_roots) we find:

$$x = 0.73\color{red}{557\cdots}$$

However, after the 3rd term, we run into a problem. [Abel's impossibility theorem](https://en.wikipedia.org/wiki/Abel–Ruffini_theorem) states that there is no generic solution to polynomial equations above degree 4. For these polynomials a root finding algorithm has to be applied to approximate the zeros of the function. But if we have to use an approximation (root finder) just to calculate our approximation (Taylor polynomial) we might as well use the root finder on the original function: $\cos x - x = 0$.

*You may have noticed I didn't include an exact representation of the quartic equation above. This is because, even though there exists a generic solution to quartic polynomials, it is crazily complex and not worth using practically. Click the [quartic](https://upload.wikimedia.org/wikipedia/commons/9/95/Quartic_Formula.jpg) link to see the equation in its entirety*

#### General Root Finding Algorithm
The only choice we have left is to use a general root, or zero, finding algorithm like [Newton's method](https://en.wikipedia.org/wiki/Newton%27s_method) or the [bisection method](https://en.wikipedia.org/wiki/Bisection_method) to calculate $\textbf{d}$ to a given accuracy.
