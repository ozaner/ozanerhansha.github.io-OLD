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

A parity sequence is a pattern of alternating even and odd numbers. Only the parity of the numbers is important, not the actual values themselves. As such, we can represent the parity sequence of a sequence as a list of "$+$" for even and "$-$" for odd numbers. Below I formally define the notion of a parity sequence, and some of their properties (at least the ones I could think of off the top of my head).

## Definition and Equivalence
Consider the set of all integer sequences (that is, all functions from the natural numbers to the integers):

$$\mathbb{Z}^\mathbb{N}\equiv\{f\mid f:\mathbb{N}\to\mathbb{Z}\}$$

<!--more-->

We can define an equivalence relation $\sim$ on $\mathbb{Z}^\mathbb{N}$ that relates sequences that have the same parity for each element:

<!-- $$\sim\equiv\{\left(a_n,b_n\right)\in (\mathbb{Z}^\mathbb{N})^2\mid\forall n\in\mathbb{N},\ (-1)^{a_n}=(-1)^{b_n}\}$$ -->

$$\sim\equiv\{\left(a,b\right) \in \mathbb{Z}^\mathbb{N} \times \mathbb{Z}^\mathbb{N} \mid \forall n\in\mathbb{N},\ (-1)^{a_n}=(-1)^{b_n}\}$$

Or in English: if $-1$ to the $n$th element of sequence $a_n$ equals $-1$ to the $n$th element of sequence $b_n$, then the sequences are **parity equivalent**. We can write this more succinctly as:

$$\begin{align}
a\sim b&\equiv (a,b)\in \sim\\
&\equiv (-1)^{a_n}=(-1)^{b_n}
\end{align}$$

Using this notion of parity equivalence, we can say that a parity sequence $P$ of a given sequence $S$ is simply its equivalence class in $\sim$:

$$P=[S]=\{x\in \mathbb{Z}^\mathbb{N}\mid S\sim x\}$$

## $+$ and $-$ Notation
Because a parity sequence is uniquely defined by the parity of the elements of any one of its members, we can represent the parity sequence of a sequence by replacing all its even terms with a $+$ and its odd terms with a $-$. For example:

$$n^2=\left(0,1,4,9,16,25,36,49,\cdots\right)$$

$$[n^2]=\left(+,-,+,-,+,-,+,-,\cdots\right)$$

*As a shorthand, I will refer to sequences, like the sequence $(n^2)_ {n\in\mathbb{N}}$ above, by simply their $n$th term starting at $n=0$. This should not introduce any ambiguities.*

#### What are $+$ and $-$?
If we want to formalize the $+$ $-$ notation we can define them as such:

$$+\equiv0 \ \ \ \ \ \ \ \ -\equiv1$$

Thus the parity sequence $[n]$ is simply:

$$\left(+,-,+,-,+,-,\cdots\right)=\left(0,1,0,1,0,1,\cdots\right)$$

Another point to make is that $[n]\not=\left(+,-,+,-,+,-,\cdots\right)$ but in fact is an element of it:

$$\left(+,-,+,-,+,-,\cdots\right)=\left(0,1,0,1,0,1,\cdots\right)\in[n]$$

We only write $[n]=\left(+,-,+,-,+,-,\cdots\right)$ as a shorthand. And again, we can do this because a parity sequence is uniquely defined by the parity of the elements (integers) of any one of its members (integer sequences), meaning there are no ambiguities.

## Parity Swap
A useful property to take note of when constructing these sequences is that adding $1$ to a sequence flips the parity of each element in the sequence. After performing this **parity swap** on a parity sequence $P$, we call the resulting parity sequence $\bar{P}$:

$$P=[n^2]=\left(+,-,+,-,+,-,+,\cdots\right)$$

$$\bar{P}=[n^2+1]=\left(-,+,-,+,-,+,-,\cdots\right)$$

This is an obvious consequence of the fact that an even number plus $1$ is an odd number and vice versa for odd numbers. This means that performing a parity swap on a sequence $2$ times or any even amount of times results in $P$ and doing it any odd number of times results in $\bar{P}$.

## Evening/Odding Out
When an integer sequence is multiplied by $2$ it becomes parity equivalent to $2n$. This is called **evening out** a sequence:

$$[2S_n]=\left(+,+,+,+,+,\cdots\right)$$

Similarly, when a sequence is multiplied by $2$ then increased by $1$, it becomes parity equivalent to $2n+1$. This is called **odding out** a sequence:

