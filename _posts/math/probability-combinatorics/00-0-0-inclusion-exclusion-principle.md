---
layout: post
title: The Inclusion-Exclusion Principle
date: 2019-08-30
tags: math combinatorics probability-theory set-theory
---

The inclusion-exclusion principle is best known as a way to express the cardinality/probability of the union of a countable number of sets in terms of finite intersections of those sets.

Below we will introduce the principle in a more general form, that is, as it applies to any finite measure, then show that this gives us both the cardinality and probability interpretations for free.

<!--more-->

## Theorem
The **inclusion-exclusion principle** is given by the following statement for any finite measure space $(X,\Sigma,\mu)$:

$$\mu\left(\bigcup_{i=1}^nS_i\right)=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)$$

*By finite measure space we mean $\mu(X)\lt\infty$.*

<details>
<summary><h3 class="inline">Proof</h3></summary>
<!-- http://aleph.math.louisville.edu/teaching/2009FA-681/notes-090901.pdf -->

We can prove the this via induction. We let $P(n)$ denote the following proposition for any positive integer $n$:

$$P(n)\equiv\mu\left(\bigcup_{i=1}^nS_i\right)=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)$$

$P(1)$ is trivial as it amounts to the following:

$$P(1)\equiv\mu(S_1)=\mu(S_1)$$

$P(2)$ is the familiar inclusion-exclusion identity:

$$P(2)\equiv \mu(S_1\cup S_2)=\mu(S_1)+\mu(S_2)-\mu(S_1S_2)$$

We can prove $P(2)$ by noting the following 3 statements:

$$\begin{align*}
S_1&=\underbrace{(S_1\setminus S_2)\cup (S_1S_2)}_{\text{Disjoint Sets}}\\
S_2&=\underbrace{(S_2\setminus S_1)\cup (S_1S_2)}_{\text{Disjoint Sets}}\\
S_1\cup S_2&=\underbrace{(S_1\setminus S_2)\cup (S_2\setminus S_1)\cup (S_1S_2)}_{\text{Disjoint Sets}}
\end{align*}$$

Recognizing that these are unions of disjoint sets, we can apply the additivity axiom of measure spaces giving us:

$$\begin{align*}
\mu(S_1)&=\mu(S_1\setminus S_2)+\mu(S_1S_2)\\
\mu(S_2)&=\mu(S_2\setminus S_1)+\mu(S_1S_2)\\
\mu(S_1\cup S_2)&=\mu(S_1\setminus S_2)+\mu(S_2\setminus S_1)+\mu(S_1S_2)
\end{align*}$$

Solving for $\mu(S_1\setminus S_2)$ and $\mu(S_2\setminus S_1)$ respectively and plugging them in to the last equation we arrive at:

$$\mu(S_1\cup S_2)=\mu(S_1)+\mu(S_2)-\mu(S_1S_2)\equiv P(2)$$

With $P(1)$ and $P(2)$ proved, all that's left is to prove the inductive hypothesis $P(n+1)$ assuming $P(n)$. We can do this via the following chain of equalities:

$$\begin{align*}
\mu\left(\bigcup_{i=1}^{n+1}S_i\right)&=\mu\left(\left(\bigcup_{i=1}^nS_i\right)\cup S_{n+1}\right)\tag{def. of indexed $\cup$}\\
&=\mu\left(\bigcup_{i=1}^nS_i\right)+\mu(S_{n+1})-\mu\left(\left(\bigcup_{i=1}^nS_i\right)\cap S_{n+1}\right)\tag{$P(2)$}\\
&=\mu\left(\bigcup_{i=1}^nS_i\right)+\mu(S_{n+1})-\mu\left(\bigcup_{i=1}^n\left(S_i\cap S_{n+1}\right)\right)\tag{distributivity of $\cap$}\\
&=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)+\mu(S_{n+1})-\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}(S_i\cap S_{n+1})\right)\right)\tag{$P(n)$}\\
&=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)+\mu(S_{n+1})-\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\left(\bigcap_{i\in I}S_i\right)\cap S_{n+1}\right)\right)\tag{distributivity of $\cap$}\\
&=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)+\mu(S_{n+1})-\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I\cup\{n+1\}}S_i\right)\right)\tag{def. of indexed $\cap$}\\
&=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)+\mu(S_{n+1})+\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|}\mu\left(\bigcap_{i\in I\cup\{n+1\}}S_i\right)\right)\tag{distribute $-1$}\\
&=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)+\sum _{I\subseteq [1..n]}\left((-1)^{|I|}\mu\left(\bigcap_{i\in I\cup\{n+1\}}S_i\right)\right)\tag{reindex to include $\mu(S_{n+1}$}\\
&=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)+\sum _{I\subseteq [1..n+1]\atop {n+1\in S}}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)\tag{redefine $S$ to always have $n+1$}\\
&=\sum _{I\subseteq [1..n+1] \atop I\not=\emptyset}\left((-1)^{|I|-1}\mu\left(\bigcap_{i\in I}S_i\right)\right)\tag{$P(n+1)$}\\
\end{align*}$$

