---
layout: post
title: n-Tuples
date: 2018-04-23
tags: math set-theory
---
An $n$-tuple is an ordered list of $n$ elements. It is dissimilar to a set in that the order of its elements matter, it must be finite, and it can contain multiples of the same element.

Here are some common names for tuples of different size:

$n$-tuple | Name(s)
--:|:--
$0$ | null-tuple, $0$-tuple
$1$ | singleton, $1$-tuple
$2$ | ordered pair, $2$-tuple
$3$ | ordered triplet, $3$-tuple
$n$ | $n$-tuple

*My [medium article](https://medium.com/@ozanerhansha/the-ordered-pair-and-set-theory-69aa6e2b8a32) on ordered pairs and their uses.*

<!--more-->

## Definition
#### $2$-tuples
We define ordered pairs, or $2$-tuples, as [Kuratowski](https://en.wikipedia.org/wiki/Kazimierz_Kuratowski) did:

$$(x_1,x_2)=\{\{x_1\},\{x_1,x_2\}\}$$

The above definition distinguishes $a$ from $b$ in that both sets in the right set contain $a$ but only one contains $b$. This is what gives the pair order.

#### $n$-tuples
Using the $2$-tuple, we can define all $n$-tuples recursively as an ordered pair of an $(n-1)$-tuple and another element. The $3$-tuple, for example, would be:

$$\begin{align}
(x_1,x_2,x_3)&=((x_1,x_2),x_3)\\
&=\{\{(x_1,x_2)\},\{(x_1,x_2),x_3\}\}\\
&=\{\{\{\{x_1\},\{x_1,x_2\}\}\},\{\{\{x_1\},\{x_1,x_2\}\},x_3\}\}\\
\end{align}$$

And in general, an $n$-tuple for $n>2$ is recursively defined as:

$$(x_1,x_2,\cdots,x_{n-1},x_n)=((x_1,x_2,\cdots,x_{n-1}),x_n)$$

*While the above definition is standard, it lacks a notion of a $0$ and $1$-tuple. See [this](https://en.wikipedia.org/wiki/Tuple#Tuples_as_nested_sets) for a different definition of $n$-tuples that uses the null-tuple as a base case rather than ordered pairs. I can't find a use for them that justifies their complication to the definition of $n$-tuple, so I excluded them.*

<!-- *Alternatively, $n$-tuples can also be defined as functions with domains over some finite interval of the positive integers. In this sense, they would be equivalent to finite sequences. Although since tuples are usually used to define functions (and thus finite sequences) this would be circular.*

Whatever definition is used, all that matters is that two $n$-tuples are equivalent *only* when the elements at each of their indices are equivalent. This is their defining property. -->

<details>
<summary><h4 class="inline" id="simultaneous-interpretation">Simultaneous Interpretation</h4></summary>
A consequence of this definition is that any $n$-tuple can also be thought of as a $k$-tuple where $2\le k\le n$. This is an immediate consequence of the recursive definition:

$$(x_1,x_2,\cdots,x_n)=((x_1,x_2,\cdots,x_{n-k+1}),x_{n-k+2},\cdots,x_n)$$

This has consequences in how we interpret the <a href="\cartesian-product#simultaneity-of-arity">arity of Cartesian products</a> and thus relations and functions.
</details>

#### Existence in ZFC
The existence of an ordered pair of elements in ZFC can be proved using the axiom of pairing 3 times. Once to prove that $ \\{ a \\} $ exists, another to prove $ \\{ a,b \\} $ exists, and one more time to pair them with each other.

And since $n$-tuples are simply nested ordered pairs, they too must exist.

## Equality
Two ordered pairs are equivalent if and only if the elements in each of their respective indices are equal. That is to say, for two $n$-tuples $X$ and $Y$:

$$\begin{align}
X&=(x_0,x_1,x_2,\cdots,x_{n-1})\\
Y&=(y_0,y_1,y_2,\cdots,y_{n-1})
\end{align}$$

$X$ and $Y$ are only equal if:

$$\begin{align}
X=Y&\equiv\forall k\in n \ (x_k=y_k)\\
&\equiv x_0=y_0 \land x_1=y_1 \land \cdots \land x_{n-1}=y_{n-1}\\
\end{align}$$

*Where $n$ is a set as per its construction in the [natural numbers](\natural-numbers).*

Note that for this definition to work, the two tuples have to be the same size. As such, tuples of different sizes will never be equal.

## Extraction
In order to use these tuples, we have to be sure we can have some formula to extract the first and second elements from them. These formulas are called the first and second **projections**.
#### First Element
To project the first element $\pi_1(P)$ of an ordered pair $P=(a,b)$ we can use the following construction:

$$\pi_1(P)=\bigcup\bigcap P=a$$

<details><summary><strong>Proof</strong></summary>
  <b>Lemma 1</b>
  <p>To make proving the above statement easier, it would help to prove that the arbitrary union of a set of an element $\{x\}$ is that element $x$:

  $$\bigcup \{x\}=x$$

  First let's start with the definition of the arbitrary union of a set $S$:

  $$\bigcup S=\{a\mid \left(\exists b\in S\right)a\in b\}$$

  In in English this means, all elements $a$ that are contained in at least one set $b$ that are contained in $S$. (i.e the union of all the elements in $S$). Plugging $\{x\}$ in for $S$ we see:

  $$\bigcup \{x\}=\{a\mid \left(\exists b\in \{x\}\right)a\in b\}$$

  Since there is only one element in $\{x\}$, namely $x$, there is only one set $b$ could be: $x$. So, we can say the following:

  $$\bigcup \{x\}=\{a\mid a\in x\}$$

  And since the set of all elements in $x$ is simply that same set:

  $$\boxed{\bigcup \{x\}=x}$$
  </p>
  <b>The Proof</b>
  <p>

  $$\begin{align}
  \pi_1(P)&=\bigcup\bigcap P\\
  &=\bigcup\bigcap \{\{a\},\{a,b\}\}\\
  &=\bigcup \left(\{a\}\cap\{a,b\}\right)\\
  \end{align}$$

  Of course the only element in common between $\{a\}$ and $\{a,b\}$ is $a$ so:

  $$\pi_1(P)=\bigcup \{a\}$$

  And from Lemma 1, we know this equals:

  $$\pi_1(P)=\bigcup \{a\}=a$$

  And indeed, $a$ is the first element of the ordered pair $P$.
  </p>
</details>

#### Second Element
The second element $\pi_2(P)$ of an ordered pair $P=(a,b)$ can be found like so:

$$\pi_2(P)=\bigcup\{x\in\bigcup P\mid\bigcup P\not=\bigcap P\implies x\not\in\bigcap P\}=b$$

<details><summary><strong>Proof</strong></summary>
I'll do it later...
</details>

#### Extracting Elements of $n$-Tuples
You may have noticed that the above definitions only apply to $2$-tuples. What about $n$-tuples? Well, quite intuitively, we can extract the elements of an $n$-tuple of any size by recursively using the $\pi_1$ and $\pi_2$ functions we defined above.

The notation we'll use is as follows: $\pi^n_i(P)$ is the $i$th element of the $n$-tuple $P=\left(x_1,x_2,x_3,\cdots,x_n\right)$.

The first element of $P$ can be found like so:

$$\pi^n_1(P)=\underbrace{\pi_1\circ\cdots\circ\pi_1}_{n-1\text{ iterations}}(P)=x_1$$

For any element *other* than the first, we can use the following formula:

$$\pi^n_i(P)=\pi_2\circ\underbrace{\pi_1\circ\cdots\circ\pi_1}_{n-i\text{ iterations}}(P)=x_i$$

This should be fairly intuitive as the repeated $\pi_1$ serve to extract the desired nested tuple and once we reach the base case of the $2$-tuple, we either want the first $\pi_1$ or second $\pi_2$ term.

<!-- <details><summary>"Proof" & Intuition</summary>
Not really a proof, I just wrote down how to find the elements of $2,3,4,5$-tuples and found the pattern:

$$\begin{align}
  &2\text{-tuple}\left\{
    \begin{array}{l}
      \pi^2_1=\pi_1(P)\\
      \pi^2_2=\pi_2(P)\\
    \end{array}
  \right.\\
  &3\text{-tuple}\left\{
    \begin{array}{l}
      \pi^3_1=\pi_1\left(\pi_1\left(P\right)\right)\\
      \pi^3_2=\pi_2\left(\pi_1\left(P\right)\right)\\
      \pi^3_3=\pi_2\left(P\right)\\
    \end{array}
  \right.\\
  &4\text{-tuple}\left\{
    \begin{array}{l}
      \pi^4_1=\pi_1\left(\pi_1\left(\pi_1\left(P\right)\right)\right)\\
      \pi^4_2=\pi_2\left(\pi_1\left(\pi_1\left(P\right)\right)\right)\\
      \pi^4_3=\pi_2\left(\pi_1\left(P\right)\right)\\
      \pi^4_4=\pi_2\left(P\right)\\
    \end{array}
  \right.\\
  &5\text{-tuple}\left\{
    \begin{array}{l}
      \pi^5_1=\pi_1\left(\pi_1\left(\pi_1\left(\pi_1\left(P\right)\right)\right)\right)\\
      \pi^5_2=\pi_2\left(\pi_1\left(\pi_1\left(\pi_1\left(P\right)\right)\right)\right)\\
      \pi^5_3=\pi_2\left(\pi_1\left(\pi_1\left(P\right)\right)\right)\\
      \pi^5_4=\pi_2\left(\pi_1\left(P\right)\right)\\
      \pi^5_5=\pi_2\left(P\right)\\
    \end{array}
  \right.\\
\end{align}$$

Why are is there a conditional definition of the $a$th element of an $n$-tuple? What causes this asymmetry? Well it must be the fact that our base case in defining $n$-tuples was the ordered pair rather than some sort of $1$-tuple. Although it's possible that starting with a $1$-tuple wouldn't change this conditional...
</details> -->

## Some Uses
#### Cartesian product
Ordered pairs are necessary in defining the [Cartesian Product](/cartesian-product), which in turn are used to define relations, functions, coordinates, etc.

#### Mathematical Structures
Tuples are often used to encapsulate sets along with some operator or relation into a complete mathematical structure. One example is a graph which is defined as an ordered pair $G=(V,E)$ where $V$ is a set of vertices and $E$ a set of edges connecting those vertices. Another example is a group which is defined as an ordered pair $G=(S,\cdot)$ where $\cdot$ is some binary operation on the elements of $S$. Tuples are also used to encapsulate rings, fields, vector spaces, topological spaces, ordered sets, and so on.
