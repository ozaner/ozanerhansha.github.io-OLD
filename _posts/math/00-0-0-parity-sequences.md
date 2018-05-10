---
layout: post
title: Parity Sequences
date: 2018-05-10
tags: math set-theory
---
<!--
New Date is formal reformulation of parity sequences

Thought about this when we had to find Taylor series' for certain sinusoidal functions and the terms had hard to capture patterns of negative/even terms. It is possible to capture this via more sinusoidal functions but I wanted a polynomial answer. I don't think there is a polynomial answer for the general case, and the 2 examples below are the extent of my findings.

first publish date: 2018-03-03-->

While toying around with infinite alternating series, I become interested in the idea of alternation beyond the simple $+,-,+,-$ like that of the power series of $\sin x$. This is where **parity sequences** come in.

A parity sequence is a pattern of alternating even and odd numbers. Only the parity of the numbers is important, not the actual values themselves. As such, we can represent the parity sequence of a sequence as a list of "$+$" for even and "$-$" for odd numbers. Below I formally define what the notion of a parity sequence, and some of its properties.

## Definition and Equivalence
Consider the set of all integer sequences (that is, all functions from the natural numbers to the integers):

$$\mathbb{Z}^\mathbb{N}\equiv\{f\mid f:\mathbb{N}\to\mathbb{Z}\}$$

<!--more-->

We can define an equivalence relation $₽$ on $\mathbb{Z}^\mathbb{N}$ that relates sequences that have the same parity for each element:

$$\sim\equiv\{\left(a_n,b_n\right)\in (\mathbb{Z}^\mathbb{N})^2\mid\forall n\in\mathbb{N},\ (-1)^{a_n}=(-1)^{b_n}\}$$

Or in English: if $-1$ to the $n$th element of sequence $a_n$ equals $-1$ to the $n$th element of sequence $b_n$, then the sequences are **parity equivalent**. We can write this more succinctly as:

$$\begin{align}
a_n\sim b_n&\equiv (a_n,b_n)\in \sim\\
&\equiv (-1)^{a_n}=(-1)^{b_n}
\end{align}$$

Using this notion of parity equivalence, we can say that a parity sequence of a given sequence $S_n$ is simply its equivalence class in $\sim$:

$$[S_n]=\{x\in S_\mathbb{Z}\mid S_n\sim x\}$$

## $+$ and $-$ Notation
Because a parity sequence is uniquely defined by the parity of the elements of any one of its members, we can represent the parity sequence of a sequence by replacing all its even terms with a $+$ and its odd terms with a $-$. For example:

$$n^2=\{0,1,4,9,16,25,36,49,\cdots\}$$

$$[n^2]=\{+,-,+,-,+,-,+,-,\cdots\}$$

## Parity Swap
A useful property to take note of when constructing these sequences is that adding $1$ to a sequence $P$ flips the parity of each element in the sequence. After performing this **parity swap**, we call the resulting parity sequence $\bar{P}$:

$$P_n=[n^2]=\{+,-,+,-,+,-,+,\cdots\}$$

$$\bar{P_n}=[n^2+1]=\{-,+,-,+,-,+,-,\cdots\}$$

This is an obvious consequence of the fact that an even number plus $1$ is an odd number and vice versa for odd numbers.

## Evening/Odding Out
When any parity sequence is multiplied by $2$ it becomes parity equivalent to $2n$. This is called **evening out** a sequence:

$$[2P_n]=\{+,+,+,+,+,\cdots\}$$

Similarly, when any parity sequence is multiplied by $2$ then increased by $1$, it becomes parity equivalent to $2n+1$. This is called **odding out** a sequence:

$$[2P_n+1]=\{-,-,-,-,-,\cdots\}$$


## Uses
Notice that when we raise $-1$ to the power of one of these sequences, it will evaluate to $+1$ for even values and $-1$ for odd values.

*This property is where the $+$ $-$ notation comes from.*

When constructing things like Taylor Series', this is a useful property to have. Terms that alternate from negative to positives can be dealt with by appending a factor of $(-1)^{P_n}$ to the series.

## Examples
All examples start indexing at 0 (the most rational way to index lists).
#### Base Case Parity Sequences
The two most simple parity sequences are simply the natural numbers:

$$n=\{0,1,2,3,4,5,6,7,\cdots\}$$

$$[n]=\{+,-,+,-,+,-,+,-,\cdots\}$$

and the even numbers:

$$2n=\{0,2,4,6,8,10,12,14,\cdots\}$$

$$[2n]=\{+,+,+,+,+,+,+,+,\cdots\}$$

These two sequences can be parity swapped to form the parity sequences $\{-,+,-,+,-,+,\cdots\}$ and $\{-,-,-,-,-,-,\cdots\}$ respectively.

#### The Fibonacci Sequence
The Fibonacci sequence can be considered a parity sequence with the pattern:

$$\begin{align}
F_n&=F_{n-2}+F_{n-1}\\
&=\{0,1,1,2,3,5,8,13,\cdots\}\\
\end{align}$$

$$\text{where } F_0=0 \land F_1 = 1$$

$$[F_n]=\{+,-,-,+,-,-,+,-,\cdots\}$$

<details>
  <summary>Closed Form</summary>
  <p>

  $$\begin{align}
  F_n=\frac{\phi^n-\psi^n}{\sqrt 5}&=\{0,1,1,2,3,5,8,13,\cdots\}
  \end{align}$$

  $$[F_n]=\{+,-,-,+,-,-,+,-,\cdots\}$$

  $$\begin{align*}
  \text{where } &\phi=\frac{1+\sqrt 5}{2} \text{ (the golden ratio)}\\
  &\psi=\frac{1-\sqrt 5}{2} \text{ (the conjugate golden ratio)}
  \end{align*}$$
  </p>
</details>

#### Other Examples
$$\begin{alignat*}{2}
  \frac{n(n-1)}{2}& &&= \{0,0,1,3,6,10,15,21,\cdots\} && \\
  \left[\frac{n(n-1)}{2}\right]& &&=\{+,+,-,-,+,+,-,-,\cdots\} && \\\\
  \frac{n^2(n-1)}{2}& &&= \{0,0,2,9,24,50,90,630,\cdots\} &&\\
  \left[\frac{n^2(n-1)}{2}\right]& &&=\{+,+,+,-,+,+,+,-,\cdots\}&&\\\\
  \cos \frac{n\pi}{2}& &&= \{1,0,-1,0,1,0,-1,0,\cdots\} &&\\
  \left[\cos \frac{n\pi}{2}\right]& &&=\{-,+,-,+,-,+,-,+,\cdots\}&&
\end{alignat*}$$
