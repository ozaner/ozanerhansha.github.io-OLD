---
layout: post
title: Dottie Number
date: 2018-04-15
tags: math
---
The Dottie number, which I will denote as $\textbf{d}$, is the only real solution to the following equation:

$$\cos x=x$$

![graph](https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/Dottie_number.svg/800px-Dottie_number.svg.png?style=centerme){:width="440px"}

The above is what's known as a transcendental equation. Equations like these usually return transcendental numbers and indeed $\textbf{d}$ is transcendental. It's decimal expansion is as follows:

$$\textbf{d}=0.7390851332151606...$$

*The Dottie number is sequence [A003957](http://oeis.org/A003957) in the OEIS.*

<!--more-->

### Fixed Point
$\textbf{d}$ is what's called a fixed point of $\cos x$, because the cosine function maps $\textbf{d}$ to itself. As a result, repeatedly taking the cosine of $\textbf{d}$ returns the same result:

$$\cos \textbf{d} = \textbf{d} \implies \underbrace{\cos\circ\cos\circ\cdots\circ\cos}_{n\text{ iterations}}\ \textbf{d}=\textbf{d}$$

$\textbf{d}$ is the $\cos$ function's only real fixed point, but there exists infinitely many solutions to $\cos z=z$ for the complex numbers. Those solutions, however, are not attractors.

### Universal Attractor
What's interesting about $\textbf{d}$ is that it's not just the real fixed point of $\cos$ but also its **universal fixed point attractor**. That is to say, if you take the cosine of any real number and repeatedly take the cosine of the result, you will always approach $\textbf{d}$:

$$\forall x\in\mathbb{R} \left(\lim_{n\to\infty} \underbrace{\cos\circ\cos\circ\cdots\circ\cos}_{n\text{ iterations}}\ x=\textbf{d}\right)$$

In fact, the above is true for a certain range of the complex numbers as well. This range forms the [*Julia Set*](https://en.wikipedia.org/wiki/Julia_set) of $\cos z$.

<!-- ### Proof of Transcendence

#### LWT
To prove $\textbf{d}$'s transcendence, we'll need to make use of the [**Lindemann–Weierstrass theorem**](https://en.wikipedia.org/wiki/Lindemann%E2%80%93Weierstrass_theorem) (LWT) which states:

$$\forall x\in \mathbb{A}\left(x\not= 0\implies e^x\notin\mathbb{A} \right)$$

Or in English: $e$ to the power of any non-zero algebraic number is not algebraic (i.e transcendental).

#### Lemma 1
The proof will be easier if we first establish the following identity:

$$\begin{align*}
\sin^2 \textbf{d}+\cos^2 \textbf{d} = 1 \tag{Pythagorean theorem}\\
\sin^2 \textbf{d}+ \textbf{d}^2 = 1 \tag{\(\textbf{d}\) is a fixed point}\\
\sin \textbf{d} = \sqrt{1-\textbf{d}^2}
\end{align*}$$

#### The Proof
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

This is because it consists solely of algebraic numbers and operations $\left(\textbf{d},i,1,+,-,x^2,\sqrt{x}\right)$ and thus is a root of a polynomial with integer coefficients (i.e algebraic).

However, also assuming $\textbf{d}$ is algebraic:

$$e^{i\textbf{d}}\notin \mathbb{A} \tag{LWT}$$

Since the right side of the boxed equation is algebraic yet LWT guarantees that the left side is transcendental (because $i\textbf{d}$ is algebraic), we are left with a contradiction. Meaning our initial assumption, that $\textbf{d}$ is algebraic, was false. Via *reductio ad absurdum* we can conclude:

$$\therefore\textbf{d}\notin \mathbb{A}\\ \tag{q.e.d}$$ -->

<details>
<summary><h3 class="inline"> Proof of Transcendence </h3></summary>

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

This is because it consists solely of algebraic numbers and operations $\left(\textbf{d},i,1,+,-,x^2,\sqrt{x}\right)$ and thus is a root of a polynomial with integer coefficients (i.e algebraic).

However, also assuming $\textbf{d}$ is algebraic:

$$e^{i\textbf{d}}\notin \mathbb{A} \tag{LWT}$$

Since the right side of the boxed equation is algebraic yet LWT guarantees that the left side is transcendental (because $i\textbf{d}$ is algebraic), we are left with a contradiction. Meaning our initial assumption, that $\textbf{d}$ is algebraic, was false. Via <i>reductio ad absurdum</i> we can conclude:

$$\therefore\textbf{d}\notin \mathbb{A} \tag{q.e.d}$$
</p></details>

### Kaplan's Series
[Kaplan](https://www.maa.org/sites/default/files/Kaplan2007-131105.pdf) proved that $\textbf{d}$ is equivalent to the following series:

$$\begin{align}
\textbf{d} &= \sum_{n=0}^{\infty}a_n\pi^{2n+1}\\
&= \frac{\pi}{4} - \frac{\pi^3}{768} - \frac{\pi^5}{61440} - \frac{43\pi^7}{165150720} - \ \cdots
\end{align}$$

Where the sequence $a_n$ is:

$$a_n=\frac{d^{2n+1} u}{dx^{2n+1}}f^{-1}\left(0\right)$$

and $f^{-1}\left(x\right)$ is the inverse of the function $f\left(x\right)$ which is defined as:

$$f\left(x\right)=x-\cos x$$

*We define it in this roundabout way because there is no explicit definition of $f^{-1}\left(x\right)$. This makes the construction of Kaplan's series all the more interesting.*

#### Proof of Kaplan's Series
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

$$g\left(x\right)=\sum_{n=0}^{\infty}=g^{\left(n\right)}\left(c\right)\frac{\left(x-c\right)^n}{n!}$$

- $g^{\left(n\right)}\left(x\right)$ is the $n$th derivative of $g\left(x\right)$
- $c$ is the point we are constructing the Taylor series about. (Since we are letting $n\to\infty$ it doesn't matter what this constant is.)

So now let us choose a value of $c$ that will be easy to compute. Notice that:

$$\begin{align}
f\left(\frac{\pi}{2}\right)&=\frac{\pi}{2}-\cos \frac{\pi}{2}\\
&= \frac{\pi}{2}-0\\
&= \frac{\pi}{2}
\end{align}$$

This means that $\frac{\pi}{2}$ is a fixed point of $f$ and that the following is also true of its inverse $g$:

$$g\left(\frac{\pi}{2}\right)=\frac{\pi}{2}$$

Also notice that finding the $n$th derivative of $f$ at $\frac{\pi}{2}$ is simple:

$$\begin{align}
f\left(x\right)&=x-\cos x\\
f'\left(x\right)&=1+\sin x\\
f''\left(x\right)&=\cos x\\
&\vdots\\
\left(\forall n>1\right)\ f^{(n)}\left(x\right)&=\frac{d^{n-2}}{dx^{n-2}}\cos x
\end{align}$$

Because the derivatives of $\cos x$ are cyclical, we only need to evaluate the next 3 derivatives after $f''\left(\frac{\pi}{2}\right)$. Doing this we can see the pattern:

$$f^{(n)}\left(\frac{\pi}{2}\right)=\{2,0,-1,0,1,0,-1,\cdots\}$$

Rest of the proof under construction!

### Approximating the Dottie Number
Under construction!
<!-- taylor series quickly fails due to abels theorem

bisection theorem more reliable and can calculate error at any step -->
