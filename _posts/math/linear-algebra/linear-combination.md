---
layout: post
title: Linear Combination
date: 2018-09-11
tags: math geometry linear-algebra
---
Linear combinations are a key concept in linear algebra as they directly lead into topics like linear independence, span, and basis. Below I provide a definition of them and related concepts.

## Definition
A **linear combination** of the elements of a module is any finite sum of elements from that module scaled by the elements of their underlying ring(s). For a left $R$-module it's any element of the form:

$$\sum_{i=1}^{n}{r_im_i}=r_1m_1+r_2m_2+\cdots+r_nm_n$$

likewise, for a right $S$-module, it's any expression of the form:

$$\sum_{i=1}^{n}{m_is_i}=m_1s_1+m_2s_2+\cdots+m_ns_n$$

<!--more-->

And in general, for a $R$-$S$-bimodule, it is an expression of the form:

$$\sum_{i=1}^{n}{r_im_is_i}=r_1m_1s_1+r_2m_2s_2+\cdots+r_nm_ns_n$$

*Where $m_i\in M$, $r_i\in R$ and $s_i\in S$ and $n$ is finite.*

If $R$ is a commutative ring, then the left/right distinction doesn't matter. This is the case for vector spaces, the focus of the rest of these notes, as they are just special cases of modules over a commutative ring.

## Linear Independence
A set of vectors $X\subseteq V$, where $V$ is a vector space, is **linearly independent** if none of the vectors in the set can be written as linear combinations of the others. The negation of linearly independence is **linearly dependence**.

#### Definition
We can define linear independence as a family of predicates indexed by the class of all vector spaces. That is to say, for every vector space $V$ over a field $F$ there is a corresponding predicate denoted $LI_V(X)$:

$$\operatorname{LI}_V(X)\equiv \sum_{i\in I}{a_i\mathbf x_i}=\mathbf 0\rightarrow (\forall i\in I)\ a_i=0$$

*Where $\mathbf x_i\in X\subseteq V$ and $a_i\in A\subseteq F$. Also both $A$ and $X$ are indexed by the set $I$.*

Note that this predicate only takes in subsets of $V$ and so its domain is $\mathcal{P}(V)$. Also, thanks to the index set, this definition applies to infinite subsets of $V$ as well.

## Linear Span
The linear span of a set of vectors is the set of all *finite* linear combinations of those vectors. This doesn't exclude infinite sets of vectors, just infinite linear combinations.

When the $\operatorname{span}(S_1)=S_2$ we say that $S_1$ spans $S_2$ or that $S_1$ is a **spanning set** of $S_2$.

#### Definition
We can define $\operatorname{span}$ as a family of functions indexed by the class of all vector spaces. That is to say, for every vector space $V$ over a field $F$ there is a corresponding function denoted $span_V(S)$ where $S\subseteq V$:

$$\operatorname{span}_V (S)=\left\{{\left.\sum_{i=1}^{n\in \mathbb{N}}\lambda_{i}\mathbf v_{i}\right|\mathbf v_{i}\in S\wedge\lambda_{i}\in F\wedge n\le \left|S\right|}\right\}$$

*Note that if $n=0$ (empty sum) then the resulting linear combination is the zero vector $\mathbf 0\in V$.*

Notice that $\operatorname{span}_V$ takes in a subset of $V$ and outputs another subset of $V$, because any scalar $\lambda\in F$ times a vector $\mathbf v\in V$ is also in $V$ via closure. In other words, both the domain and range of the function are the power set of $V$:

$$\operatorname{span}_V:\mathcal{P}(V)\to\mathcal{P}(V)$$

#### Notation
When it is clear from the context what vector space is being used we can write $\operatorname{span}_V(S)$ as $\operatorname{span}(S)$ to avoid cluttered notation.

#### Properties (PROVE THEM)
For some $S_1,S_2\subseteq V$ where $V$ is a vector space:

- If

Proof

- $\operatorname{span}(\{\mathbf v,\lambda\mathbf v\})=\operatorname{span}(\{\mathbf v\})$ same applies to any finite amount of linearly dependent vectors.
- $S_1\subseteq \operatorname{span}(S_1)$
- $S_1\subseteq S_2\rightarrow \operatorname{span}(S_1)\subseteq\operatorname{span}(S_2)$
- $\operatorname{span}(S_1)\subseteq V$
- $\mathbf 0\in \operatorname{span}(S_1)$
- if $S_1$ is a basis of $V\rightarrow (\forall \mathbf v\in V) \ \exists!\lambda_{i}\in F\mid \sum_{i=1}^{\operatorname{dim}(V)}\lambda_{i}\mathbf v_{i}=\mathbf v$
- $n$ linearly independent vectors in $V$ span $V$? or just for reals?
- Isomorphism between the span of a single vector and a line (real 2-space). hyperplane and real nspace. (leave for n space post?) any metric space?

## Basis
