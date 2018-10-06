---
layout: post
title: Bachmann–Landau Notation
date: 2018-09-28
tags: math computer-science
---
**Bachmann–Landau notation** is a collection of notations used to  classify the limiting behavior of a particular function as its argument tends towards a particular value or infinity. It, along with [asymptotic equivalence](\asymptotic-equivalence), make up the primary relations of **asymptotics**.

These notations, particularly big $O$, are most commonly used to classify and compare the computational complexity (both temporal and spatial) of different algorithms as a function of their input size.

Ideally, an algorithm will be on the order of a relatively slowly growing function (e.g $\log n$ grows slower than $n^2$) as they take less resources and thus are more feasible to compute.

<!--more-->

## Formal Definitions
There are 5 related notations that fall under the umbrella of Bachmann–Landau:

| Notation               | Name            | Comparison |
|------------------------|-----------------|------------|
| $f(n)\in o(g(n))$      | Little-$o$      | $\lt$      |
| $f(n)\in O(g(n))$      | Big-$O$         | $\le$      |
| $f(n)\in \Theta(g(n))$ | Big-$\Theta$    | $=$        |
| $f(n)\in \Omega(g(n))$ | Big-$\Omega$    | $\ge$      |
| $f(n)\in \omega(g(n))$ | Little-$\omega$ | $\gt$      |

The comparison describes $f$'s behavior with respect to $g$ as $x\to c$ where $c$ could be a particular value or infinity. For the definitions we will assume $c$ is $\infty$ as that is the most common use case of asymptotic notation.

More concretely, this notation is based off $f$ being a member of some set defined by $g$. How these sets are defined for each notation is elaborated below via two similar (but not quite equivalent) formalizations of the concept:

<details>
<summary><h4 class="inline">Growth Definitions</h4></summary>
A function $f(x)$ is big $O$ of $g(x)$, i.e $f(x)\in O(g(x))$, if the following holds:

$$f(x)\in O(g(x))\equiv (\exists k,x_0)\ x\ge x_0\rightarrow f(x)\le kg(x)$$

This means that there is some point such that for all $x$ after it, $f(x)$ is less than or equal to $g(x)$ up to some constant.

The definitions for the other notations are similar:

$$\begin{align}
f(x)\in o(g(x))&\equiv \left(\forall k,\exists x_0\right) x\ge x_0&&\rightarrow f(x)\lt kg(x)\\
f(x)\in O(g(x))&\equiv \left(\exists k,x_0\right) x\ge x_0&&\rightarrow f(x)\le kg(x)\\
f(x)\in \Theta(g(x))&\equiv \left(\exists k_1,k_2,x_0\right) x\ge x_0&&\rightarrow k_1g(x)\le f(x)\le k_2g(x)\\
f(x)\in \Omega(g(x))&\equiv \left(\exists k,x_0\right) x\ge x_0&&\rightarrow f(x)\ge kg(x)\\
f(x)\in \omega(g(x))&\equiv \left(\forall k,\exists x_0\right) x\ge x_0&&\rightarrow f(x)\gt kg(x)
\end{align}$$

*Where $f,g:\mathbb{R}\to\mathbb{R}$ and $x,x_0,k,k_1,k_2\in\mathbb{R}.$*
</details>

<details>
<summary><h4 class="inline">Limit Definitions</h4></summary>
We can also define asymptotic notation via limits. Doing so comes with added stipulations about limit existence and so on but if those conditions are met, we can define them as so:

$$\begin{align}
f(x)\in o(g(x))&\equiv \lim_{x\to\infty}\frac{f(x)}{g(x)}=0\\
f(x)\in O(g(x))&\equiv \limsup_{x\to\infty}\left|\frac{f(x)}{g(x)}\right|\lt\infty\\
f(x)\in \Theta(g(x))&\equiv (\exists k)\lim_{x\to\infty}\frac{f(x)}{g(x)}=k\\
f(x)\in \Omega(g(x))&\equiv \liminf_{x\to\infty}\left|\frac{f(x)}{g(x)}\right|\gt 0\\
f(x)\in \omega(g(x))&\equiv \lim_{x\to\infty}\left|\frac{f(x)}{g(x)}\right|=\infty
\end{align}$$
</details>

