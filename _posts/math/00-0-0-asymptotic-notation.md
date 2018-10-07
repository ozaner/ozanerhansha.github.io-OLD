---
layout: post
title: Asymptotic Notation
date: 2018-10-07
tags: math computer-science
---
The notation used to describe the **asymptotics**, or limiting behavior, of functions consists of a set of 6 relations. These different relations allow us to compare the growth of different functions as they approach some constant or, in most cases, infinity.

In the infinite case, these relations usually boil down to the functions' *most significant term*. That is, the term that grows the quickest as a function of their input. For example, in the function $x^3+5x^2+x$ this role falls on the $x^3$ term as the other terms become insignificant (i.e tend to 0) as $x\to\infty$.

<!--more-->

These notations, particularly big $O$, are most commonly used to classify and compare the computational complexity (both temporal and spatial) of different algorithms as a function of their input size by stripping away unnecessary constants and minor terms that correspond to the different preconditions and runtime environments that these algorithms may run on. Ideally, an algorithm will be on the order of a relatively slowly growing function (e.g $\log n$ grows slower than $n^2$) as they take less resources and thus are more feasible to compute.

They are also used in the approximation of functions that would be infeasible, or even impossible, to calculate otherwise.

| Name | Set Membership<br>Notation | Comparitive<br>Notation |
|-|:-:|:-:|
| Little-$o$ | $f(n)\in o(g(n))$ | $f\prec g$ |
| Big-$O$ | $f(n)\in O(g(n))$ | $f\preceq g$ |
| Big-$\Theta$ | $f(n)\in \Theta(g(n))$ | $f\asymp g$ |
| Big-$\Omega$ | $f(n)\in \Omega(g(n))$ | $f\succeq g$ |
| Little-$\omega$ | $f(n)\in \omega(g(n))$ | $f\succ g$ |
| Asymptotic<br>Equivalence | N/A | $f\sim g$ |

## Formal Definitions
We can formalize this notation by considering either how the values of the function grow after some sufficiently large value $x_0$ or by the limit of their ratio as $x$ approaches infinity. Both notions are given below:

*Note that these two different definitions are similar but not equivalent. Also note that asymptotic equivalence only has a limit definitoin.*

<details>
<summary><h3 class="inline">Growth Definitions</h3></summary>
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

<i>Where $f,g:\mathbb{R}\to\mathbb{R}$ and $x,x_0,k,k_1,k_2\in\mathbb{R}.$</i>
<p></p>
</details>

<details>
<summary><h3 class="inline">Limit Definitions</h3></summary>
Defining asymptotic notation via limits is cleaner, both visually and possibly conceptually. However, doing so comes with added stipulations about limit existence and so on but if those conditions are met, we can define them as so:

$$\begin{align}
f(x)\prec g(x)&\equiv \lim_{x\to\infty}\frac{f(x)}{g(x)}=0\\
f(x)\preceq g(x)&\equiv \limsup_{x\to\infty}\left|\frac{f(x)}{g(x)}\right|\lt\infty\\
f(x)\asymp g(x)&\equiv (\exists k)\lim_{x\to\infty}\frac{f(x)}{g(x)}=k\\
f(x)\sim g(x)&\equiv \lim_{x\to\infty}\frac{f(x)}{g(x)}=1\\
f(x)\succeq g(x)&\equiv \liminf_{x\to\infty}\left|\frac{f(x)}{g(x)}\right|\gt 0\\
f(x)\succ g(x)&\equiv \lim_{x\to\infty}\left|\frac{f(x)}{g(x)}\right|=\infty
\end{align}$$
<p></p>
</details>

#### Asymptotic with respect to Constants
Notice that while the limit definitions above use limits to infinity and the growth definitions used a similar notion, asymptotic notation can be generalized to limits to any constant and not just infinity. For example, with big-$O$ this looks like:

$$f(x)\in O(g(x)) \ \ (\text{as }x\to c)$$

In this more general case, the asymptotic notations are actually families of notations indexed by some constant $c$. We can modify the limit definitions given above by simply replacing $x\to\infty$ with $x\to c$.

