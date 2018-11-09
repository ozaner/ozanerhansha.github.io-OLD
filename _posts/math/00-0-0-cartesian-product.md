---
layout: post
title: Cartesian Product
date: 2018-04-30
tags: math set-theory
---
<!-- Heavily Reformatted 10/25/18 -->
## Definition
The Cartesian product $\times$ is an operation on two sets, call them $A$ and $B$, that returns the set of all [ordered pairs](/n-tuples) with their first element from $A$ and their second from $B$.

$$A\times B=\{(a,b)\mid a\in A \land b\in B\}$$

#### Existence in ZFC
Utilizing the [Kuratowski definition](/n-tuples#definition) of ordered pairs, we can show that the Cartesian product of two sets can be constructed from the axioms of ZFC. In particular, it is a subset of the following easily constructed set:

$$A\times B \subseteq \mathcal{P}\left(\mathcal{P}\left(A\cup B\right)\right)$$

<details><summary><strong>Proof</strong></summary>
First, note that $A\cup B$ is guaranteed by the axiom of union and that its power set is guaranteed by the axiom of power set.

Next notice that, among many other elements, the power set of $A\cup B$ contains:
<!-- \left(\forall a\in A,\forall b\in B\right) -->
$$\{a\},\{a,b\}\in\mathcal{P}\left(A\cup B\right)$$

where $a$ and $b$ are elements in $A$ and $B$ respectively. Now if we take the power set again we'll see that the result contains, among other things, the elements:

$$\{\{a\},\{a,b\}\}\in\mathcal{P}\left(\mathcal{P}\left(A\cup B\right)\right)$$

for all $a$ and $b$ in $A$ and $B$. Now invoke the axiom of subset to choose only those elements that fit the description and we are done!
</details>
<p></p>

<!-- $A\cup B$ is guaranteed by the axiom of union, and its repeated power sets are guaranteed by the axiom of power set. This coupled with the fact that the Cartesian product is only a subset of the above expression implies that it must exist. -->

<!--more-->

## $n$-ary Cartesian Product
It is easy to see how one might generalize this notion to $n$ sets. By simply chaining the Cartesian product we are left with a set of $n$-tuples:

$$\begin{align*}(S_0\times S_1)\times S_2&=\{(\left(s_0,s_1),s_2\right)\mid\forall k\in 3,\ s_i\in S_i)\}\\
&=\{\left(s_0,s_1,s_2\right)\mid\forall k\in 3,\ s_i\in S_i)\}
\end{align*}$$

Repeating this $n$ times (inductively), we are left with the following for any $n$ sets:

$$S_0\times S_1\times \cdots \times S_{n-1}=\{\left(s_0,s_1,\cdots,s_{n-1}\right)\mid\forall i\in n,\ s_i\in S_i)\}$$

*Notice that the parenthesis are omitted. This is because the cartesian product is left-associative, a property that is expounded upon further below.*

<!-- Letting $S_i$ be a family of sets indexed by $n$, we can write this in the more concise big pi notation:
$$\prod_{i=1}^nS_i=S_1\times S_2\times \cdots \times S_n$$

*Note that the notion of indexed families comes from functions which depend on the definition of $n$-ary cartesian products. So it should only be taken as a useful shorthand.* -->

#### Indexed and Infinitary Products
It is possible to extend the notion of the Cartesian product to allow for the product of any indexed family of sets:

$$\prod_{i\in I}S_i=\{f:I\to\bigcup_{i\in I}S_i\mid \forall i,f(i)\in S_i\}$$

In words this Cartesian product returns the set of all functions that map an element from $I$ to a corresponding element in $S_i$. Note that this allows for index sets with an infinite cardinality, leading to **infinitary** products.

$$\underbrace{\text{binary},\text{trinary},\cdots,n\text{-ary}}_{\text{finitary}}\cdots;\underbrace{\aleph_0\text{-ary},\aleph_1\text{-ary},\cdots}_{\text{infinitary}}$$

Note that this definition of Cartesian product depends on the notion of functions (indexed family of sets), which in turn depends on our previous definition. As such we are left with two distinct versions of the Cartesian product, one more general than the other.

*That said, once defined, we can always map between these two definitions (for finitary products at least). So in most cases, the distinction is irrelevant.*

#### Cartesian Powers
When dealing with the repeated Cartesian product of a single set $S$, we call it the $n$th Cartesian power and use the following notation:

 $$S^n=\underbrace{S\times S \times \cdots \times S}_{n\text{ sets}}$$

 Even more generally, using the indexed definition of Cartesian product, we can denote the set of all functions from a set $I$ to $S$ like so:
 $$S^I=\prod_{i\in I}S=\{f\mid f:I\to S\}$$

 *Note that this meshes with the simpler definition of $S^n$ since $n$ can be considered a set as per its construction in the [natural numbers](\natural-numbers).*

## Properties
### Ordering Properties
<!-- #### Non-Commutative -->
<details>
<summary><h4 class="inline">Non-Commutative</h4></summary>
The Cartesian product is a non-commutative operator:

$$A\times B \not= B \times A$$

