---
layout: post
title: Intro Probability Notes Ch. 3
date: 2018-12-31
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

### Properties
$$\begin{align*}
P(A|\Omega)&=P(A)\tag{Identity of Conditional Probability}\\
P(A)P(A|B)&=P(B)P(B|A) \tag{Bayes' Theorem}
\end{align*}$$

*Where $A,B$ are events and $\Omega$ is the sample space.*

### Multiplication Rule
Note that we can rearrange the conditional probability formula as so:

$$P(EF)=P(F)P(E|F)$$

giving us a formula for the probability of the intersection of events.
We can extend this formula to the intersection of multiple events like so:

$$P(E_1E_2E_3\cdots E_n)=P(E_1)P(E_2|E_1)P(E_3|E_1E_2)\cdots P(E_n|E_1E_2\cdots E_{n-1})$$

Or more succinctly:

$$P\left(\bigcap_{i=1}^n E_i\right)=\prod_{i=1}^n\left(E_i\mid\bigcap_{i=1}^{n-1} E_i\right)$$
