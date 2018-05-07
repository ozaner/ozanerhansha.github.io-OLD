---
layout: post
title: Parity Sequences
date: 2018-03-03
tags: math
---
<!-- Thought about this when we had to find Taylor series' for certain sinusoidal functions and the terms had hard to capture patterns of negative/even terms. It is possible to capture this via more sinusoidal functions but I wanted a polynomial answer. I don't think there is a polynomial answer for the general case, and the 2 examples below are the extent of my findings. -->

A parity sequence is a pattern of alternating even and odd numbers. Only the parity of the numbers is important, not the actual values themselves. As such, we can represent the parity sequence of a sequence as a list of "$+$" for even and "$-$" for odd numbers.

## Definition and Equivalence
Consider the set of all integer sequences (that is, all functions from the natural numbers to the integers):

$$S_\mathbb{Z}\equiv\{f\mid f:\mathbb{N}\to\mathbb{Z}\}$$

We can define an equivalence relation $Ꝑ$ on $S_\mathbb{Z}$ that relates sequences that have the same parity for each element:

$$Ꝑ\equiv\{\left(a_n,b_n\right)\in (S_\mathbb{Z})^2\mid\forall n\in\mathbb{N},\ (-1)^{a_n}=(-1)^{b_n}\}$$

Or in English: if $-1$ to the $n$th element of sequence $a_n$ equals $-1$ to the $n$th element of sequence $b_n$, then the sequences are **parity equivalent**. We can write this more succinctly as:

$$\begin{align}
a_nꝐb_n&\equiv (a_n,b_n)\in Ꝑ\\
&\equiv (-1)^{a_n}=(-1)^{b_n}
\end{align}$$

Using this notion of parity equivalence, we can say that a parity sequence of a given sequence $S_n$ is simply its equivalence class in $Ꝑ$:

$$[S_n]=\{x\mid a_nꝐx\}$$

## $+$ and $-$ Notation
Because a parity sequence is uniquely defined by the parity of any one of its members' elements, we can construct the following notation:

## Parity Swap
A useful property to take note of when constructing these sequences is that adding $1$ to the sequence flips the parity of each element in the sequence:

$$\begin{align}
S_n=\frac{n(n-1)}{2}&=\{0,0,1,3,6,10,\cdots\}\\
&\rightarrow\{+,+,-,-,+,+,\cdots\}\\
S'_ n=\frac{n(n-1)}{2}+1&=\{1,1,2,4,7,11,\cdots\}\\
&\rightarrow\{-,-,+,+,-,-,\cdots\}
\end{align}$$

## Evening/Odding Out
When any parity sequence is multiplied by $2$ it becomes parity equivalent to $2n$. This is called evening out:

$$\forall S_n:2S_n=\{+,+,+,+,+,\cdots\}$$

Similarly, when any parity sequence is multiplied by $2$ then increased by $1$, it becomes parity equivalent to $2n+1$. This is called odding out:

$$\forall S_n:2S_n+1=\{-,-,-,-,-,\cdots\}$$


## Use
Notice that when we raise $-1$ to the power of one of these sequences, it will evaluate to $+1$ for even values and $-1$ for odd values.

*This property is where the $+$ $-$ notation comes from.*

When constructing things like Taylor Series', this is a useful property to have. Terms that alternate from negative to positives can be dealt with by appending a factor of $(-1)^{S_n}$ to the series.

<!--more-->
## Examples
#### Base Case Parity Sequences
The two most simple parity sequences are simply the natural numbers:

$$\begin{align}
S_n=n&=\{0,1,2,3,4,5,6,7,\cdots\}\\
&\rightarrow\{+,-,+,-,+,-,+,-,\cdots\}\\
\end{align}$$

and the even numbers:

$$\begin{align}
S_n=2n&=\{0,2,4,6,8,10,12,14,\cdots\}\\
&\rightarrow\{+,+,+,+,+,+,+,+,\cdots\}\\
\end{align}$$

These two sequences can be parity swapped (explained below) to form the parity sequences $\{-,+,-,+,-,+,\cdots\}$ and $\{-,-,-,-,-,-,\cdots\}$ respectively.

#### The Fibonacci Sequence
The Fibonacci sequence can be considered a parity sequence with the pattern:

$$\begin{align}
F_n=F_{n-2}+F_{n-1}&=\{0,1,1,2,3,5,8,13,\cdots\}\\
&\rightarrow\{+,-,-,+,-,-,+,-,\cdots\}\\
\end{align}$$

$$\text{where } F_0=0, F_1 = 1$$

<details>
  <summary>Closed Form</summary>
  <p>

  $$\begin{align}
  F_n=\frac{\phi^n-\psi^n}{\sqrt 5}&=\{0,1,1,2,3,5,8,13,\cdots\}\\
  &\rightarrow\{+,-,-,+,-,-,+,-,\cdots\}\\
  \end{align}$$

  $$\begin{align*}
  \text{where } &\phi=\frac{1+\sqrt 5}{2} \text{ (the golden ratio)}\\
  &\psi=\frac{1-\sqrt 5}{2} \text{ (the conjugate golden ratio)}
  \end{align*}$$
  </p>
</details>

#### Other Examples
All examples start indexing at 0 (the most rational way to index lists).

$$\begin{alignat*}{2}
  S_n=\frac{n(n-1)}{2}& &&= \{0,0,1,3,6,10,15,21,\cdots\} && \\
  & &&\rightarrow\{+,+,-,-,+,+,-,-,\cdots\} && \\
  S_n=\frac{n^2(n-1)}{2}& &&= \{0,0,2,9,24,50,90,630,\cdots\} &&\\
  & &&\rightarrow\{+,+,+,-,+,+,+,-,\cdots\}&&\\
  S_n=\cos \frac{n\pi}{2}& &&= \{1,0,-1,0,1,0,-1,0,\cdots\} &&\\
  & &&\rightarrow\{-,+,-,+,-,+,-,+,\cdots\}&&
\end{alignat*}$$
