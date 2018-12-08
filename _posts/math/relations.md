---
layout: post
title: Relations
date: 2018-10-25
tags: math set-theory relations
---
We can call a predicate with $n\ge2$ free variables a **relationship** between those variables. That is, given a particular choice of $n$ variables, the relationship $P$ may or may not hold:

$$P(x_1,x_2,x_3,\cdots,x_n)$$

If we limit the domain of each variable $x_i$ in the predicate as belonging to some corresponding set $S_i$, we can define the solution set $G$ to the relationship $P$ as follows:

$$G=\{(x_1,x_2\cdots,x_n)\in S_1\times S_2\times\cdots\times S_n\mid P(x_1,x_2,\cdots,x_n)\}$$

We can now extend the idea of relationships to set theory by constructing a **relation** between those $n$ sets which will be characterized by the solution set $G$, commonly called its **graph**.

<!--more-->

## Definition
An **$n$-ary relation** $R$ is an ordered pair of an $n$-ary [Cartesian product](\cartesian-product) $\prod_{i=1}^n$ and a subset of that product $G$:

$$R\equiv\left(\prod_{i=1}^nS_i,G\right)$$

The set $S_i$ is called the $i$th **domain** of $R$ and the subset $G$ is called the **graph** of $R$. We can always extract the domains of $R$ from the Cartesian product by [factoring](\cartesian-product#factoring) them out.

Note that this implies that (for $n\ge3$) any $n$-ary relation can also be considered an $(n-1)$-ary relation. That said, there is always a maximum $n$ for which an $n$-ary relation can be considered (i.e. the number of prime Cartesian factors).

*When the domains of the relation are understood from context, it is common for people to simply identify the relation by its graph.*

#### Indexed & Infinitary Relations
Note that, since we have already defined [indexed Cartesian products](\cartesian-product#indexed--infinitary-products), this definition of relations covers infinitary relations (i.e. relations with an infinite number of arguments). In particular the arity of such a relation is, as in the finite case, the cardinality of the index set of the Cartesian product.

While first order logic doesn't support predicates with an infinite number of free variables, we can still salvage this connection by simply considering the variable to be the list as a whole rather than its infinite components.

$$P(x_1,x_2,\cdots)\rightarrow P(\{x_i\}_{i\in I})$$

*That said there are some logics, namely [infinitary logic](https://plato.stanford.edu/entries/logic-infinitary/), that allow for predicates with a countably infinite number of free variables.*

#### Empty Relation
*Interestingly, if we don't assume the axiom of choice, it is possible that an infinite Cartesian product of nonempty sets will still produce the empty set.*

An $n$-ary **empty relation** is a relation whose graph is the empty set. That is, any relation of the form:

$$E\equiv(S_1,S_2,\cdots,S_n,\emptyset)$$

Note that if any one of the domains $S_i=\emptyset$ then the relation is necessarily the empty relation. This is because for any set $S$:

$$S\times\emptyset=\emptyset$$

And so any one of the sets $S_i$ being empty will force their product to be empty, thereby forcing $G$ (a subset of that product) to be empty.

The corresponding relationship to such a relation is simply one that is never satisfied by any combination of elements $x_i$ from the domains $S_i$:

$$\left(\forall \{x_i\}_{i=1}^n\in \prod_{i=1}^nS_i\right)\ \neg P(x_1,x_2,x_3,\cdots,x_n)$$

#### Large Relations & Proper Classes

some solution sets are to big to be sets how to phrase that. generalize the reelation

predicate and free vairables but not bounded by some domain.

#### Existence in ZFC
Because [cartesian products exist](/cartesian-product#existence-in-zfc), invoking the axiom of subset tells us that their subsets exist too (i.e. graphs). This, combined with the [existence of $n$-tuples](/n-tuples#existence-in-zfc), is enough to conclude that relations must also exist.

## Notation
Relations are very common mathematical objects and thus have special notation associated to them:

#### $n$-ary Relations
For $n$-ary relations it is common to write:

$$Rx_1x_2x_3\cdots \equiv (x_1,x_2,x_3,\cdots)\in G$$

*Where $G$ is the graph of the relation $R$.*

#### Binary Relations
While we could use $Rxy$ for binary relations, it is more convenient to write:

$$xRy\equiv (x,y)\in R$$

This notation is ubiquitous, for example: $3\le5$, $ABC \cong ADC$, $\mathbf v\perp\mathbf u$, etc...
