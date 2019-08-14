---
layout: post
title: Parity Sequences
date: 2018-05-10
tags: math
# relations
---
<!-- New new date is even better reformulation of parity sequences as a commutative ring with associated operations. Also got rid of +- notation
since that would confuse the ring operations.

Also, leave note at end of paper about generalize to the commutative ring of finite parity sequences. an $n$-parity sequence is a sequence of length $n$. There will be 2^n element in this set. Our normal parity sequences would be $\omega$-parity sequences in this more general framework, and we can even go further beyond and consider transfinite parity sequences (although I am hard pressed to find any immediate application of such a ring).

second publish date: 2018-05-10 -->

<!--New Date is formal reformulation of parity sequences

Thought about this when we had to find Taylor series' for certain sinusoidal functions and the terms had hard to capture patterns of negative/even terms. It is possible to capture this via more sinusoidal functions but I wanted a polynomial answer. I don't think there is a polynomial answer for the general case, and the 2 examples below are the extent of my findings.

first publish date: 2018-03-03-->

While toying around with infinite alternating series, I became interested in the idea of alternation of the signs of the terms beyond the simple $+,-,+,-$ like that of the power series of $\sin x$. This is where **parity sequences** come in.

A parity sequence is a pattern of alternating even and odd numbers. Only the parity of the numbers is important, not the actual values themselves. As such, we can canonically represent a parity sequence as a list of $0$'s for even and $1$'s for odd numbers. Below I formally define the notion of a parity sequence, and some of their properties (at least the ones I could think of off the top of my head).

<!--more-->

## Definition
Consider the set of all integer sequences, denoted $\mathbb{Z}^\mathbb{N}$. That is to say, all functions from the natural numbers to the integers:

$$\mathbb{Z}^\mathbb{N}\equiv\{f\mid f:\mathbb{N}\to\mathbb{Z}\}$$

We define an equivalence relation on $\mathbb{Z}^\mathbb{N}$ called **parity equivalence**, denoted $\sim$, that relates sequences whose corresponding elements have the same parity. Given two integer sequences $S$ and $T$, they are parity equivalent if:

<!-- Used to use p with strikethrough symbol (like poke dollers) but wont render on mathjax if used in real paper make a symbol and at the end define it in latex code-->

<!-- $$\sim\equiv\{\left(a_n,b_n\right)\in (\mathbb{Z}^\mathbb{N})^2\mid\forall n\in\mathbb{N},\ (-1)^{a_n}=(-1)^{b_n}\}$$ -->

<!-- $$\sim\equiv\{\left(a,b\right) \in \mathbb{Z}^\mathbb{N} \times \mathbb{Z}^\mathbb{N} \mid \forall n\in\mathbb{N},\ (-1)^{a_n}=(-1)^{b_n}\}$$ -->

<!-- Or in English: if $-1$ to the $n$th element of sequence $a_n$ equals $-1$ to the $n$th element of sequence $b_n$, then the sequences are **parity equivalent**. We can write this more succinctly as: -->

$$\begin{align}
S\sim T \equiv (\forall i\in\mathbb N)\ \ S_i\bmod 2\equiv T_i\bmod 2
\end{align}$$

Using this notion of parity equivalence, we define a **parity sequence** as a particular equivalence class of $\sim$. Thus, given some integer sequence $S$, it's corresponding parity sequence $P$ is:

$$P=[S]=\{x\in \mathbb{Z}^\mathbb{N}\mid S\sim x\}$$

## Canonical Parity Sequence
Because a parity sequence is uniquely defined by the parity of the elements of any one of its members, we can represent any parity sequence with one of it's particular member. For example, given the following sequence:

$$n^2=\left(0,1,4,9,16,25,36,49,\cdots\right)$$

*As a shorthand I will refer to sequences, like the sequence $(n^2)_ {n\in\mathbb{N}}$ above, by simply their $n$th term starting at $n=0$. This should not introduce any ambiguities.*

We can identify it's corresponding parity sequence by the following sequence of $0$'s and $1$'s:

$$\left(0,1,4,9,16,25,36,49,\cdots\right)\sim\left(0,1,0,1,0,1,0,1,\cdots\right)$$

Because every parity sequence contains a *unique* bitstream, there is no ambiguity in identifying that parity sequence as 'equal' to it:

$$[n^2]=\left(0,1,0,1,0,1,0,1,\cdots\right)$$


Of course, the above bitstream doesn't *equal* $[n^2]$. It is a member of it and thus it would be more accurate to write:

