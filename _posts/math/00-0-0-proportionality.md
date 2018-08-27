---
layout: post
title: Proportionality
date: 2018-08-17
tags: math relations
---
## A Review of Proportionality
Recall that two expressions, which we can consider **functions**, are proportional if there exists some constant that when multiplied by one of the functions makes them equivalent. This relationship is usually denoted $y\propto x$ or equivalently as $y=kx$ where $k$ is some **proportionality constant**.

For example, a circle's circumference $C$ is proportional to it's diameter $d$. We can write this as $C\propto d$ and even further, with the knowledge that the constant between them is $\pi$, we can write $C=\pi d$

<!--more-->

#### Finer Points and Motivation
Notice that proportionality satisfies the three criterion for an equivalence relation: reflexivity, symmetry, and transitivity (we'll prove this later). By imagining proportionality as a relation (or as we'll see a family of relations) on the set of real/complex valued functions, we can begin to formally define it.

## Definition on $\mathbb{R}$-Valued Functions
Proportionality is a family of equivalence relations on the set(s) of real valued functions (i.e the set of functions $f:S\to\mathbb{R}$ where $S$ is an arbitrary set):

$$\propto_{\mathbb{R}^S}\equiv\{(x,y)\in(\mathbb{R}^S)^2\mid\exists k\in \mathbb{R}:kx=y\}$$

And because $x\propto_{\mathbb{R}^S}y$ is shorthand for $(x,y)\in\propto_{\mathbb{R}^S}$ we can say:

$$x\propto_{\mathbb{R}^S}y\equiv(\exists k\in \mathbb{R})\ kx=y$$

Notice that the set of functions from $S$ to $\mathbb{R}$ forms a vector space with its underlying field being the real numbers. Every choice of $S$ produces a different proportionality relation, hence it being a family.

*The notation $\propto_{\mathbb{R}^S}$ was chosen instead of $\propto_S$ in order to match the more general definition of proportionality given below.*

#### Other Number Systems
- $\mathbb{C,Q}$: Note that the above definition works just as well with both complex and rational valued functions and scalars. This is because, like the real numbers, they both form fields with inverse elements.
- $\mathbb{Z,N}$: Unlike the complex, real, and rational numbers, the integers and natural numbers do not form fields because they do not have inverses under multiplication. As such, proportionality loses the reflexive property because the constant $k^{-1}$ does not exist for any integer. Proportionality can still be used, just not as an equivalence relation.

## Generalized Definition
We can generalize this definition to not just the set of real-valued functions, but any vector space. Given a vector space with vectors $V$, an underlying field $F$, and a valid scalar multiplication $\cdot$, we can define the following equivalence relation:

$$\propto_V\equiv\{(\mathbf{x},\mathbf{y})\in V^2\mid\exists k\in F:k\mathbf{x}=\mathbf{y}\}$$

And because $x\propto_Vy$ is shorthand for $(x,y)\in\propto_V$ we can say:

$$\mathbf{x}\propto_V \mathbf{y}\equiv(\exists k\in F)\ k\mathbf{x}=\mathbf{y}$$

#### Notation
When the context is clear, we can omit the subscript denoteing what vector space the relation is acting upon and just write $\propto$. This is usually the case when relating two functions, real valued or otherwise, since proportionality is most commonly used in fields like physics where the domain of discourse is very clear.

## Proof of Equivalence Relation
Using the general definition above, we will prove $\propto$ forms an equivalence relation by showing it has the reflexive, symmetric, and transitive properties.

<details>
<summary><strong>Reflexivity</strong></summary>
Proportionality is reflexive, i.e $\mathbf{v}\propto \mathbf{v}$ for all $\mathbf{v}\in V$, because every vector space has an identity scalar that when multiplied by any of its vectors, produces that same vector.

$$(\exists e\in F)(\forall \mathbf{v}\in V)\ e\mathbf{v}=\mathbf{v}$$

This is enough to prove reflexivity because if $\mathbf{x}=\mathbf{y}$ then the definition becomes:

$$\mathbf{x}\propto_V \mathbf{x}\equiv(\exists k\in F)\ k\mathbf{x}=\mathbf{x}$$

and there will always exist a $k\in F$, that satisfies $k\mathbf{x}=\mathbf{x}$ and it will always be the identity scalar $e$ (aka the number $1$ in the case of the complex/real/etc. numbers).
</details>

<details>
<summary><strong>Symmetry</strong></summary>
Proportionality is symmetric, i.e $\mathbf{u}\propto \mathbf{v}\implies \mathbf{v}\propto \mathbf{u}$ for all $\mathbf{u},\mathbf{v}\in V$, because every scalar in a vector space has a multiplicative inverse:

$$(\forall s\in F)(\exists s^{-1}\in F)\ ss^{-1}=e$$

<i>Where $e$ is the identity scalar. Also note that a field's multiplication is commutative.</i><p></p>

So assuming two vectors are proportional $\mathbf{x}\propto_V \mathbf{y}$ there must exist some $k\in F$ that satisfies $k\mathbf{x}=\mathbf{y}$. If we multiply both sides by $k^{-1}$, which too must exist as we've stated, we are left with:

$$\begin{align}
k\mathbf{x}&=\mathbf{y}\\
 k^{-1}k\mathbf{x}&=k^{-1}\mathbf{y}\\
e\mathbf{x}&=k^{-1}\mathbf{y}\\
\mathbf{x}&=k^{-1}\mathbf{y}
\end{align}$$

Notice that, because $k^{-1}\in F$, this is precisely the definition of $\mathbf{y}\propto \mathbf{x}$. And so we have shown that for any two vectors in $V$ that if $\mathbf{x}\propto \mathbf{y}$ then $\mathbf{y}\propto \mathbf{x}$. And that if the proportionality constant of $\mathbf{x}\propto \mathbf{y}$ is $k$ then the constant between $\mathbf{y}\propto \mathbf{x}$ is $k^{-1}$.
</details>

<details>
<summary><strong>Transitivity</strong></summary>
The last property to prove is transitivity. Proportionality being transitive means that $\mathbb{u}\propto\mathbb{v}\wedge\mathbb{v}\propto\mathbb{w}\implies\mathbb{u}\propto\mathbb{w}$. This can be shown by noting:

$$\mathbb{u}\propto\mathbb{v}\iff k_1\mathbb{u}=\mathbb{v}$$

$$\mathbb{v}\propto\mathbb{w}\iff k_2\mathbb{v}=\mathbb{w}$$

So if we have $\mathbb{u}\propto\mathbb{v}\wedge\mathbb{v}\propto\mathbb{w}$ then we also know there exists two constants $k_1$ and $k_2$ that correspond to each. Now we can simply substitute $k_1\mathbb{u}$ in for $\mathbb{v}$ in the following way:

$$\begin{align}
k_1\mathbb{u}&=\mathbb{v}\\
k_2\mathbb{v}&=\mathbb{w}\\
k_2k_1\mathbb{u}&=\mathbb{w}\\
\end{align}$$

Because field multiplication is associative, the scalar $k_2k_1$ is the proportionality constant between $\mathbb{u}$ and $\mathbb{w}$ implying that $\mathbb{u}\propto\mathbb{w}$. And thus we have proved the transitivity of the proportional relation.
</details>
