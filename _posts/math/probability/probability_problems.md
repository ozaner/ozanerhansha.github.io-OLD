---
layout: post
title: Miscellaneous Probability Problems
date: 2019-02-24
tags: math probability
---
This is a collection of random (ha) exercises relating to combinatorics and probability theory. Most of them are taken from Ross' *A First Course in Probability*.

## Chapter 2 - Problems
#### Problem 1
**Question:** Consider a box with 1 red, 1 green, and 1 blue marble. Whenever a marble is chosen from the box, it is replaced with a marble of the same color. What sample space $\Omega$ represents this? What about when the marble isn't replaced?

**Answer:** When sample space for the first half of the experiment is the same as the second, i.e. replacement is in effect:

$$\Omega=\{r,g,b\}^2$$

Without replacement, the sample space looks like:

$$\Omega=\{(r,g),(r,b),(g,r),(g,b),(b,r),(b,g)\}$$

Where the first element of each outcome is the first choice and likewise for the second. Note that this sample space has no [cartesian factorization](\cartesian-product#cartesian-factorization).

#### Problem 2
**Question:** A die is rolled continually until a 6 appears. What is the sample space of this experiment? Let $E_n$ denote the event that $n$ rolls were needed to end the experiment. What outcomes are in $E_n$?

**Answer:** The sample space of this experiment is the set of all finite sequences of integers from $[1..5]$ (we can omit the final $6$ as it is redundant):

$$\Omega = \bigcup_{n\in\mathbb N} [1..5]^n$$

The event $E_n$ is simply all sequences of length $n-1$ (because the last roll counts):

$$E_n = [1..5]^{n-1}$$

#### Problem 3
**Question:** Two dice are thrown. Let $E$ be the event that their sum is odd, $F$ that at least one die is a $1$, and $G$ be that their sum is $5$. Give the events $EF$, $E\cup F$, $FG$, $EF^\complement$, and $EFG$.

**Answer:** $EF$ is the event that the dice's sum is odd *and* one of them is a $1$:

$$EF=\{(x,y)\mid x+y \equiv 1 \bmod{2}\wedge (x=1\vee y=1)\}$$

$E\cup F$ is the event that either the sum is odd *or* one die is a $1$:

$$EF=\{(x,y)\mid x+y \equiv 1 \bmod{2}\vee (x=1\vee y=1)\}$$

$FG$ is the event that 1 die is a $1$ *and* their sum is a 5. This leaves only two possibilities:

$$FG=\{(1,4),(4,1)\}$$

$EF^\complement$ is the event that the sum is odd and that *no* die is a $1$:

$$EF=\{(x,y)\mid x+y \equiv 1 \bmod{2}\wedge (x\not=1\wedge y\not=1)\}$$

and finally, $EFG$ is the event that the sum is odd, there is at least one $1$, and that the sum is $5$. This again leaves two possibilities and is the same as $FG$:

$$EFG=\{(1,4),(4,1)\}$$

#### Problem 4
**Question:** Player A, B, and C take turns flipping a coin. The first to get heads wins. The sample space of this experiment is the following:

$$\Omega = \{1,01,001,0001,\cdots,0000\dots\}$$

Interpret the sample space, and define the following events in terms of $\Omega$: Player A wins is event $A$, player B wins is $B$, and $(A\cup B)^\complement$

**Answer:** The first $\omega$ outcomes of the sample space each represent how many rounds until someone got a heads. Whoever was flipping is round-robin assigned to each bit (A is first, B is second, C is third, A is fourth, etc.). The $\omega$th element is the outcome where the game never ends.

Event $A$ is the set of all outcomes whose length modulo 3 is 0, because A takes the first flip. Likewise, event $B$ is the set of all outcomes whose length module 3 is 1. Note that this doesn't include the never ending outcome as nobody wins there. They are trapped. Forever.

Note that $(A\cup B)^\complement = A^\complement B^\complement$, so this event is the set of all outcomes whose length modulo 3 is neither 0 nor 1. Note that this includes the never ending outcome.

#### Problem 5
**Question:** A system has 5 components, each of which can be either working or failed. The sample space of observing the status of the system is thus a $5$-tuple where the $i$th element is a $0$ if failed and a $1$ if working. How big is the sample space? If the system works when component 1 and 2 are working or when 3 and 4 are working or when 1, 3, and 5 are working, then what is the event $W$ that the system is working? What is the event $A$ that 4 and 5 have failed? Write out all outcomes of $AW$.

**Answer:** The sample space is the set of all bit strings (sequences of 0's and 1's) of length 5:

$$\Omega =\{0,1\}^5$$

The system is working when at least 1 of those 3 conditions are satisfied:

$$W=\{(x_1,x_2,x_3,x_4,x_5)\mid (x_1=x_2=1)\vee(x_3=x_4=1)\vee(x_1=x_3=x_5=1)\}$$

The event $A$ is just when 4 and 5 are 0:

$$A=\{(x_1,x_2,x_3,x_4,x_5)\mid x_4=x_5=0\}$$

Event $AW$ is when the system is working, despite 4 and 5 not working. This only leaves two possibilities (because 3 working is irrelevant):

$$AW=\{(1,1,0,0,0),(1,1,1,0,0)\}$$

#### Problem 6
**Question:**

**Answer:**

#### Problem 8
**Question:** $A$ and $B$ are mutually exclusive events, $P(A)=.3$, and $P(B)=.5$. What is the probability of $A\cup B$, $AB^\complement$, and $AB$

**Answer:** The probabilities are:

$$\begin{align*}
A\cup B &= .3+.5=.8\\
AB^\complement &= .3\cdot(1-.5)=.15\\
AB &= .3\cdot.5=.15\\
\end{align*}$$

#### Problem 15
**Question:**

**Answer:**