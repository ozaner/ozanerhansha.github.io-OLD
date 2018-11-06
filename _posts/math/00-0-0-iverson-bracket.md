---
layout: post
title: Iverson Bracket
date: 2018-08-27
tags: math logic
---
The Iverson bracket, denoted $[P]$, is a function that evaluates to $1$ if the given proposition $P$ is true and $0$ if it's false. That is to say:

$$[P]={\begin{cases}1,&{P}\\0,&{\neg P}\end{cases}}$$

The Iverson bracket can also be used with predicates:

$$[P(x)]={\begin{cases}1,&{P(x)}\\0,&{\neg P(x)}\end{cases}}$$

Below I give two formal definitions of the Iverson bracket. One for the propositional case and one for the predicate case.

<!--more-->

## Propositional Definition
We can think of the notation $[P]$ as being shorthand for the following:

$$[P]\equiv\bigcup\{x\in 2\mid(P\wedge x=1) \vee (\neg P\wedge x=0)\}$$

*Where $2=\\{0,1\\}$ as per its construction in the [natural numbers](\natural-numbers).*

The set builder notation above will end up being $\\{0\\}$ or $\\{1\\}$ depending on whether $P$ is true. The arbitrary union, denoted $\bigcup$, outside of the set 'unwraps' the singleton set so that we are left with just $0$ or $1$.

This allows us to truly equate $[P]$ with the values $0$ and $1$ in the set-theoretic sense.

## Predicate Definition
While we could simply use the same definition above and replace all instances of $P$ with $P(x)$, it would instead be more useful to define $[P(x)]$ as a full blown set-theoretic function.

And indeed, assuming $x$ is an element of some domain $S$ (i.e $x\in S$), we can do just that. However, to aid in defining $[P(x)]$ we'll call it $Q(x)$ for the time being:

$$Q\equiv\{(x,y)\mid(P(x)\wedge y=1)\vee(\neg P(x)\wedge y=0)\}$$

<details>
<summary><strong>Proof of Function</strong></summary>
We can see that $Q$ is a set of ordered pairs $(x,y)$ with $x\in S$ and $y\in 2$. This implies that $Q\subset S\times 2$. However, this only shows that $[P(x)]$ is a <a href="\relations">relation</a>.
<p></p>

To show that $Q$ is a function, we must show that it is right-unique. This should be clear as for any given $x$, $y=0\oplus y=1$. This is because $P(x)\oplus\neg P(x)$ due to the law of the excluded middle.
</details>
<p></p>

And so $Q$ is a function $Q:S\to 2$. We can now say $Q(x)\equiv [P(x)]$, to return to our original notation.

## Arithmetic Properties
Below are some of the immediate properties of the Iverson bracket. We can think of these equalities as bridges between the first order logic notions of truth (true vs. false) and the arithmetic/computational notion of booleans ($0$ vs. $1$).

- $[\neg P]=1-[P]$
- $[P\wedge Q]=[P][Q]$
- $[P\vee Q]=[P]+[Q]-[P][Q]$
- $[P\oplus Q]=([P]-[Q])^2$
- $[P\rightarrow Q]=1-[P]-[Q]+[P][Q]$
- $[P\equiv Q]=1-([P]-[Q])^2$

*The last three can be solved via substitution of the first three and normal propositional calculus.*

## Examples
Iverson brackets are, in many cases, a more natural way to express certain conditional functions or properties.

<details open>
<summary><strong>Kronecker Delta</strong></summary>
The Iverson bracket generalizes the Kronecker delta function $\delta_{ij}$ to any proposition $P$ rather than the specific proposition $i=j$. We can express the Kronecker delta function in terms of the Iverson bracket as so:

$$\delta_{ij}=[i=j]$$
</details>

<details open>
<summary><strong>Trichotomy of $\mathbb{R}$</strong></summary>
Iverson brackets afford a much simpler way to convey the property of trichotomy, or any list of mutually exclusive conditions:

$$[a<b]+[a=b]+[a>b]=1$$
</details>

<details>
<summary><strong>Sign Function</strong></summary>
$$\operatorname{sgn}(x)=[x>0]-[x<0]\ \ \ \ \ \ (\text{For $x\not=0$})$$
</details>

<details>
<summary><strong>Absolute Value</strong></summary>
$$ {\begin{aligned}|x|&=x\cdot \operatorname {sgn}(x)\\&=x([x>0]-[x<0])\end{aligned}}$$
</details>

<details>
<summary><strong>Heaviside Step Function</strong></summary>
$$H(x)=[x>0]$$
</details>

<details>
<summary><strong>Min and Max</strong></summary>
$$\min(x,y)=x[x\leq y]+y[x>y]$$

$$\max(x,y)=x[x>y]+y[x\leq y]$$
</details>

<details>
<summary><strong>Ceiling and Floor</strong></summary>
$$\lceil x\rceil =\sum _{n}n\cdot [n-1<x\leq n]$$

$$\lfloor x\rfloor =\sum _{n}n\cdot [n\leq x<n+1]$$
</details>
