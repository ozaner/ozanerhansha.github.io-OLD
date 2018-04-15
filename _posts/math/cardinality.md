---
layout: post
title: Cardinal Numbers and Cardinality
date: 2018-04-01
tags: math
---
All sets have a property known as cardinality. The cardinality of a set $S$ is denoted $\vert S\vert$ and is equal to a **cardinal number**. For example:

$$S=\{0,1,7\}$$

$$\vert S\vert = \vert \{0,1,7 \}\vert=3$$

Informally, cardinality is 'size' of a set. Indeed for finite sets it is the number of  elements in a set, but for infinite sets (guaranteed by the axiom of infinity in ZFC) a more technical definition is needed.

## Definition of Cardinality
The cardinality of a set $A$ is less than or equal to that of $B$ if there exists a one-to-one (injective) function from $A$ to $B$:

$$\exists f:A\xrightarrow{1-1}B \iff \vert A\vert \le \vert B\vert$$

The cardinality of two sets are thus equal if there exists a bijective function from $A$ to $B$:

$$\exists f:A\xrightarrow{\text{bijective}}B \iff \vert A\vert = \vert B\vert$$

This can be more simply seen as:

$$\left(\vert A\vert \le \vert B\vert\right) \land \left(\vert A\vert \ge \vert B\vert\right) \iff \vert A\vert = \vert B\vert$$

This definition of cardinality allows us to compare infinite cardinalities, something we couldn't do if we simply defined cardinality as the number of elements in a set (which would only apply to finite sets).

However, we'd like to assign objective sizes to different sets (even infinite ones) rather than just compare them. To do this we'll need a new number system that includes natural numbers along with a new set of numbers to describe infinite sizes:

## Cardinal Numbers
The cardinal numbers are a generalization of the natural numbers used to classify the sizes of different sets. For any finite set, its cardinality is a natural number. But, for an infinite set, its size is described by a **transfinite number**. All of these transfinite, or infinite, cardinals are larger than any natural number.

#### Aleph Numbers
The size any countably infinite set (a set for which there exists a bijection with the natural numbers) is denoted $\aleph_0$. Some common sets of this size are:

$$\left|\mathbb{N} \right|=\left|\mathbb{Z} \right|=\left|\mathbb{Q} \right|=\aleph_0$$

$$\underbrace{0,1,2,3,4,5,6,7,8,9,\cdots}_{\text{natural numbers}},\underbrace{\aleph_0,\aleph_1,\aleph_2,\aleph_3,\cdots}_{\text{aleph numbers}}$$

If the axiom of choice is true, then the above sequence accounts for all cardinal numbers (all transfinite numbers are well-ordered.) If the axiom of choice is false then there are more infinite cardinalities in between the aleph numbers.

#### Cardinality of the Continuum
The cardinality of the real numbers $\mathbb{R}$ is denoted $\mathfrak{c}$ and is uncountably infinite. That is to say there is no bijection between it and the natural numbers.

Moreover, via Cantor's theorem (which states that any set is smaller than its power set), we know that $\mathfrak{p}$ $2^{\aleph_0}$

### Law of Trichotomy
Like the natural numbers, the cardinal numbers obey the law of trichotomy (i.e every cardinal has a unique ranking):

$$\forall x\forall y\in C\ ((x>y) \oplus (x=y) \oplus (x<y))$$

Where $C$ is the proper class of cardinal numbers.

*you cannot construct a set of all cardinal numbers, it leads to a contradiction similar to Russell's paradox.*

This