$$\left(0,1,0,1,0,1,0,1,\cdots\right)\in[n^2]$$

<!-- Where $+$ denotes an even element and $-$ denotes an odd one. To make things concrete we can say that $+=0$ and $-=1$. This implies that the canonical sequence of a parity sequence is the unique binary sequence, or bitstream, that it contains:

$$\left(+,-,+,-,+,-,+,-,\cdots\right)=\left(0,1,0,1,0,1,0,1,\cdots\right)$$ -->

<!--

This is just a useful shorthand for, as we'll see, performing **parity arithmetic** with parity sequences. -->

<!-- #### What are $+$ and $-$?
If we want to formalize the $+$ $-$ notation we can define them as such:

$$+\equiv0 \ \ \ \ \ \ \ \ -\equiv1$$

Thus the parity sequence $[n]$ is simply:

$$\left(+,-,+,-,+,-,\cdots\right)=\left(0,1,0,1,0,1,\cdots\right)$$

Another point to make is that $[n]\not=\left(+,-,+,-,+,-,\cdots\right)$ but in fact is an element of it:

$$\left(+,-,+,-,+,-,\cdots\right)=\left(0,1,0,1,0,1,\cdots\right)\in[n]$$

We only write $[n]=\left(+,-,+,-,+,-,\cdots\right)$ as a shorthand. And again, we can do this because a parity sequence is uniquely defined by the parity of the elements (integers) of any one of its members (integer sequences), meaning there are no ambiguities. -->

## Unary Operations
#### Parity Swap
A interesting property to take note of when constructing these sequences is that adding $1$ to a sequence flips the parity of each element in the sequence. We can make this an operation, called a **parity swap**, on a parity sequence $P$. We denote the resulting parity sequence $\overline{P}$:

$$P=[n^2]=\left(0,1,0,1,0,1,0,\cdots\right)$$

$$\overline{P}=[n^2+1]=\left(1,0,1,0,1,0,1,\cdots\right)$$

This is an obvious consequence of the fact that an even number plus $1$ is an odd number and vice versa for odd numbers. This means that performing a parity swap on a sequence $2$ times or any even amount of times results in $P$ and doing it any odd number of times results in $\overline{P}$.

#### Evening/Odding Out
When an integer sequence is multiplied by $2$ it becomes parity equivalent to $2n$. This is called **evening out** a sequence:

$$[2S_n]=\left(0,0,0,0,0,\cdots\right)$$

Similarly, when a sequence is multiplied by $2$ then increased by $1$, it becomes parity equivalent to $2n+1$. This is called **odding out** a sequence:

$$[2S_n+1]=\left(1,1,1,1,1,\cdots\right)$$

*Note that odding out a sequence is equivalent to evening it out then parity swapping it. $2S_n$ is the evening and the $+1$ is the parity swap.*

## Commutative Ring
As we'll see below, the set of parity sequences admits a natural notion of addition, subtraction, and multiplication that are all compatible with each other in such a way that they form a commutative ring.

#### Addition & Subtraction
Thinking back to our elementary school educations, we might recall the interesting fact that the parity of the sum (or difference) of two integers is determined by the parity of its summands:
- Even + Even = Even
- Even + Odd = Odd
- Odd + Odd = Even

If we extend this
  
- $[S_i]+[T_i]=[S_i+T_i]$
- $[S_i]-[T_i]=[S_i-T_i]$
- $[S_i]\cdot [T_i]=[S_i\cdot T_i]$ (Pointwise multiplication)

Symmetries/Identities:
- $[S_i]=[|S_i|]$
- $(\forall n\in\mathbb N)\ [S_i]=[S_i+2n]$ (unsurprising as this is just repeated usage of pairs of parity swap)

#### Note on Division
We can't define a natural division on parity sequences (and thus form a field) because
Division isn't defined. Because, even moving past integer division problems, a parity sequence doesn't have enough information to know whether the element had a least 1 factor of 2. Give example of parity changing via pointwise division.

Consider:

$$\begin{align*}
(2,4,6,8,10,12,\cdots)&\sim(4,6,8,10,12,14,\cdots)\\
(0,0,0,0,0,0,\cdots)&=(0,0,0,0,0,0,\cdots)
\end{align*}$$

Now lets pointwise divide both sequences by $2$:

$$\begin{align*}
\frac{(2,4,6,8,10,12,\cdots)}{2}&=(1,2,3,4,5,6,\cdots)\\
\frac{(4,6,8,10,12,14,\cdots)}{2}&=(2,3,4,5,6,7,\cdots)
\end{align*}$$