This should be obvious as the ordered tuples $(a,b)\not=(b,a)$ where $a\in A$ and $b\in B$ via the definition of <a href="/n-tuples#equality">tuple equality</a>.
<p></p>
</details>

<!-- #### Non-Associative -->
<details>
<summary><h4 class="inline">Non-Associative</h4></summary>
The Cartesian product is a non-associative operator:

$$\left(A\times B\right) \times C \not= A\times \left(B \times C\right)$$

Similar to its non-commutativity, we can illustrate this by noting that $((a,b),c)\not= (a,(b,c))$ where $a\in A$, $b\in B$, and $c\in C$.
<p></p>
</details>

<!-- #### Left-Associative -->
<details>
<summary><h4 class="inline">Left-Associative</h4></summary>
When faced with an $n$-ary Cartesian product, it is conventionally evaluated from left to right. That is to say the Cartesian product is left-associative:

$$A\times B \times C=(A \times B)\times C$$

This convention agrees with the definition of $n$-ary Cartesian products and $n$-tuples.
</details>

### Distributive Properties
<!-- <details>
<summary><h3 class="inline">Distributive Properties</h3></summary> -->
$$\begin{gather*}
A\times\left(B\cup C\right)=\left(A\times B\right)\cup \left(A\times C\right)\tag{Union}\\
A\times\left(B\cap C\right)=\left(A\times B\right)\cap \left(A\times C\right)\tag{Intersection 1}\\
\left(A\times B\right)\cap \left(C\times D\right)=\left(A\cap B\right)\times \left(C\cap D\right)\tag{Intersection 2}\\
A\times\left(B\setminus C\right)=\left(A\times B\right)\setminus \left(A\times C\right)\tag{Set Difference}\\
B\subseteq C\iff\left(A\times B\right)\subseteq \left(A\times C\right)\tag{Subset 1}\\
\left(A\times B\right)\subseteq \left(C\times D\right)\iff\left(A\subseteq B\right)\land \left(C\subseteq D\right)\tag{Subset 2}\\
\end{gather*}
$$

<!-- <h4>Union</h4>
$$A\times\left(B\cup C\right)=\left(A\times B\right)\cup \left(A\times C\right)$$

<h4>Intersection</h4>
$$A\times\left(B\cap C\right)=\left(A\times B\right)\cap \left(A\times C\right)$$

$$\left(A\times B\right)\cap \left(C\times D\right)=\left(A\cap B\right)\times \left(C\cap D\right)$$

<h4>Set Difference</h4>
$$A\times\left(B\setminus C\right)=\left(A\times B\right)\setminus \left(A\times C\right)$$

<h4>Subsets</h4>
$$B\subseteq C\iff\left(A\times B\right)\subseteq \left(A\times C\right)$$

$$\left(A\times B\right)\subseteq \left(C\times D\right)\iff\left(A\subseteq B\right)\land \left(C\subseteq D\right)$$

<h4>Complements</h4> -->
If $A$ and $B$ are members of some universal set $U$, then their absolute complement is denoted $A^C$ and $B^C$ respectively.

$$\left(A\times B\right)^C=\left(A^C\times B^C\right)\cup\left(A^C\times B\right)\cup\left(A\times B^C\right)\tag{Complement}$$
<!-- </details> -->

## Examples
#### Relations
An $n$-ary [relation](\relations) is defined as an $n$-tuple with the first $n$ elements being a list of sets and the last element a subset of their Cartesian product. For example, $\le$ is a binary relation on the set $\mathbb R$:
$$\begin{gather}
\le\equiv(\mathbb R,\mathbb R,G)\\
G\subseteq\mathbb R\times\mathbb R
\end{gather}$$

This allows us to formalize statements like $4\le7$ which really means $(4,7)\in G$.

#### Cardinal Multiplication
Cartesian products are used to define the product of two cardinal numbers:

$$\left|X\times Y\right|=\left|X\right|\left|Y\right|$$

And for any indexed family of cardinal numbers:
$$\left|\prod_{i\in I}X_i\right|=\prod_{i\in I}\left|X_i\right|$$

#### Cartesian Coordinates
Every point in $2$-space represents an element of the Cartesian product of the Reals with themselves (i.e $\mathbb{R}^2$). This can be generalized to $n$-space with every point being an element of $\mathbb{R}^n$:

$$\mathbb{R}^n=\{(x_0,x_1,\cdots,x_{n-1})\mid \forall k\in n:   x_k\in\mathbb{R}\}$$

![plane](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Cartesian-coordinate-system.svg/354px-Cartesian-coordinate-system.svg.png?style=centerme)

*Indeed, the graphical representation above was dubbed the Cartesian plane after the same [Descartes](https://en.wikipedia.org/wiki/René_Descartes) that used it to represent the Cartesian product $\mathbb{R}\times\mathbb{R}$.*

Points in $3$-space are necessary in describing the [position](/position) of objects and particles in space and thus set up the study of [motion](\kinematics), the causes of that motion and, ultimately, the rest of physics.

Moreover, $2$-space (and less frequently $3$-space) is used in plotting and making inferences from data as well as visualizing functions over an interval of numbers. We can even consider an infinite dimensional real space $\mathbb R^\mathbb \omega$, aka the set of all real sequences.