That said, the $x\to\infty$ case is so much more common that when no approached value is specified, we will assume this to be the case. In other words:

$$f(x)\in O(g(x)) \ \ (\text{as }x\to\infty)\iff f(x)\in O(g(x))$$

## Notation and Terminology
The use of asymptotic notation is, unfortunately, quite varied and oftentimes informal. As such, I will try to clear up some of the nuance packed into these notations.

#### Membership vs Equality
The set membership notation $f(x)\in O(g(x))$ implies that there is a set of functions that are big-$O$ of $g$ and that $f$ is one of those functions. The same reasoning applies to the other notations.

That said, while I've used this notation throughout this post as well as in my other writing, it is more common to write:

$$f(x)=O(g(x))$$

This is an **abuse of notation** and does not *really* denote equality between the function $f$ and the class of functions on the order of $g$. It is merely a shorthand and, as we'll see below, this abuse can be taken to a much farther extreme...

#### Computational Complexity
When someone refers to the complexity of an algorithm without context they are assumed to be referring to its temporal, rather than its spatial, complexity. Similarly, when the order of an algorithm (its big $O$) is given without context it is assumed to be the algorithm's **worst-case** complexity (as opposed to the best/average case).

<details>
<summary><h4 class="inline">$n$ vs. $x$</h4></summary>
Although I used the variable $x$ in the definitions given above, the variable $n$ is more common in Bachmann-Landau notation. This is because $x$ is conventionally used to denote a continuous valued, real variable, while $n$ is conventionally used to denote a discrete, integer valued variable. This jives with the fact that these notations are mostly used in describing the computational complexity of algorithms expressed as functions of their, discrete sized, inputs (e.g there are no lists of size $2.5$ and even further to the point, we cannot subdivide the bit).
<p></p>
</details>

#### Equational Notation
It is possible to use, for example, big $O$ notation in equations, extending the equality *analogy* that is common practice. For instance:

$$n^{O(1)}=O(e^n)$$

Is equivalent to the following, more formal, proposition:

$$(\exists f,g)\left(f\in O(1)\wedge g\in O(e^n)\right)n^{f(n)}=g(n)$$

And in general, the equation means that if all the big $O$'s on both sides were replaced with some function in that class, the equation is true. There just has to exist one set of functions that make the equation true.

#### Common Orders
Below is a table of common terminology for certain lower-bound complexity classes from slowest to fastest growth:

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

While the terminology $f$ is **'of the order'** $g$ is loose, if the particular notation is not specified it can be assumed to be referring to big $O$.

## Big $O$ and little $o$
Big $O$, one of the most used notations, gives an upper-bound on the asymptotic growth of a function. Thus a function $f$ that is big $O$ of a function $g$ grows as fast or slower than $g$ (up to a constant). In the context of algorithms, this is its **upper-bound complexity**. Little-$o$ is a stronger version of this where $f$ grows strictly slower than $g$.

#### Popularity
While big $\Theta$ is the most descriptive of the 3 notations, it is not as popular as big $O$. Why is this? Well, it is in part due to laziness and convention.

However there is a more practical reason for this as well. Proving something is big $\Theta$ means proving it is both big $O$ and big $\Omega$ which may be much more difficult or even impossible compared to just proving one or the other.

As a result of this, it is generally expected that when someone states an algorithm is $O(g(x))$ that $g(x)$ is as small as they could make it. This makes it a tighter bound when possible but doesn't enforce it incase such a bound is not possible to prove.