## Big $O$ vs. $\Omega$ vs. $\Theta$
### Big $O$
Big $O$, the most used notation, describes what is called the **upper-bound complexity** of an algorithm. Thus a function $f$ that is big $O$ of a function $g$ grows as fast or slower than $g$ (up to a constant). When a function $f$ is **'of the order'** $g$ this means that it is big $O$ of $g$ and not any other notation.

#### Popularity
While big $\Theta$ is the most descriptive of the 3 notations, it is not as popular as big $O$. Why is this? Well, it is in part due to laziness and convention.

However there is a more practical reason for this as well. Proving something is big $\Theta$ means proving it is both big $O$ and big $\Omega$ which may be much more difficult or even impossible compared to just proving one or the other.

As a result of this, it is generally expected that when someone states an algorithm is $O(g(x))$ that $g(x)$ is as small as they could make it. This makes it a tighter bound when possible but doesn't enforce it incase such a bound is not possible to prove.

#### Common Orders
Below is a table of common terminology for certain lower-bound complexity classes (from smallest to largest):

| Complexity Class | Notation           |
|------------------|--------------------|
| Constant         | $O(1)$             |
| Logarithmic      | $O(\log n)$        |
| Polylogarithmic  | $O((\log n)^k)$    |
| Fractional Power | $O(n^k)_{\ 0<k<1}$ |
| Linear           | $O(n)$             |
| Linearithmic     | $O(n\log n)$       |
| Quadratic        | $O(n^2)$           |
| Polynomial       | $O(n^k)_{\ k>1}$   |
| Exponential      | $O(k^n)_{\ k>1}$   |
| Factorial        | $O(n!)$            |

<details>
<summary><h3 class="inline">Big $\Omega$</h3></summary>
This contrasts with big $\Omega$ which describes the <b>lower-bound complexity</b> of an algorithm. So a function $f$ that is big $\Omega$ of a function $g$ grows as fast or faster than $g$ (up to a constant).
<p></p>
</details>

<details>
<summary><h3 class="inline">Big $\Theta$</h3></summary>
Big $\Theta$, on the other hand, is known as a <bf>tight bound</bf> on the complexity of an algorithm and can be equivalently stated as:

$$f(x)\in\Theta(g(x))\equiv f(x)\in O(g(x))\wedge f(x)\in\Omega(g(x))$$

And so, following the pattern, a function $f$ that is big $\Theta$ of a function $g$ grows as fast as $g$ (up to a constant).

<h4>Equivalence Relation</h4>
Note that, unlike big $O$ and $\Omega$, the relation $f(x)\in\Theta(g(x))$ forms an equivalence relation given some function $g$.

<details>
<summary><strong>Reflexivity</strong></summary>
I'll do this later.
</details>

<details>
<summary><strong>Symmetry</strong></summary>
I'll do this later.
</details>

<details>
<summary><strong>Transitivity</strong></summary>
I'll do this later.
</details>

<h4>Asymptotic Equivalence</h4>
Another interesting point is that $f(x)\in\Theta(g(x))$ is actually a more general case of $f(x)\sim g(x)$ where $\sim$ is <a href="\asymptotic-equivalence#relation-to-algorithmic-complexity">asymptotic equivalence</a>. This should come as no surprise. After all, $f$ and $g$ are asymptotically equal up to a constant, and so if that constant happened to be $1$ we would be left with asymptotic equivalence.
</details>

## Regarding Notation
The use of the Bachmann–Landau notations is, unfortunately, quite varied and oftentimes informal. As such, I will try to clear up some of the nuance packed into these notations.

