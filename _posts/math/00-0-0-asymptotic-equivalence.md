---
layout: post
title: Asymptotic Equivalence
date: 2018-08-26
tags: math calculus relations
---
Asymptotic analysis is a way of describing the limiting behavior of functions. Two functions are **asymptotically equivalent** if they have the same limiting behavior, in a sense they are *proportional at infinity*.

This boils down to whether or not the functions have the same *most significant term*, that is the term that grows the quickest as $x$ increases. For example in the function $x^3+5x^2+x$ this role falls on the $x^3$ term as the other terms become insignificant as $x\to\infty$.

Some important results in asymptotic analysis include the prime number theorem and Stirling's approximation.

<!--more-->

## Definition
Asymptotic equivalence is an equivalence relation, denoted $\sim$, on the set of $\mathbb{R}$-valued functions (or $\mathbb{C}$, $\mathbb{Z}^+$, etc.) and is defined as such:

$$f(x)\sim g(x)\equiv\lim_{x\to\infty}{\frac{f(x)}{g(x)}}=1$$

The definition can also be extended to limits not just to infinity but any constant:

$$f(x)\sim g(x) \ \ (\text{as }x\to c)\equiv\lim_{x\to c}{\frac{f(x)}{g(x)}}=1$$

creating a family of equivalence relations, indexed by some real number $c$.

#### Examples
- $x^2\sim x^2+2x$ (most significant terms are same)
- $4n!\sim 4n!+3n^2$ (most significant terms are same)
- $2x^2\not\sim x^2$ (different constants on most significant terms)
- $x^3\not\sim x^4$ (different most significant terms)
- $n!\sim \sqrt{2\pi n}\left(\frac{n}{e}\right)^n$ (Stirling's approximation)

## Proof of Equivalence Relation
To qualify as an equivalence relation, a given [relation](\relations) must satisfy the three properties given below:

<details>
<summary><strong>Reflexivity</strong></summary>
Asymptotic equivalence is reflexive meaning that for all functions $f\sim f$. This is obvious as:

$$\forall f:\lim_{x\to\infty}{\frac{f(x)}{f(x)}}=1$$

<i>Assuming $f(x)$ doesn't approach $0$.</i>
</details>

<details>
<summary><strong>Symmetry</strong></summary>
Asymptotic equivalence is symmetric meaning that $f\sim g\implies g\sim f$. To prove this notice that the only term that "survives" after the limit is taken of both $f$ and $g$ is the most significant one:

$$\lim_{x\to\infty}{\frac{f(x)}{g(x)}}=\frac{\lim\limits_{x\to \infty}{f(x)}}{\lim\limits_{x\to \infty}{g(x)}}=\frac{f_s(x)}{g_s(x)}$$

<i>Where $f_s$ and $g_s$ represent the most significant terms of $f$ and $g$ respectively.</i>

Notice that $f(x)\sim g(x)$ is the same as saying $f_s/g_s=1$. And so we can deduce the following:

$$\frac{f_s(x)}{g_s(x)}=1=\frac{g_s(x)}{f_s(x)}=\lim_{x\to\infty}{\frac{g(x)}{f(x)}}\equiv g(x)\sim f(x)$$

Thus we have proved $f\sim g\implies g\sim f$.
</details>

<details>
<summary><strong>Transitivity</strong></summary>
I'll do this later, but this should be clear as asymptotic equivalence forms equivalence classes characterized by the most significant terms of functions.
</details>

## Relation to Algorithmic Complexity
When dealing with the time and space complexity of algorithms, asymptotic analysis (either in the form defined above or via **Bachmann–Landau notation**) is used to compare the efficiency of different algorithms by stripping away unnecessary constants and minor terms that correspond to the different preconditions and runtime environments that these algorithms may run on.

In particular, the limit definitions of the Bachmann–Landau notation are very similar to that of asymptotic equivalence. In fact, we can phrase Big $O$, $\Omega$, and $\Theta$ notation in terms of asymptotic growth.

$$f(x)\in O(g(x))\equiv \exists c\not=0:cg(x)\text{ grows asymptotically faster than } f(x)$$


$$f(x)\in \Omega(g(x))\equiv \exists c\not=0:cg(x)\text{ grows asymptotically slower than } f(x)$$

$$f(x)\in \Omega(g(x))\equiv \exists c\not=0:cg(x) \sim f(x)$$