Note that in the second to last equality we adjust the exponent of the $-1$ to account with the cardinality of $S$ being $1$ higher than before.
<p></p>
Also note that the last equality was valid because the index over the first term was mutually exclusive to that of the second since the second always includes $n+1$. Also note that their union indeed produces the desired $\mathcal P([1..n+1])\setminus\{\emptyset\}$ giving us a single index. Trust me... it works.

</details>

## Alternate Forms & Bounds
A more intuitive form the identity can take is as the following:

$$\begin{align*}
\mu\left(\bigcup_{i=1}^nS_i\right)&=\sum_{k=1}^{n}\left((-1)^{k-1}\sum_{i_1< i_2<\cdots< i_k}{\mu}(S_{i_1}S_{i_2}\cdots S_{i_k})\right)\\
&=\sum_{i=1}^n\mu(S_i)-\sum_{j< i}\mu(S_i S_j)+\sum_{k< j< i}\mu(S_i S_j S_k)-\cdots
\end{align*}$$

Here we can see the measure of the union of $n$ sets is simply the sum of the measures of all the sets minus the sum of the measures of all pairwise intersections plus the sum of the measures of all threeway intersections and so on, alternating the sign.

An interesting property of the principle is best displayed in this form. That is, the entire sum is bounded either above or below by each additional term like so:

$$\begin{align*}
\mu\left(\bigcup_{i=1}^nS_i\right)&\le\sum_{i=1}^n\mu(S_i)\\
&\ge\sum_{i=1}^n\mu(S_i)-\sum_{j< i}\mu(S_i S_j)\\
&\le\sum_{i=1}^n\mu(S_i)-\sum_{j< i}\mu(S_i S_j)+\sum_{k< j< i}\mu(S_i S_j S_k)
\end{align*}$$

As more terms are computed the value gets closer to the true answer. Depending on our desired accuracy, this allows us to get away with summing only some of the terms.

Removing the ellipses from our formula and instead expressing the intersections in terms of an index set $I$ for each cardinality from $1$ to $n$ we get a more compact formula:

$$\mu\left(\bigcup_{i=1}^nS_i\right)=\sum _{k=1}^{n}\left((-1)^{k-1}\sum _{I\subseteq [1..n] \atop |I|=k}\mu\left(\bigcap_{i\in I}S_i\right)\right)$$

Taking this formula even further and just considering every subset at once (barring the empty set) we arrive at the formula we first stated, which is even more compact. 

<!-- https://en.wikipedia.org/wiki/Inclusion%E2%80%93exclusion_principle#Special_case -->

<!-- ## Intuition -->

## Probability
Since a probability space $(\Omega, \mathcal F, P)$ is a finite measure space, in particular $P(\Omega)=1$, the inclusion-exclusion principle applies to any finite set of events $(E_i)_{i=1}^n$ giving us the familiar identity:

$$P\left(\bigcup_{i=1}^nE_i\right)=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}P\left(\bigcap_{i\in I}E_i\right)\right)$$

## Cardinality
To see how the principle applies to cardinality we need to define the following measure $\mu: \Sigma\to[0,\infty]$ that assigns values based on the set's cardinality:

<!-- $$\mu (S)={\begin{cases}\vert S\vert &{\text{if }}S{\text{ is finite}}\\+\infty &{\text{if }}S{\text{ is infinite}}\end{cases}}$$ -->

$$\mu(S)={\begin{cases}\vert S\vert, &|S|\in\aleph_0\\\infty, &|S|\not\in\aleph_0\end{cases}}$$

*The above does indeed qualify as a measure on any $\sigma$-algebra.*

Now, if we let $X$ be the union of $n$ finite sets $(S_i)_{i=0}^n$ and $\Sigma$ a $\sigma$-algebra over $X$, the inclusion-exclusion principle applies since $\mu(X)\lt\infty$. This gives us:

$$\left|\bigcup_{i=1}^nS_i\right|=\sum _{I\subseteq [1..n] \atop I\not=\emptyset}\left((-1)^{|I|-1}\left|\bigcap_{i\in I}S_i\right|\right)$$

<!-- ## Infinite Measures
https://ncatlab.org/nlab/show/inclusion-exclusion -->