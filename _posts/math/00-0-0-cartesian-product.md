---
layout: post
title: Cartesian Product
date: 2018-04-30
tags: math
---
### Definition
The Cartesian product $\times$ is an operation on two sets, $A$ and $B$, that returns the set of all [ordered pairs](/n-tuples) with their first element from $A$ and their second from $B$.

$$A\times B=\{(a,b)\mid a\in A \land b\in B\}$$

#### Existence in ZFC
We can show that, utilizing the [Kuratowski definition](/n-tuples#definition) of ordered pairs, that the Cartesian product of two sets is merely a subset of the following:

$$A\times B \in \mathcal{P}\left(\mathcal{P}\left(A\cup B\right)\right)$$

<details><summary>Proof</summary>Ill do it later...</details>
<p></p>

$A\cup B$ is guaranteed by the axiom of union, and its repeated power sets are guaranteed by the axiom of power set. This coupled with the fact that the Cartesian product is only a subset of the above expression implies that it must exist.

<!--more-->

### $n$-ary Cartesian Product
While the Cartesian product of two sets returns a set of ordered pairs, the Cartesian product of $n$ sets returns an $n$-tuple:

$$S_1\times S_2\times \cdots \times S_n=\{\left(s_1,s_2,\cdots,s_n\right)\mid\forall k\in\mathbb{N}^* _ n,\ s_k\in S_k)\}$$

<details><summary>Details & Explanation</summary>

Because of this, and the definition of an [$n$-tuple](/n-tuples#n-tuples), we can give an example of a $3$-ary Cartesian product returning a set of $3$-tuples:

$$\begin{align}
A\times B\times C&=(A \times B)\times C\\
&=\{(a,b)\}\times C\\
&=\{((a,b),c)\}\\
&=\{(a,b,c)\}
\end{align}$$
*Where $a\in A$, $b\in B$, and $c\in C$*.
</details>

#### Cartesian Powers
When referring to the repeated Cartesian product of the same set $S$, we can use an abbreviated notation:

 $$\underbrace{S\times S \times \cdots \times S}_{n\text{ sets}}=S^n$$

### Order Properties
#### Non-Commutative
The Cartesian product is a non-commutative operator:

$$A\times B \not= B \times A$$

<details><summary>Rationale</summary>

This should be obvious as the ordered tuples $(a,b)\not=(b,a)$ where $a\in A$ and $b\in B$ via the definition of [tuple equality](/n-tuples#equality).
</details>

#### Non-Associative
The Cartesian product is a non-associative operator:

$$\left(A\times B\right) \times C \not= A\times \left(B \times C\right)$$

<details><summary>Rationale</summary>

Similar to its non-commutativity, we can illustrate this by noting that $((a,b),c)\not= (a,(b,c))$ where $a\in A$, $b\in B$, and $c\in C$.
</details>

#### Left-Associative
When faced with an $n$-ary Cartesian product, it is conventionally evaluated from left to right. That is to say the Cartesian product is left-associative:

$$A\times B \times C=(A \times B)\times C$$

<details>
<summary><h3 class="inline">Distributive Properties</h3></summary>

#### Union
$$A\times\left(B\cup C\right)=\left(A\times B\right)\cup \left(A\times C\right)$$

#### Intersection
$$A\times\left(B\cap C\right)=\left(A\times B\right)\cap \left(A\times C\right)$$

$$\left(A\times B\right)\cap \left(C\times D\right)=\left(A\cap B\right)\times \left(C\cap D\right)$$

#### Set Difference
$$A\times\left(B\setminus C\right)=\left(A\times B\right)\setminus \left(A\times C\right)$$

#### Subsets
$$B\subseteq C\iff\left(A\times B\right)\subseteq \left(A\times C\right)$$

$$\left(A\times B\right)\subseteq \left(C\times D\right)\iff\left(A\subseteq B\right)\land \left(C\subseteq D\right)$$

#### Complements
If $A$ and $B$ are memebers of some universal set $U$, then their absolute complement is denoted $A^C$ and $B^C$ respectively.

$$\left(A\times B\right)^C=\left(A^C\times B^C\right)\cup\left(A^C\times B\right)\cup\left(A\times B^C\right)$$
</details>

### Cardinal Multiplication
Cartesian products are used to define the product of two cardinal numbers:

$$\left|X\right|\cdot\left|Y\right|=\left|X\times Y\right|$$

### Some Uses
#### Functions and Relations
Relations, and thus functions and operations, from a set $A$ to a set $B$ are defined as subsets of the Cartesian product $A\times B$. For example the less than or equal to relation $\le$ on the integers can be defined as so:

$$\le\equiv\{\cdots,\left(1,2\right),\left(-14,0\right),\left(5,5\right),\left(12,13\right),\cdots\}$$

*We can formalize this definition to set theory by comparing the cardinality of the sets represented by the naturals and further the integers.*

And so, because $10$ is less than $12$, the ordered pair $(10,12)\in\le$. We can write this more conventionally as $10\le12$.

#### Coordinates
Every point in $2$-space represents an element of the Cartesian product of the Reals with themselves (i.e $\mathbb{R}^2$). This can be generalized for $n$-space with every point being an element of $\mathbb{R}^n$:

$$\mathbb{R}^n=\{(x_1,x_2,\cdots,x_n)\mid \forall k\in \mathbb{N}^* _ n,\   x_k\in\mathbb{R}\}$$

![plane](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Cartesian-coordinate-system.svg/354px-Cartesian-coordinate-system.svg.png?style=centerme)

*Indeed, the graphical representation above was dubbed the Cartesian plane after the same [Descartes](https://en.wikipedia.org/wiki/René_Descartes) that used it to represent the Cartesian product $\mathbb{R}\times\mathbb{R}$.*

Points in $3$-space are necessary in describing the [position](/position) of objects and particles in space and thus set up the study of [motion](\kinematics), the causes of that motion and, ultimately, the rest of physics.

Moreover, $2$-space (and less frequently $3$-space) is useful in plotting and making inferences from data, as well as visualizing functions over numbers.
