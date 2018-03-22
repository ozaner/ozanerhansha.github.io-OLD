---
layout: post
title: Parity Sequences
tags: math
---
<!-- Thought about this when we had to find Taylor series' for certain sinusoidal functions and the terms had hard to capture patterns of negative/even terms. It is possible to capture this via more sinusoidal functions but I wanted a polynomial answer. I don't think there is a polynomial answer for the general case, and the 2 examples below are the extent of my findings. -->

A parity sequence is a sequence of numbers that follow a set pattern of even and odd. The notation we will use is "$+$" for even and "$-$" for odd.

## Examples
All examples start indexing at 0 (the most rational way to index lists).

$$\begin{alignat*}{2}
  S_n=\frac{n(n-1)}{2}& &&= \{0,0,1,3,6,10,15,21,\cdots\} && \\
  & &&\rightarrow\{+,+,-,-,+,+,-,-,\cdots\} && \\
  S_n=\frac{n^2(n-1)}{2}& &&= \{0,0,2,9,24,50,90,630,\cdots\} &&\\
  & &&\rightarrow\{+,+,+,-,+,+,+,-,\cdots\}&&\\
  S_n=\cos \frac{n\pi}{2}& &&= \{1,0,-1,0,1,0,-1,0,\cdots\} &&\\
  & &&\rightarrow\{-,+,-,+,-,+,-,+,\cdots\}&&
\end{alignat*}$$

<!--more-->

## Use
Notice that when we raise $-1$ to the power of one of these sequences, it will evaluate to $+1$ for even values and $-1$ for odd values.

*This property is where the $+$ $-$ notation comes from.*

When constructing things like Taylor Series', this is a useful property to have. Terms that alternate from negative to positives can be dealt with by appending a factor of $(-1)^{S_n}$ to the series.

## Equivalence
When the corresponding elements of two sequences have the same parity, we can call those two sequences **parity equivalent**.

This can be formally stated as:

$$\forall n\in\mathbb{N},\text{ }(-1)^{A_n}=(-1)^{B_n}$$

i.e for all Natural Numbers $n$, if $-1$ to the $A_n$ equals $-1$ to the $B_n$, then the sequences $A$ and $B$ are parity equivalent.

## Parity Swap
A useful property to take note of when constructing these sequences is that adding $1$ to the sequence flips the parity of each element in the sequence:

$$\begin{align}
S_n=\frac{n(n-1)}{2}&=\{0,0,1,3,6,10,\cdots\}\\
&\rightarrow\{+,+,-,-,+,+,\cdots\}\\
S'_n=\frac{n(n-1)}{2}+1&=\{1,1,2,4,7,11,\cdots\}\\
&\rightarrow\{-,-,+,+,-,-,\cdots\}
\end{align}$$
