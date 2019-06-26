---
layout: post
title: The Fundamental Principle of Counting
date: 2019-06-25
tags: math set-theory probability-theory
---
The fundamental principle of counting is a basic combinatorial, and ultimately set-theoretic, statement regarding the number of outcomes two events can have when taken together.

The principle states that if two events are independent (that is, one doesn't affect the other) and the first has $m$ possible outcomes and the second has $n$ possible outcomes, then the events taken together have $mn$ possible outcomes.

<!--more-->

Formally, if $A$ is the set of all outcomes of the first event and $B$ the second:

$$A=\{a_1,a_2,\cdots,a_m\}\ \ \ \ \ B=\{b_1,b_2,\cdots,b_n\}$$

then the set of combined outcomes is just their [cartesian product](\cartesian-product) $A\times B$:

$$A\times B=\{(a,b)\mid a\in A\wedge b\in B\}=\left\{
\begin{matrix}
    (a_1,b_1), & (a_1,b_2), & \dots & (a_1,b_n), \\
    (a_2,b_1), & (a_2,b_2), & \dots & (a_2,b_n), \\
    \vdots & \vdots & \ddots & \vdots \\
    (a_m,b_1), & (a_m,b_2), & \dots & (a_m,b_n)
\end{matrix}\right\}$$

The basic principle, then, just reiterates that the [product of cardinalities](\cartesian-product#cardinal-multiplication) is equal to the cardinality of the cartesian product:

$$|A\times B|=|A||B|=mn$$

#### Example
For example, consider rolling two dice, where the event of rolling a die is given by $D=\{1,2,3,4,5,6\}$. Since these are independent events (rolling one dice doesn't affect the outcome of the other) the set of outcomes for rolling two dice is given by $D\times D$. An example of an outcome is $(3,2)$ which corresponds to rolling a $3$ on the first die and a $2$ on the second. The fundemental principle tells us that the number of different possible dice rolls is given by:

$$|D\times D|=|D||D|=6\cdot6=36$$

*Note here that $(3,2)$ is different from $(2,3)$. That is to say, order matters.*

#### Generalizations
This of course generalizes to, not just two, but any number of independent events due to the properties of multiplication:

$$\left|\prod_{i\in I}S_i\right|=|S_1\times S_2\times\cdots|=|S_1||S_2|\cdots=\prod_{i\in I}|S_i|$$

The cardinality of the cartesian product serves as the definition of the (possibly infinitary) product of cardinals. Below is an example of the product of an infinite number of infinite sets:

$$|\mathbb Z^{\aleph_0}|=|\underbrace{\mathbb Z\times \mathbb Z\times\cdots}_{\aleph_0}|=|\mathbb Z||\mathbb Z|\cdots=\aleph_0\aleph_0\cdots=\aleph_0^{\aleph_0}=\mathfrak{c}=|\mathbb R|$$

#### Independence of Outcomes
It is important to note that if the outcome of the first experiment *does*  affect the second experiment (i.e. not independent), then certain pairs of outcomes may not be possible. The cartesian product, then, wouldn't represent all possible outcomes as it would include impossible ones as well. An example might be if rolling a 2 on the first die precluded you from rolling a 4 on the second dice. This would mean $(2,4)$ was not a possible event and $|D\times D|$ is $1$ too high. 

#### Without Explicit Sets
Sometimes if the first event affects the second, it is possible to still use the fundamental principle regardless of the particular sets of outcomes. For example, if we want the set of all two digit strings with no repeats we have 10 choices of digits for the first digit and 9 choices for the second:

$$|\{(0,1),(2,3),(9,3),\cdots\}|=10\cdot 9=90$$

Notice that while we cannot represent the above as a cartesian product of two sets (i.e. it doesn't have a [cartesian factorization](\cartesian-product#cartesian-factorization)) because the set of possible choices of the second element changes for every choice of the first element, we do know the *cardinality* of the set of second choices and thus can still use the basic principle.