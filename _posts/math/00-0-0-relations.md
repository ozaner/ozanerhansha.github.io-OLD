---
layout: post
title: Relations
date: 2018-08-12
tags: math set-theory
---
<!-- ## What is a Relation?
Relations are used to correlate elements of different sets in some way. They are a more general form of a function, which can only relate elements to a single output.

#### Example
Say I had a set of tops $T$, pants $P$, and shoes $S$. I could define another set $R$ that is a collection of all the combinations of clothing that go together (a set of ordered triplets). This set would be called a relation, because it *relates* pieces of clothing that go well together by virtue of that combination being an element of $R$. -->

## Definition
A **relation** $R$ on a set of sets $S_1,S_2,S_3,\cdots$ is a subset of their [**cartesian product**](/cartesian-product):

$$R\subset S_1\times S_2\times S_3\times \cdots$$

Relations are used to establish $n$-way relationships between elements of the same or different sets (ex. there is a two way relationship between $2$ and $5$ in that $2<5$).

#### Arity
The arity of a relation is the number of sets it is a relation on (i.e the [arity of the cartesian product](/cartesian-product#arity) it is a subset of). Thus, a relation on $2$ sets is a *bi*nary relation, $3$ sets makes a *tri*nary relation and, in general, $n$ sets make an $n$-ary relation.

When $n$ is infinite the relation is **infinitary** as opposed to **finitary** for finite $n$.

<!--more-->

#### Existence in ZFC
We [proved that cartesian products existed](/cartesian-product#existence-in-zfc) in another post and so, because relations are subsets of cartesian products, we only need to invoke the axiom of subset to prove their existence.

## Notation
Relations are common mathematical objects and thus have special notation regarding their use:

#### $n$-ary Relations
For $n$-ary relations it is common to write:

$$Rabcd\cdots \equiv (a,b,c,d,\cdots)\in R$$

where $R$ is the relation in question and $(a,b,c,d,\cdots)$ are elements of the cartesian product $R$ is a subset of.

#### Binary Relations
While you can write $Rab$ for binary relations, it is more common to write:

$$aRb\equiv (a,b)\in R$$

This notation is used for almost all common relations like $5>3$ or $ABC \cong ADC$.

## Properties of Binary Relations
The most common type of relations are binary. This is in part due to the fact that many higher arity relations can be broken up into a collection of binary relations.

<!-- This is in part because many relations can be [*curried*](https://en.wikipedia.org/wiki/Currying) into several different binary relations -->

A binary relation on two different sets $A$ and $B$ is called *heterogenous* when $A\not=B$ and *homogenous* when $A=B$. Homogenous relations are also called **relations on a set**.

Below is a list of common classifications of binary relations based on what properties they satisfy. In all the definitions below, we will assume $R\subset A\times B$ and $a\in A, b\in B$:

### Uniqueness Properties

<details>
<summary><h4 class="inline">Injective</h4></summary>
A relation is called injective if for all $b$ on the right side, the $a$ on the left side is unique in the expression $aRb$. More formally, $R$ is injective if:

$$(\forall a_1,a_2\in A, \forall b\in B)\ a_1Rb\wedge a_2Rb\implies a_1=a_2$$

Because of this property, injective relations are also called <b>left-unique</b>.
</details>

<details>
<summary><h4 class="inline">Functional</h4></summary>
A relation is functional if for all $a$ on the left side, the $b$ on the right is unique. Relations that fulfill this property are called <b>functions</b> and are said to have a unique output $b$ for a given input $a$. Formally this means:

$$(\forall a\in A, \forall b_1,b_2\in B)\ aRb_1\wedge aRb_2\implies b_1=b_2$$

Similar to injective relations, a functional relation is also called <b>right-unique</b>.
</details>

<!-- <details>
<summary><h4 class="inline">One-to-One</h4></summary>
One-to-One functions are relations that are both functional and injective. These functions map every element in their domain to a unique element in the range. These are also called <b>injective functions</b> because being functional is implied in the classification 'function'.
</details> -->

### Totality Properties

<details>
<summary><h4 class="inline">Left-Total</h4></summary>
A left-total relation means that for every element in $A$ there is at least one element in $B$ that it is related to:

$$(\forall a\in A,\exists b\in B)\ aRb$$

Note that all functions are automatically left-total, but not all left-total relations are functions.
</details>

<details>
<summary><h4 class="inline">Surjective</h4></summary>
A relation is surjective every element in $B$ is related to at least one element in $A$:

$$(\exists a\in A,\forall b\in B)\ aRb$$

Similar to left-total relations, surjective relations are also called <b>right-total</b>. When a function is both injective and surjective it forms a bijection.
</details>

### Other Properties
The following properties only apply to homogenous relations (i.e $R\subset X\times X$).
<details>
<summary><h4 class="inline">Reflexive and Irreflexive</h4></summary>
A relation is reflexive if all elements relate to themselves:

$$(\forall x\in X)\ xRx$$

Some example of this are the less than or equal to $\le$ and the divides $\mid$ relations. Relations that don't relate <i>any</i> element to themselves are called <b>irreflexive</b>:

$$(\forall x\in X)\ \neg(xRx)$$

An example of this is the $lt$ relation.
</details>

<details>
<summary><h4 class="inline">Symmetric</h4></summary>
A relation is symmetric if $xRy$ means $yRx$ as well:

$$(\forall x,y\in X)\ xRy \implies yRx$$

Some examples of this include the proportionality $\propto$ of functions and similarity $\sim$ of geometric objects.
</details>

<details>
<summary><h4 class="inline">Anti-Symmetric</h4></summary>
A relation is anti-symmetric if when $xRy$ and $yRx$ are both true, then $x=y$:

$$(\forall x,y\in X)\ xRy\wedge yRx \implies x=y$$

Some examples of this include the $\le$ relation,  

</details>

<details>
<summary><h4 class="inline">Transitive</h4></summary>
A relation is transitive if $xRy$ and $yRz$ means $xRz$:

$$(\forall x,y,z\in X)\ xRy \wedge yRz\implies xRz$$

Relations like $\le$ and similarity $\sim$ are transitive.
</details>

<details>
<summary><h4 class="inline">Trichotomous</h4></summary>
A relation is trichotomus if for any two element in $X$ either $xRy$, $yRx$, or $x=y$ holds. But only 1 of those three options:

$$(\forall x,y\in X)\ (xRy \oplus yRx \oplus x=y) \wedge \neg(xRy \wedge yRx \wedge x=y)$$

The most common example of this is as a property of the real numbers under the $\lt$ or $\gt$ relations. In other words, any real number is either greater than, lesser than, <i>xor</i> equal to any other number.
</details>

## Calculus of Relations
This is a list of different operations and transformations on one or more sets.

<details>
<summary><h4 class="inline">Union and Intersection</h4></summary>
The union of two relations that are on the same sets is equivalent to 'adding/or-ing' them together. For example, the union of the $\lt$ and the $=$ relations is $\le$. Intersection has similar behavior except it displays an 'and' effect.
</details>

<details>
<summary><h4 class="inline">Complement</h4></summary>
The complement of a relation $R\subset A\times B$ is simply all the of the ordered pairs in $A\times B$ that are <i>not</i> in $R$. We can think of this as the ordinary complement of the relation denoted $R^\complement$ where $A\times B$ is the universal set:

$$R^\complement=\{(a,b)\in A\times B\mid (a,b)\not\in R\}$$

For example, the complement of less than or equal to is greater than: $\le^\complement=\gt$. The complement of "is a parent of" is "is not a parent of".
</details>

<details>
<summary><h4 class="inline">Logical Negation of a Relation</h4></summary>
Notice that negating a relation is equivalent to asserting its complement (assuming both elements being related are in the universal set). Put more formally, if $a\in A$ and $b\in B$:

$$\neg(aRb)\equiv aR^\complement b$$

It is this negating property that allows us to replace statements like $\neg(a\le b)$ with  $a\gt b$.
</details>

<details>
<summary><h4 class="inline">Composition</h4></summary>
The composition of two relations $R\subset A\times B$ and $S\subset B\times C$ is a sort of 'product' denoted $S\circ R\subset A\times C$:

$$S\circ R=\{(a,c)\in A\times C\mid\exists b:(a,b)\in R\wedge(b,c)\in S\}$$

<i>Notice that relation composition is associative: $X\circ (Y\circ Z)=(X\circ Y)\circ Z$</i><p></p>

An intuitive example of this can be found in kinship relations. The composition "is parent of" $\circ$ "is father of" returns the new relation "is grandfather of".
</details>

<details>
<summary><h4 class="inline">Converse</h4></summary>
The converse of a relation $R$ is denoted $R^\top$ and is simply the opposite of $R$. In other words, if $(x,y)$ is in a relation then $(y,x)$ is in its converse. Formally, for a relation $R\subset A\circ B$:

$$R^\top=\{(b,a)\in B\times A\mid (a,b)\in R\}$$

<i>Note that this means that the converse is idempotent: $(R^\top)^\top=R$. It also respects composition: $(R\circ L)^\top=L^\top\circ R^\top$.</i><p></p>

For example, the converse of the greater than relation $\ge^\top$ is $\le$. Similarly, the converse of the relation "is a child of" is "is a parent of".
</details>

<details>
<summary><h4 class="inline">Inverse</h4></summary>
Some relations are <i>invertible</i> meaning that for a relation $R$ there exists another relation $X$ such that $X\circ R=I$, called <b>left-invertible</b>, or if there exists a relation $Y$ such that $R\circ Y=I$, called <b>right-invertible</b>. When both the left and right inverses concincide, the inverse $R^{-1}$ is simply equivalent to the converse $R^\top$. <p></p>

For example, the composition "is child of" $\circ$ "is parent of" returns the identity relation (i.e "is you"). As such, they are inverses of each other.
</details>
