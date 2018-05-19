---
layout: post
title: Natural Numbers
date: 2018-05-19
tags: math set-theory
---
## What are Natural Numbers?
The natural numbers are considered the most *natural* set of numbers humans can begin to think of, observe and calculate. They are the numbers we count with $0,1,2,3,4,5,\cdots$ When used to denote the *order* of objects they are considered **ordinal** numbers. When used to describe the quantity of a set of objects they are considered **cardinal** numbers. This distinction becomes important when the naturals are extended to include transfinite numbers.

#### Is $0$ an element of $\mathbb{N}$?
Some definitions of the natural numbers don't include $0$ but, all things considered, including it makes defining the naturals as well as expressing a variety formulae easier. As such, whenever I reference the set of naturals it will always contain $0$. The [notation](#notation) for different variations is cleared up below.

<!--more-->

## Definition
The natural numbers are defined by defining the empty set as zero, then defining the next number, or **successor**, as the set of all previous numbers:

$$\begin{align}
0&\equiv\emptyset\\
1&\equiv\{0\}=\{\emptyset\}\\
2&\equiv\{0,1\}=\{\emptyset,\{\emptyset\}\}\\
3&\equiv\{0,1,2\}=\{\emptyset,\{\emptyset\},\{\emptyset,\{\emptyset\}\}\}\\
&\ \ \vdots\\
n&\equiv\{0,1,2,3,\cdots,n-1\}\\
\end{align}$$

Defining the naturals in this way gives us the first part of the [von Neumann ordinals](http://mathworld.wolfram.com/OrdinalNumber.html).

#### Successor Function
This definition of the naturals can be more succinctly written via the successor function $S(n)$ which returns the number that comes after $n$:

$$S(n)=n\cup\{n\}$$

So, if $0$ is $\emptyset$ then:

$$\begin{align}
S(0)&=0\cup\{0\}\\
&=\emptyset\cup\{\emptyset\}\\
&=\{\emptyset\}
\end{align}$$

And remeber, we define $1$ to be the successor, or number that comes after, $0$. As such $1\equiv S(0)=\{\emptyset\}$. The same is true for all natural numbers: $n+1\equiv S(n)$.

#### Existence in ZFC
While it is possible to construct the successor of every natural number using the axiom of pairing (to prove the existence of the singleton set) and the axiom of union, we can only prove that any *finite* natural number exists. No matter how many successors we compute, there will always be another.

So how do we prove the existence of the infinite set of natural numbers? Well, as it turns out, the only way to do this is to simply declare that such a set exists. This is the **axiom of infinity**:

$$\exists S\left(\emptyset\in S\land\forall x\in S\left(\left(x\cup\{x\}\right)\in S\right)\right)$$

In English, the above statement asserts that there exists a set $S$ that contains the empty set $\emptyset$ as well as contains the successor to every one of its members. Notice that since we can always take the successor of another number, this set is *necessarily* infinite. Indeed all infinite sets from ZFC originate from this set $S$ which we more commonly denote $\mathbb{N}$.

## Notation
The set of natural numbers is denoted by the double struck capital letter $\mathbb{N}$. But there are variations on the set that do/don't include $0$ as well as include all natural numbers up to and including $n$:

$$\begin{alignat*}{2}
&\mathbb{N}&&=\{0,1,2,3,4,5,\cdots\}\\
&\mathbb{N}^* &&=\{1,2,3,4,5,\cdots\}\\
&\mathbb{N}_n&&=\{0,1,2,3,4,\cdots,n\}\\
&\mathbb{N}^* _ n&&=\{1,2,3,4,\cdots,n\}\\
\end{alignat*}$$

The last one in particular, the set of all non-zero natural numbers up to $n$, can be written as the integer interval $[1\ldotp\ldotp n]$ to avoid confusion.