#### Properties
I am omitting the $(x)$ after the functions (which, strictly speaking, shouldn't have been present in the first place) for readability:

- $f_1\in O(g_1)\wedge f_2\in O(g_2)\rightarrow f_1+f_2\in O(g_1+g_2)$
- $f_1\in O(g_1)\wedge f_2\in O(g_2)\rightarrow f_1f_2\in O(g_1g_2)$
- $fO(g)\in O(fg)$
- $kf\in O(g)\rightarrow f\in O(g)$
- $O(kg)=O(g)$

*Where $f,g$ are functions and $k$ is some constant*

#### Examples
- $5x^3\in O(x^3)$ Same most significant term (times a constant).
- $x^2\in O(x^3)$ Lower than most significant term.
- $2n^2\in O(n!+n)$ Lower than most significant term.
- $x^3\not\in O(x^2)$ Can't grow faster than function.
- - $x^2\not\in o(x^2)$ Little $o$ is strictly smaller.

## Big $\Omega$ and little $\omega$
Big $\Omega$ gives a lower-bound on the asymptotic growth of a function. Thus a function $f$ that is big $O$ of a function $g$ grows as fast or faster than $g$ (up to a constant). In the context of algorithms, this is its **lower-bound complexity**. Little-$\omega$ is a stronger version of this where $f$ grows strictly faster than $g$.

#### Properties
I am omitting the $(x)$ after the functions (which, strictly speaking, shouldn't have been present in the first place) for readability:

- $f_1\in\Omega(g_1)\wedge f_2\in\Omega(g_2)\rightarrow f_1+f_2\in O(g_1+g_2)$
- $f_1\in\Omega(g_1)\wedge f_2\in\Omega(g_2)\rightarrow f_1f_2\in O(g_1g_2)$
- $f\Omega(g)\in\Omega(fg)$
- $kf\in\Omega(g)\rightarrow f\in\Omega(g)$
- $\Omega(kg)=\Omega(g)$

#### Examples
- $2x^2\in\Omega(x^2)$ Same most significant term (times a constant).
- $x^3\in\Omega(x)$ Greater than most significant term.
- $n!\in\Omega(3n^2+2n)$ Greater than most significant term.
- $x^3\not\in\Omega(x^4)$ Can't grow slower than function.
- $x^2\not\in\omega(x^2)$ Little $\omega$ is strictly bigger.

## Big $\Theta$
Big $\Theta$ gives a lower-bound on the asymptotic growth of a function. Thus a function $f$ that is big $O$ of a function $g$ grows as fast or faster than $g$ (up to a constant). In the context of algorithms, this is its **lower-bound complexity**. Little-$\omega$ is a stronger version of this where $f$ grows strictly faster than $g$.

Big $\Theta$ forms a **tight bound** on the asymptotic growth of a function. It is the combination of both big-$O$ and big-$\Omega$:

$$f(x)\in\Theta(g(x))\equiv f(x)\in O(g(x))\wedge f(x)\in\Omega(g(x))$$

And so, following the pattern, a function $f$ that is big $\Theta$ of a function $g$ grows as fast as $g$ (up to a constant).

<!-- #### Properties
I am omitting the $(x)$ after the functions (which, strictly speaking, shouldn't have been present in the first place) for readability:

- $f_1\in O(g_1)\wedge f_2\in O(g_2)\rightarrow f_1+f_2\in O(g_1+g_2)$
- $f_1\in O(g_1)\wedge f_2\in O(g_2)\rightarrow f_1f_2\in O(g_1g_2)$
- $f\cdot O(g)\in O(fg)$
- $kf\in O(g)\rightarrow f\in O(g)$
- $O(kg)=O(g)$
 -->

 #### Equivalence Relation
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

#### Examples
- $2x^2\in\Theta(x^2)$ Same most significant term (times a constant).
- $x^3\in\Theta(15x^3+4x^2)$ Same most significant term (times a constant).
- $n!\not\in\Theta(3n^2+2n)$ Most significant terms don't match.

## Asymptotic Equivalence
Another interesting point is that $f(x)\sim g(x)$ is just a more specific case of $f(x)\asymp g(x)$. This should come as no surprise. After all, in big-$\Theta$ the functions $f$ and $g$ are asymptotically equal up to a constant, and so if that constant happened to be 1 we would be left with asymptotic equivalence:

$$\begin{align}
&f(x)\asymp g(x)\equiv (\exists k)\lim_{x\to\infty}\frac{f(x)}{g(x)}=k\\
&k=1\\
\therefore\ &f(x)\sim g(x)\equiv \lim_{x\to\infty}\frac{f(x)}{g(x)}=1\\
\end{align}$$

And since this is a special case of big-$\Theta$, it also forms an equivalence relation.
