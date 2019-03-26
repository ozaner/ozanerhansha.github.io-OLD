---
layout: post
title: Relations
date: 2019-03-17
tags: math set-theory relations
---
Relations are used to establish $n$-way relationships between elements of the same or different sets (ex. there is a two way relationship between $2$ and $5$ in that $2<5$). Some important types of relations include partial orders, equivalence relations, and functions.

<!-- Relations are some of the most fundamental objects to set theory and mathematics as a whole. They allow us to formalize the relationships between different mathematical objects and concepts in the broadest sense.  -->


<!--
Some examples of relations include:
- $\vec v\perp\vec u$ Orthogonality
- $x^2$ Square function
- $n|m$ Divisibility
- $x\le y$ Less than or equal to -->

Relations with certain properties can be further collected to form particular mathematical structures like fields, ordered sets, and vector spaces that can be studied further.

<!-- We can call a predicate with $n\ge2$ free variables a **relationship** between those variables. That is, given a particular choice of $n$ variables, the relationship $P$ may or may not hold:

$$P(x_1,x_2,x_3,\cdots,x_n)$$

If we limit the domain of each variable $x_i$ in the predicate as belonging to some corresponding set $S_i$, we can define the solution set $G$ to the relationship $P$ as follows:

$$G=\{(x_1,x_2\cdots,x_n)\in S_1\times S_2\times\cdots\times S_n\mid P(x_1,x_2,\cdots,x_n)\}$$

We can now extend the idea of relationships to set theory by constructing a **relation** between those $n$ sets which will be characterized by the solution set $G$, commonly called its **graph**. -->

<!--more-->

## Definition
An **$n$-ary relation** $R$ is an ordered pair of an $n$-ary [Cartesian product](\cartesian-product) $\prod_{i=1}^n$ and a subset of that product $G$:

$$R\equiv\left(\prod_{i=1}^nS_i,G\right)$$

