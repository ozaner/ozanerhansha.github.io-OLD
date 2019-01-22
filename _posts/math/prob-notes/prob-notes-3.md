---
layout: post
title: Intro Probability Notes Ch. 3
date: 2019-01-21
tags: math probability-theory
---
Notes for *A First Course in Probability* Ch. 3 - Conditional Probability and Independence

## Conditional Probabilities
Conditional probabilities arise when we have partial information about an experiment. That is, given that an event $F$ has occurred, the probability that an event $E$ occurs is denoted and given by:

$$P(E|F)=\frac{P(EF)}{P(F)}$$

Note that the conditional probability is not defined when $P(F)=0$, which should make sense considering an event that cannot happen cannot possibly be a precondition for another.

<!--more-->

<details>
<summary><strong>Example</strong></summary>
For example, suppose our sample space $S$ is the set of all outcomes of rolling two fair dice:

$$S=[1..6]\times[1..6]$$

What is the probability that the sum of the dice is 8, given that the first die we rolled was a 3? Here, event $E$ is rolling a 3 on the first die and event $F$ is getting a pair that adds to 8:

$$\begin{align*}
E&=\{(3,1),(3,2),(3,3),(3,4),(3,5),(3,6)\}\\
F&=\{(2,6),(3,5),(4,4),(5,3),(6,2)\}\\
EF&=\{(3,5)\}
\end{align*}$$

Remember that each dice roll is equally likely (i.e. this is a uniform distribution) and so the probabilities of the relevant events are:

$$\begin{align*}
P(F)&=\frac{|F|}{|S|}=\frac{5}{36}\\
P(EF)&=\frac{|EF|}{|S|}=\frac{1}{36}
\end{align*}$$

This leaves us with:

$$P(E|F)=\frac{P(EF)}{P(F)}=\frac{1}{5}$$

</details>

#### Edge Cases
Note that since the sample space itself always has a probability of $1$, it serves as a sort of identity for the conditional probability of any event:

$$P(E|\Omega)=\frac{P(E\Omega)}{P(\Omega)}=P(E)$$

Conversely, the conditional probability formula is undefined for events having $0$ probability:

$$P(F)=0\implies P(E|F)=\frac{P(EF)}{P(F)}=\frac{0}{0}$$

This jives with our intuition as it doesn't make sense to consider the probability of an event $E$ under the precondition that an impossible event $F$ occurred.

### Multiplication Rule
Note that we can rearrange the conditional probability formula as so:

$$P(EF)=P(F)P(E|F)$$

giving us a formula for the probability of the intersection of events.
We can extend this formula to the intersection of multiple events like so:

$$P(E_1E_2E_3\cdots E_n)=P(E_1)P(E_2|E_1)P(E_3|E_1E_2)\cdots P(E_n|E_1E_2\cdots E_{n-1})$$

Or more succinctly:

$$P\left(\bigcap_{i=1}^n E_i\right)=\prod_{i=1}^n\left(E_i\mid\bigcap_{i=1}^{n-1} E_i\right)$$

### Law of Total Probability
The law of total probability states that for any countable partition $(B_i)_{i\in I}$ of the sample space $\Omega$, the event $A\in\mathcal F$ satisfies:

$$\begin{align*}
P(A)&=\sum_{i\in I}P(AB_i)\\
&=P(AB_1)+P(AB_2)\cdots
\end{align*}$$

We can think of the sum as a weighted average of the probability of $A$ which should, if the weights sum to 1 (i.e. partition $\Omega$), equal that same probability. Also, note that the multiplication rule allows us to phrase this law as:

$$\begin{align*}
P(A)&=\sum_{i\in I}P(A|B_i)P(B_i)\\
&=P(A|B_1)P(B_1)+P(A|B_2)P(B_2)\cdots
\end{align*}$$

*Where $i$ such that $P(B_i)=0$ are omitted from the sum.*

### Bayes' Theorem
Bayes' Theorem is the simple observation that:

$$P(E|F)=\frac{P(F|E)P(E)}{P(F)}$$

<!-- We can remove the discontinuity when $P(F)=0$ by writing it like so:

$$P(E|F)P(F)=P(F|E)P(E)$$ -->

<details>
<summary><strong>Proof</strong></summary>
$$\begin{align*}
P(FE)&=P(F|E)P(E)\tag{Multiplication Rule}\\
P(E|F)&=\frac{P(EF)}{P(F)}\tag{Def. of conditional prob.}\\
&=\frac{P(FE)}{P(F)}\tag{Commutativity of intersection}\\
&=\frac{P(F|E)P(E)}{P(F)}\tag{substitution}\\
\end{align*}$$

</details>

Using the law of total probability, we can generalize this