And as we can see, these two sequences are *not* parity equivalent:

$$\begin{align*}
(1,2,3,4,5,6,\cdots)&\not\sim(2,3,4,5,6,7,\cdots)\\
(1,0,1,0,1,0,\cdots)&\not=(0,1,0,1,0,1,\cdots)
\end{align*}$$


## Uses
Notice that when we raise $-1$ to the power of one of these sequences, it will evaluate to $+1$ for even values and $-1$ for odd values.

<!-- *This property is where the $+$ $-$ notation comes from.* -->

When constructing things like Taylor Series', this is a useful property to have. Terms that alternate from negative to positive in different patterns can be dealt with by appending a factor of $(-1)^{S_n}$ to the series.

Parity equivalence also allows us to simplify otherwise overly complicated sequences and expressions purely using algebra rather than writing the terms out and trying to spot the pattern. Here's an example:

$$(-3)^{\sin \frac{n\pi}{2}}\left(\frac{n^2-2n}{3}\right)^n$$

At first this expression seems a little intimidating. However, notice that $\sin \frac{n\pi}{2}$ and $n$ are parity equivalent:

$$\left[\sin \frac{n\pi}{2}\right]=\left[n\right]=\left(0,1,0,1,0,1,0,1,\cdots\right)$$

Using this knowledge, and the fact that $-1$ is being raised to this sequence, we can simplify the above expression as so:

$$\begin{align}
(-1)^{\sin \frac{n\pi}{2}}\left(\frac{n^2-2n}{3}\right)^n&=(-1)^{n}\left(\frac{n^2-2n}{3}\right)^n\\
&=\left(\frac{2n-n^2}{3}\right)^n
\end{align}$$

Remember, parity equivalence is only defined on the integers (rational and real numbers don't have parity) so the above result only holds for integer $n$.

## Examples of Parity Sequences
<!-- All examples start indexing at 0 (the most rational way to index lists). -->
#### Base Case Parity Sequences
The two most simple parity sequences are simply the natural numbers:

$$n=\left(0,1,2,3,4,5,6,7,\cdots\right)$$

$$[n]=\left(0,1,0,1,0,1,0,1,\cdots\right)$$

and the positive even numbers:

$$2n=\left(0,2,4,6,8,10,12,14,\cdots\right)$$

$$[2n]=\left(0,0,0,0,0,0,0,0,\cdots\right)$$

These two sequences can be parity swapped to form the parity sequences $\left(1,0,1,0,1,0,\cdots\right)$ and $\left(1,1,1,1,1,1,\cdots\right)$ respectively.

#### The Fibonacci Sequence
The Fibonacci sequence can be considered a parity sequence with the pattern:

$$\begin{align}
F_n&=F_{n-2}+F_{n-1}\\
&=\left(0,1,1,2,3,5,8,13,\cdots\right)\\
\end{align}$$

$$\text{where } F_0=0 \land F_1 = 1$$

$$[F_n]=\left(0,1,1,0,1,1,0,1,\cdots\right)$$

<details>
  <summary>Closed Form</summary>
  <p>

  $$\begin{align}
  F_n=\frac{\phi^n-\psi^n}{\sqrt 5}&=\left(0,1,1,2,3,5,8,13,\cdots\right)
  \end{align}$$

  $$[F_n]=\left(0,1,1,0,1,1,0,1,\cdots\right)$$

  $$\begin{align*}
  \text{where } &\phi=\frac{1+\sqrt 5}{2} \text{ (the golden ratio)}\\
  &\psi=\frac{1-\sqrt 5}{2} \text{ (the conjugate golden ratio)}
  \end{align*}$$
  </p>
</details>

#### Other Examples

$$\begin{alignat*}{2}
  \frac{n(n-1)}{2}& &&= \left(0,0,1,3,6,10,15,21,\cdots\right) && \\
  \left[\frac{n(n-1)}{2}\right]& &&=\left(0,0,1,1,0,0,1,1,\cdots\right) && \\\\
  \frac{n^2(n-1)}{2}& &&= \left(0,0,2,9,24,50,90,630,\cdots\right) &&\\
  \left[\frac{n^2(n-1)}{2}\right]& &&=\left(0,0,0,1,0,0,0,1,\cdots\right)&&\\\\
  \cos \frac{n\pi}{2}& &&= \left(1,0,-1,0,1,0,-1,0,\cdots\right) &&\\
  \left[\cos \frac{n\pi}{2}\right]& &&=\left(-,0,1,0,1,0,1,0,\cdots\right)&&
\end{alignat*}$$