The set $S_i$ is called the $i$th **domain** of $R$ and the subset $G$ is called the **graph** of $R$. We can always extract the domains of $R$ from the Cartesian product by [factoring](\cartesian-product#factoring) them out.

Note that this implies that (for $n\ge3$) any $n$-ary relation can also be considered an $(n-1)$-ary relation. That said, there is always a maximum $n$ for which an $n$-ary relation can be considered (i.e. the number of prime Cartesian factors).

*e.g. the first domain of an $n$-ary relation $R$ is $\operatorname{CF}_1^n(\pi_1(R))$*

When the domains of the relation are understood from context, it is common for people to simply identify the relation by its graph. This is analogous to identifying an algebraic structure with just its underlying set.

<!-- #### Indexed & Infinitary Relations
Note that, since we have already defined [indexed Cartesian products](\cartesian-product#indexed--infinitary-products), this definition of relations covers infinitary relations (i.e. relations with an infinite number of arguments). The arity of such a relation is, as in the finite case, the cardinality of the index set of the Cartesian product.

While first order logic doesn't support predicates with an infinite number of free variables, we can still salvage this connection by simply considering the variable to be the list as a whole rather than its infinite components.

$$P(x_1,x_2,\cdots)\rightarrow P(\{x_i\}_{i\in I})$$

*That said there are some logics, namely [infinitary logic](https://plato.stanford.edu/entries/logic-infinitary/), that allow for predicates with a countably infinite number of free variables.* -->

#### Existence in ZFC
Because [cartesian products exist](/cartesian-product#existence-in-zfc), invoking the axiom of subset tells us that their subsets exist too (i.e. graphs). This, combined with the [existence of $n$-tuples](/n-tuples#existence-in-zfc), is enough to conclude that relations must also exist.

#### Simultaneity of Arity

<!-- #### Large Relations & Proper Classes

some solution sets are to big to be sets how to phrase that. generalize the reelation

predicate and free vairables but not bounded by some domain. -->

## Notation
Relations are very common mathematical objects and thus have special notation associated to them. Below are common notations for denoting that $n$-elements are related by some relation, i.e. that a given tuple is in the graph $G$ of a relation $R$:

#### $n$-ary Relations
Given an $n$-ary relation $R$, it is common to write the left-hand statement in place of the more formal right-hand one:

$$Rx_1x_2\cdots x_n \equiv (x_1,x_2,\cdots,x_n)\in G$$

*Where $G$ is the graph of the relation $R$.*

#### Binary Relations
While we could use $Rxy$ for binary relations as above, it is often more convenient to write:

$$xRy\equiv (x,y)\in G$$

This notation is ubiquitous, for example: $3\le5$, $ABC \cong ADC$, $\mathbf v\perp\mathbf u$, etc...


## Empty, Universal, and Identity Relations
#### Negation
To denote that a tuple does *not* satisfy a relation, we draw a strikethrough

#### Empty Relation
An $n$-ary **empty relation** is a relation whose graph is the empty set. That is, any relation of the form:

$$E=\left(\prod_{i=1}^nS_i,\emptyset\right)$$

Thus no element of a Cartesian product satisfies its empty relation:

$$\left(\forall(x_1,x_2,\cdots,x_n)\in\prod_{i=1}^nS_i\right)\neg Ex_1x_2\cdots x_n$$

Note that if any one of the domains $S_i=\emptyset$, then the relation is necessarily an empty relation. This is because the [zero property of the Carteisan product](/cartesian-product#empty-set) means that one of the sets $S_i$ being empty forces the entire product to be empty along with, by extension, any subset of that product.

<!-- The corresponding relationship to such a relation is simply one that is never satisfied by any combination of elements $x_i$ from the domains $S_i$:

$$\left(\forall \{x_i\}_{i=1}^n\in \prod_{i=1}^nS_i\right)\ \neg P(x_1,x_2,x_3,\cdots,x_n)$$ -->

#### Universal Relation
Similar to an empty relation, a universal relation is one whose graph includes every element of the Cartesian product of its domains:

$$U=\left(\prod_{i=1}^nS_i,\prod_{i=1}^nS_i\right)$$

Thus every element of a Cartesian product satisfies its universal relation:

$$\left(\forall(x_1,x_2,\cdots,x_n)\in\prod_{i=1}^nS_i\right) Ux_1x_2\cdots x_n$$

#### Identity Relation
Unlike the empty and universal relations which can be defined for any Cartesian product, the identity relation can only be defined as a relation on a set (see below). An identity relation is a binary relation where each element is only related to itself:

$$I=\left(S\times S,\{(x,x)\mid x\in S\}\right)$$

Thus the identity relation satisfies the following property:

$$\forall x,y\in S\ \left(xIy\iff x=y\right)$$

## Properties of Binary Relations
The most common type of relations are binary. This is in part due to the fact that many higher arity relations can be broken up into a collection of binary relations.

<!-- This is in part because many relations can be [*curried*](https://en.wikipedia.org/wiki/Currying) into several different binary relations -->

A binary relation on two different sets $A$ and $B$ is called *heterogenous* when $A\not=B$ and *homogenous* when $A=B$. Homogenous relations are also called **relations on a set**.

Below is a list of common classifications of binary relations based on what properties they satisfy. In all the definitions below we will assume $R=(A\times B,G)$ where $G\subseteq A\times B$:

### Uniqueness Properties

<details>
<summary><strong>Injective</strong></summary>
A relation is called injective if for all $b\in B$, the $a\in A$ is unique in the expression $aRb$. More formally, $R$ is injective if:

$$\forall a_1,a_2\in A, \forall b\in B \left(a_1Rb\wedge a_2Rb\implies a_1=a_2\right)$$

Because of this property, injective relations are also called <b>left-unique</b>.
</details>

<details>
<summary><strong>Functional</strong></summary>
A relation is functional if for all $a\in A$ on the left side, the $b\in B$ on the right is unique. Relations that fulfill this property are called <b>functions</b> and are said to have a unique output $b$ for a given input $a$. Formally this means:

$$\forall a\in A, \forall b_1,b_2\in B \left(aRb_1\wedge aRb_2\implies b_1=b_2\right)$$

Similar to injective relations, a functional relation is also called <b>right-unique</b>.
</details>

<!-- <details>
<summary><strong>One-to-One</strong></summary>
One-to-One functions are relations that are both functional and injective. These functions map every element in their domain to a unique element in the range. These are also called <b>injective functions</b> because being functional is implied in the classification 'function'.
</details> -->

### Totality Properties

<details>
<summary><strong>Left-Total</strong></summary>
A left-total relation means that for every element in $A$ there is at least one element in $B$ that it is related to:

$$(\forall a\in A,\exists b\in B)\ aRb$$

Note that all functions are automatically left-total, but not all left-total relations are functions.
</details>

<details>
<summary><strong>Surjective</strong></summary>
A relation is surjective every element in $B$ is related to at least one element in $A$:

$$(\exists a\in A,\forall b\in B)\ aRb$$

Similar to left-total relations, surjective relations are also called <b>right-total</b>. When a function is both injective and surjective it forms a bijection.
</details>

### Homogenous Properties
The following properties only apply to homogenous relations, i.e. $A=B=X$.
<details>
<summary><strong>Reflexive and Irreflexive</strong></summary>
A relation is reflexive if all elements relate to themselves:

$$(\forall x\in X)\ xRx$$

Some example of this are the less than or equal to $\le$ and the divides $\mid$ relations. Relations that don't relate <i>any</i> element to themselves are called <b>irreflexive</b>:

$$(\forall x\in X)\ \neg(xRx)$$

An example of this is the $\lt$ relation.
</details>

<details>
<summary><strong>Symmetric</strong></summary>
A relation is symmetric if $xRy$ implies $yRx$ as well:

$$\forall x,y\in X \left(xRy \implies yRx\right)$$

Some examples of this include the [proportionality](/proportionality) $\propto$ of functions and similarity $\sim$ of geometric objects.
</details>

<details>
<summary><strong>Anti-Symmetric</strong></summary>
A relation is anti-symmetric if when $xRy$ and $yRx$ are both true, then $x=y$:

$$\forall x,y\in X \left(xRy\wedge yRx \implies x=y\right)$$

Some examples of this include the $\le$ relation,

</details>

<details>
<summary><strong>Transitive</strong></summary>
A relation is transitive if $xRy$ and $yRz$ means $xRz$:

$$\forall x,y,z\in X \left(xRy \wedge yRz\implies xRz\right)$$

Relations like $\le$ and similarity $\sim$ are transitive.
</details>

<details>
<summary><strong>Trichotomous</strong></summary>
A relation is trichotomus if for any two element in $X$ either $xRy$, $yRx$, or $x=y$ holds. But only 1 of those three options:

$$(\forall x,y\in X)\ (xRy \oplus yRx \oplus x=y) \wedge \neg(xRy \wedge yRx \wedge x=y)$$

The most common example of this is as a property of the real numbers under the $\lt$ or $\gt$ relations. In other words, any real number is either greater than, lesser than, <i>xor</i> equal to any other number.
</details>

## Calculus of Relations
Below we include a collection of common transformations and operations on relations along with their associated notation and terminology.

<details>
<summary><strong>Union and Intersection</strong></summary>
The union of two relations with the same domains $R_1,R_2\subseteq\prod S_i$ and graphs $G_1,G_2$ is the following relation:

$$R_1\cup^* R_2\equiv \left(\prod S_i,G_1\cup G_2\right)$$

The same goes for the intersection of two relations with the same domains:

$$R_1\cap^* R_2\equiv \left(\prod S_i,G_1\cap G_2\right)$$

And of course, we can generalize the relational union and intersection of to a finite number of relations with the same domains $n$:

$$\bigcup_{i=1}^n{\vphantom{\bigcup}}^*R_i=\left(\prod S_i,\bigcup_{i=1}^n G_i\right)$$

$$\bigcap_{i=1}^n{\vphantom{\bigcup}}^*R_i=\left(\prod S_i,\bigcap_{i=1}^n G_i\right)$$

<i>Note that the relational union/intersection above are not true set unions/intersections, hence the $ *$ above their symbols. This is because we don't define relations as JUST their graphs but as an ordered pair including it, making their set union/intersection a bit awkward. That said, when the context is clear, the $ *$ can be omitted.</i>
<p></p>
Here are some examples:
<ul>
<li>$<\cup^*I=\le$ The union of less than and the identity relation is less than or equal to.</li>
<li>$\ge\cap^*>=I$ The intersection of greater than or equal to and greater than is the identity relation.</li>
</ul>
<p></p>
</details>

<details open>
<summary><strong>Complement</strong></summary>
The complement of a relation $R\subset A\times B$ is simply all the of the ordered pairs in $A\times B$ that are <i>not</i> in $R$. We can think of this as the ordinary complement of the relation denoted $R^\complement$ where $A\times B$ is the universal set:

$$R^\complement=\{(a,b)\in A\times B\mid (a,b)\not\in R\}$$

For example, the complement of less than or equal to is greater than: $\le^\complement=\gt$. The complement of "is a parent of" is "is not a parent of".
<p></p>
</details>

<details>
<summary><strong>Logical Negation of a Relation</strong></summary>
Notice that negating a relation is equivalent to asserting its complement (assuming both elements being related are in the universal set). Put more formally, if $a\in A$ and $b\in B$:

$$\neg(aRb)\equiv aR^\complement b$$

It is this negating property that allows us to replace statements like $\neg(a\le b)$ with  $a\gt b$.
</details>

<details>
<summary><strong>Composition</strong></summary>
The composition of two relations $R\subset A\times B$ and $S\subset B\times C$ is a sort of 'product' denoted $S\circ R\subset A\times C$:

$$S\circ R=\{(a,c)\in A\times C\mid\exists b:(a,b)\in R\wedge(b,c)\in S\}$$

<i>Notice that relation composition is associative: $X\circ (Y\circ Z)=(X\circ Y)\circ Z$</i><p></p>

An intuitive example of this can be found in kinship relations. The composition "is parent of" $\circ$ "is father of" returns the new relation "is grandfather of".
</details>

<details>
<summary><strong>Converse</strong></summary>
The converse of a relation $R$ is denoted $R^\top$ and is simply the opposite of $R$. In other words, if $(x,y)$ is in a relation then $(y,x)$ is in its converse. Formally, for a relation $R\subseteq A\times B$:

$$R^\top=\{(b,a)\in B\times A\mid (a,b)\in R\}$$

<i>Note that this means that the converse is idempotent: $(R^\top)^\top=R$. It also respects composition: $(R\circ L)^\top=L^\top\circ R^\top$.</i><p></p>

For example, the converse of the greater than relation $\ge^\top$ is $\le$. Similarly, the converse of the relation "is a child of" is "is a parent of".
</details>

<details>
<summary><strong>Inverse</strong></summary>
Some relations are <b>invertible</b>. This means for a relation $R$ there exists another relation $X$ such that $X\circ R=I$, called <b>left-invertible</b>, or if there exists a relation $Y$ such that $R\circ Y=I$, called <b>right-invertible</b>. When both the left and right inverses coincide, the inverse $R^{-1}$ is simply equivalent to the converse $R^\top$.<p></p>
</details>

<!-- For example, the composition "is child of" $\circ$ "is parent of" returns the identity relation (i.e "is you"). As such, they are inverses of each other. -->