#### Terminology
When someone refers to the complexity of an algorithm without context they are assumed to be referring to its temporal, rather than its spatial, complexity. Similarly, when the order of an algorithm (its big $O$) is given without context it is assumed to be the algorithm's **worst-case** complexity (as opposed to the best/average case).

#### Equality vs Membership
While I've used the notation $f(x)\in O(g(x))$ throughout this post as well as in my other writing, it is more common to write:

$$f(x)=O(g(x))\equiv f(x)\in O(g(x))$$

This is an **abuse of notation** and does not *really* denote equality between the function $f$ and the class of functions on the order of $g$. It is merely a shorthand and, as we'll see below, this abuse can be taken to a much farther extreme...

<details>
<summary><h4 class="inline">Equational Notation</h4></summary>
It is possible to use, for example, big $O$ notation in equations, extending the equality <i>analogy</i> that is common practice. For instance:

$$n^{O(1)}=O(e^n)$$

Is equivalent to the following, more formal, proposition:

$$(\exists f,g)\left(f\in O(1)\wedge g\in O(e^n)\right)n^{f(n)}=g(n)$$

And in general, the equation means that if all the big $O$'s on both sides were replaced with some function in that class, the equation is true. There just has to exist one set of functions that make the equation true.
<p></p>
</details>

<details>
<summary><h4 class="inline">$n$ vs. $x$</h4></summary>
Although I used the variable $x$ in the definitions given above, the variable $n$ is more common in Bachmann-Landau notation. This is because $x$ is conventionally used to denote a continuous valued, real variable, while $n$ is conventionally used to denote a discrete, integer valued variable. This jives with the fact that these notations are mostly used in describing the computational complexity of algorithms expressed as functions of their, discrete sized, inputs (e.g there are no lists of size $2.5$ and even further to the point, we cannot subdivide the bit).
<p></p>
</details>

<details>
<summary><h4 class="inline">Limits to Constants</h4></summary>
The first paragraph mentioned that these notations applied to functions that approached infinity or any other value. Using big $O$ as an example we can make the following assumption:

$$f(x)\in O(g(x)) \ \ (\text{as }x\to \infty)\iff f(x)\in O(g(x))$$

For other constants, unless it is clear from the context, we should be explicit in what constant $x$ approaches. Using the limit definition as an example:

$$\limsup_{x\to c}\left|\frac{f(x)}{g(x)}\right|\lt\infty \iff f(x)\in O(g(x)) \ \ (\text{as }x\to c)$$

The formal definitions provided in the previous section assumed the infinity case simply because it is the most common.
</details>

## Properties
I am omitting the $(x)$ after the functions (which, strictly speaking, shouldn't have been present in the first place) for readability:

- $f_1\in O(g_1)\wedge f_2\in O(g_2)\rightarrow f_1+f_2\in O(g_1+g_2)$
- $f_1\in O(g_1)\wedge f_2\in O(g_2)\rightarrow f_1f_2\in O(g_1g_2)$
- $f\cdot O(g)\in O(fg)$
- $kf\in O(g)\rightarrow f\in O(g)$
- $O(kg)=O(g)$

*Where $k$ is some constant*

## Examples
- $5x^3\in O(x^3)$ Same most significant term (times a constant).
- $x^2\in O(x^3)$ Lower than most significant term.
- $2n^2\in O(n!+n)$ Lower than most significant term.
- $x^3\not\in O(x^2)$ Can't grow faster than function.

- $2x^2\in\Omega(x^2)$ Same most significant term (times a constant).
- $x^3\in\Omega(x)$ Greater than most significant term.
- $n!\in\Omega(3n^2+2n)$ Greater than most significant term.
- $x^3\not\in\Omega(x^4)$ Can't grow slower than function.

- $2x^2\in\Theta(x^2)$ Same most significant term (times a constant).
- $x^3\in\Theta(15x^3+4x^2)$ Same most significant term (times a constant).
- $n!\not\in\Theta(3n^2+2n)$ Most significant terms don't match.
