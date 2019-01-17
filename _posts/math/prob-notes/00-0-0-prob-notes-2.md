---
layout: post
title: Intro Probability Notes Ch. 2
date: 2018-12-30
tags: math probability-theory
---
Notes for *A First Course in Probability* Ch. 2 - Axioms of Probability

## Sample Spaces and Events
When considering an experiment or real world phenomena whose definite outcome is not known but whose possible outcomes *are* known, we can model it with a sample space. A sample space $S$ is the set of possible outcomes of an experiment. For example, the sample space of a dice roll is:

$$S=\{1,2,3,4,5,6\}$$

An event $E$ is a subset of a sample space. For example, the event that an even number is rolled is:

$$E=\{2,4,6\}$$

We say that an event has occurred if the outcome of the experiment $x$ is an element of the event. For example, if the outcome of the dice roll is $4$, then we say the event $E$ has occurred.

<!--more-->

#### Union and Intersection of Events
Given two events $A$ and $B$, their union is the event that either one happens. For example the union of $A$, rolling an even number, and $B$, rolling a power of two, is:

$$A\cup B=\{2,4,6\}\cup\{1,2,4\}=\{1,2,4,6\}$$

Analogously, the intersection of two events is the event that both happen. For example the intersection of rolling an even and rolling a power of two is:

$$A\cap B=\{2,4,6\}\cap\{1,2,4\}=\{2,4\}$$

*The intersection is also referred to as $AB$.*

This concept extends to arbitrary unions and intersections sets but, due to some finer points regarding measurability, only for countable arbitrary unions/intersections:

$$\left(\forall A\subseteq\mathcal{P}(S)\right)\ |A|\le\aleph_0\rightarrow \bigcup A\in S\wedge \bigcap A\in S$$

#### Null Event
Note that since the empty set is a subset of all sets, it is always an event of a sample space:

$$\left(\forall S\right)\emptyset\subseteq S$$

We call this the **null event**. Take note that the intersection of two disjoint, or **mutually exclusive**, events $EF$ results in the null event.

#### Complement of Events
The complement of an event $E^\complement$, where the universal set is the sample space, is an event that will only occur iff $E$ does not occur. So if the outcome of the experiment is $x\in S$ then:

$$x\in E^\complement\equiv x\not\in E$$

As $S\subseteq S$, it too is an event. Note that its complement $S^\complement=\emptyset$ and that this corresponds to the statement that there must be *some* outcome to the experiment. Also keep DeMorgan's law for sets in mind:

$$(A\cup B)^\complement = A^\complement\cap B^\complement\ \ \ \ \ \ \ (A\cap B)^\complement = A^\complement\cup B^\complement$$

or more generally:

$$\left(\bigcup E_i\right)^\complement=\bigcap E_i^\complement\ \ \ \ \ \ \  \left(\bigcap E_i\right)^\complement=\bigcup E_i^\complement$$

## Axioms of Probability
Consider a sample space $S$, a set of possible events $F\subseteq \mathcal{P}(S)$ called the **event space**, and a function $P:\mathcal F\to\mathbb R$ whose outputs are called **probabilities**. We call the triple $(S,\mathcal F,P)$ a **probability space** if it satisfies the following 3 axioms:

**Axiom 1.** Every event in the event space has a nonnegative probability:

$$\left(\forall E\in \mathcal F\right) P(E)\ge0$$

This is to constrain our notion of probability so that nothing can have a negative chance of happening.

*Notably, this restriction is relaxed when dealing with the probability amplitudes of quantum mechanics.*

**Axiom 2.** The probability of the entire space is $1$:

$$P(S)=1$$

This is called the unitary property, and it corresponds with the fact that every experiment must have *some* outcome in the sample space.

**Axiom 3.** Any countable set of disjoint sets $\{E_i\}_{i=1}^\infty\subseteq\mathcal F$ satisfies:

$$P\left(\bigcup_{i=1}^\infty E_i\right)=\sum_{i=1}^\infty P(E_i)$$

This allows for us to add the probabilities of mutually exclusive events as we expect.

