---
layout: post
title: Relations
date: 2018-05-17
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

#### Existence in ZFC
We proved that [cartesian products](/cartesian-product#existence-in-zfc) existed in another post and because relations are subsets of cartesian products, we only need to invoke the axiom of subset to prove their existence.

## Properties of Binary Relations
The most common type of relations are binary. This is simply because they and are simpler to work with and come up more frequently than higher arity relations.

<!-- This is in part because many relations can be [*curried*](https://en.wikipedia.org/wiki/Currying) into several different binary relations -->

A binary relation on two different sets $A$ and $B$ is called *heterogenous* when $A\not=B$ and *homogenous* when $A=B$. Homogenous relations are also called **relations on a set**.

Below is a list of common types of binary relations:

<details>
<summary><h3 class="inline">Heterogenous Classifications</h3></summary>
<i>Note that these classifications also apply to homogenous relations as well</i>
<h4>Injective</h4>
A relation is called injective 
<h4>Functional</h4>
<h4>One-to-One</h4>
<h4>Left-Total</h4>
<h4>Surjective</h4>
</details>

<details>
<summary><h3 class="inline">Homogenous Classifications</h3></summary>
<h4>Reflexivity</h4>
<h4>Symmetric</h4>
<h4>Anti-Symmetric</h4>
<h4>Transitive</h4>
<h4>Trichotomy</h4>
</details>

## Calculus of Relations
#### Union and Intersection
The union of two relations that are on the same sets is equivalent to 'adding/or-ing' them together. For example, the union of the $\lt$ and the $=$ relations is $\le$. Intersection has similar behavior except it displays an 'and' effect.

#### Complement
The complement of a relation $R\subset A\times B$ is simply all the of the ordered pairs in $A\times B$ that are *not* in $R$. We can think of this as the ordinary complement of the relation denoted $R^\complement$ where $A\times B$ is the universal set:

$$R^\complement=\{(a,b)\in A\times B\mid (a,b)\not\in R\}$$

For example, the complement of less than or equal to is greater than: $\le^\complement=\gt$. The complement of "is a parent of" is "is not a parent of".

**Negation of a Relation**

Notice that negating a relation is equivalent to asserting its complement (assuming both elements being related are in the universal set). Put more formally, if $a\in A$ and $b\in B$:

$$\neg(aRb)\equiv aR^\complement b$$

It is this negating property that allows us to replace statements like $\neg(a\le b)$ with  $a\gt b$.

#### Composition
The composition of two relations $R\subset A\times B$ and $S\subset B\times C$ is a sort of 'product' denoted $S\circ R\subset A\times C$:

$$S\circ R=\{(a,c)\in A\times C\mid\exists b:(a,b)\in R\wedge(b,c)\in S\}$$

*Notice that relation composition is associative: $X\circ (Y\circ Z)=(X\circ Y)\circ Z$*

An intuitive example of this can be found in kinship relations. The composition "is parent of" $\circ$ "is father of" returns the new relation "is grandfather of".

#### Converse
The converse of a relation $R$ is denoted $R^\top$ and is simply the opposite of $R$. In other words, if $(x,y)$ is in a relation then $(y,x)$ is in its transpose. Formally, for a relation $R\subset A\circ B$:

$$R^\top=\{(b,a)\in B\times A\mid (a,b)\in R\}$$

*Note that this means that the converse is idempotent: $(R^\top)^\top=R$. It also respects composition: $(R\circ L)^\top=L^\top\circ R^\top$.*

For example, the converse of the greater than relation $\ge^\top$ is $\le$. Similarly, the converse of the relation "is a child of" is "is a parent of".

#### Inverse
Some, but not all, relations are *invertible* meaning that for a relation $R$ there exists another relation $X$ such that $X\circ R=I$, called **left-invertible**, or if there exists a relation $Y$ such that $R\circ Y=I$, called **right-invertible**. When both the left and right inverses concincide, the inverse $R^{-1}$ is simply equivalent to the converse $R^\top$.

For example, the composition "is child of" $\circ$ "is parent of" returns the identity relation (i.e "is you"). As such, they are inverses of each other.

## Examples
#### Less than or equal too
Order relation
#### Divides
#### Similarity
Equivalence relation
#### Congruence