$$[2S_n+1]=\left(-,-,-,-,-,\cdots\right)$$

*Note that odding out a sequence is equivalent to evening it out then parity swapping it. $2S_n$ is the evening and the $+1$ is the parity swap.*

## Uses
Notice that when we raise $-1$ to the power of one of these sequences, it will evaluate to $+1$ for even values and $-1$ for odd values.

*This property is where the $+$ $-$ notation comes from.*

When constructing things like Taylor Series', this is a useful property to have. Terms that alternate from negative to positive in different patterns can be dealt with by appending a factor of $(-1)^{S_n}$ to the series.

Parity equivalence also allows us to simplify otherwise overly complicated sequences and expressions purely using algebra rather than writing the terms out and trying to spot the pattern. Here's an example:

$$(-1)^{\sin \frac{n\pi}{2}}\left(\frac{n^2-2n}{3}\right)^n$$

At first this expression seems a little intimidating. However, notice that $\sin \frac{n\pi}{2}$ and $n$ are parity equivalent:

$$\left[\sin \frac{n\pi}{2}\right]=\left[n\right]=\left(+,-,+,-,+,-,+,-,\cdots\right)$$

Using this knowledge, and the fact that $-1$ is being raised to this sequence, we can simplify the above expression as so:

$$\begin{align}
(-1)^{\sin \frac{n\pi}{2}}\left(\frac{n^2-2n}{3}\right)^n&=(-1)^{n}\left(\frac{n^2-2n}{3}\right)^n\\
&=\left(\frac{2n-n^2}{3}\right)^n
\end{align}$$

Remember, parity equivalence is only defined on the integers (rational and real numbers don't have parity) so the above result only holds for integer $n$.

## Examples of Parity Sequences
All examples start indexing at 0 (the most rational way to index lists).
#### Base Case Parity Sequences
The two most simple parity sequences are simply the natural numbers:

$$n=\left(0,1,2,3,4,5,6,7,\cdots\right)$$

$$[n]=\left(+,-,+,-,+,-,+,-,\cdots\right)$$

and the positive even numbers:

$$2n=\left(0,2,4,6,8,10,12,14,\cdots\right)$$

$$[2n]=\left(+,+,+,+,+,+,+,+,\cdots\right)$$

These two sequences can be parity swapped to form the parity sequences $\left(-,+,-,+,-,+,\cdots\right)$ and $\left(-,-,-,-,-,-,\cdots\right)$ respectively.

#### The Fibonacci Sequence
The Fibonacci sequence can be considered a parity sequence with the pattern:

$$\begin{align}
F_n&=F_{n-2}+F_{n-1}\\
&=\left(0,1,1,2,3,5,8,13,\cdots\right)\\
\end{align}$$

$$\text{where } F_0=0 \land F_1 = 1$$

$$[F_n]=\left(+,-,-,+,-,-,+,-,\cdots\right)$$

<details>
  <summary>Closed Form</summary>
  <p>

  $$\begin{align}
  F_n=\frac{\phi^n-\psi^n}{\sqrt 5}&=\left(0,1,1,2,3,5,8,13,\cdots\right)
  \end{align}$$

  $$[F_n]=\left(+,-,-,+,-,-,+,-,\cdots\right)$$

  $$\begin{align*}
  \text{where } &\phi=\frac{1+\sqrt 5}{2} \text{ (the golden ratio)}\\
  &\psi=\frac{1-\sqrt 5}{2} \text{ (the conjugate golden ratio)}
  \end{align*}$$
  </p>
</details>

#### Other Examples

$$\begin{alignat*}{2}
  \frac{n(n-1)}{2}& &&= \left(0,0,1,3,6,10,15,21,\cdots\right) && \\
  \left[\frac{n(n-1)}{2}\right]& &&=\left(+,+,-,-,+,+,-,-,\cdots\right) && \\\\
  \frac{n^2(n-1)}{2}& &&= \left(0,0,2,9,24,50,90,630,\cdots\right) &&\\
  \left[\frac{n^2(n-1)}{2}\right]& &&=\left(+,+,+,-,+,+,+,-,\cdots\right)&&\\\\
  \cos \frac{n\pi}{2}& &&= \left(1,0,-1,0,1,0,-1,0,\cdots\right) &&\\
  \left[\cos \frac{n\pi}{2}\right]& &&=\left(-,+,-,+,-,+,-,+,\cdots\right)&&
\end{alignat*}$$