You'll notice that $\mathcal F$ isn't necessarily the power set of $S$. While this definition works fine for countable sets, it runs into trouble when dealing with uncountable ones. Only *measurable* sets then can be included in $\mathcal F$.

#### Consequences
The 3 axioms above, also known as the Kolmogorov axioms, have some immediate consequences that characterize probability spaces:

$$\begin{gather*}
P(\emptyset)=0\\
A\subseteq B\rightarrow P(A)\le P(B)\\
0\le P(A)\le 1\\
P(A\cup B)=P(A)+P(B)-P(A\cap B)\\
P(A^\complement)=1-P(A)
\end{gather*}$$

<!-- - $P(\emptyset)=0$
- $A\subseteq B\implies P(A)\le P(B)$
- $0\le P(A)\le 1$
- $P(A\cup B)=P(A)+P(B)-P(A\cap B)$
- $P(A^\complement)=1-P(A)$ -->

*for any events $A,B\in F$.*

### Inclusion-Exclusion Principle
Recall one of the consequences we mentioned earlier:

$$P(A\cup B)=P(A)+P(B)-P(A\cap B)$$

This is known as the **inclusion-exclusion identity**. With a little more work, we can further generalize it to express the probability of any finite union of events:

$$P\left(\bigcup_{i=1}^nE_i\right)=\sum _{k=1}^{n}\left((-1)^{k-1}\sum _{I\subseteq \{1,\ldots ,n\} \atop |I|=k}{P}(E_{I})\right)$$

*Where $E_I=\bigcap_{i\in I}E_i$ and the sum on the inside is running over all subsets of $I$ with cardinality $k$.*

Essentially its the alternating sum of the probability of every combination of 1 event happening, minus each combination of 2 events happening, plus 3 events and so on. The textbook phrases it as:

$$\begin{align*}
P\left(\bigcup_{i=1}^nE_i\right)&=\sum_{k=1}^{n}\left((-1)^{k-1}\sum_{i_1< i_2<\cdots< i_k}{P}(E_{i_1}\cap\cdots\cap E_{i_k})\right)\\
&=\sum_{i=1}^nP(E_i)-\sum_{j< i}P(E_i\cap E_j)+\sum_{k< j< i}P(E_i\cap E_j\cap E_k)-\cdots
\end{align*}$$

Also note that each partial sum of the above either bounds the probability from above or below:

$$\begin{align*}
P\left(\bigcup_{i=1}^nE_i\right)&\le\sum_{i=1}^nP(E_i)\\
&\ge\sum_{i=1}^nP(E_i)-\sum_{j< i}P(E_i\cap E_j)\\
&\le\sum_{i=1}^nP(E_i)-\sum_{j< i}P(E_i\cap E_j)+\sum_{k< j< i}P(E_i\cap E_j\cap E_k)
\end{align*}$$

and so on, with each successive partial sum being more accurate than the last.

### Discrete Uniform Distribution
Given a finite sample space $S$, a **discrete uniform distribution** is one where each element $s$ in $S$ is equally likely to occur meaning:

$$\left(\forall s\in S\right) P(\{s\})=\frac{1}{|S|}$$

This is a consequence of $P(S)=1$. A further consequence of this is that the probability of any event $E$ is given by:

$$P(E)=\frac{|E|}{|S|}$$

### Increasing and Decreasing Sequences of Events
A sequence of events $\{E_i\}_{i=1}^\infty$ is increasing if:

$$\left(\forall i\in\mathbb Z^+\right) E_i\subseteq E_{i+1}$$

and, likewise, decreasing if:

$$\left(\forall i\in\mathbb Z^+\right) E_i\supseteq E_{i+1}$$

For any such sequence, the following statement about the probability of its limit holds true:

$$\lim_{i\to\infty}P(E_i)=P\left(\lim_{i\to\infty}E_i\right)$$

## Interpretations of Probability
In the real world, probability can be interpreted in one of two ways:

1. The proportion, or frequency, that a particular event will occur when an experiment is continually (in fact infinitely) repeated.
2. The measure of belief an individual may have about the truth of a statement.

That said, as long as the given interpretation obeys the axioms we set out earlier, the calculus of probabilities is just as valid in either case.
