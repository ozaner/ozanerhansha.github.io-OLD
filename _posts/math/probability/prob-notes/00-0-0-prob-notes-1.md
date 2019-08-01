---
layout: post
title: Intro Probability Notes Ch. 1
date: 2018-12-24
tags: math probability-theory
---
My notes on Ross' *A First Course in Probability*. Chapter 1 - Combinatorics

<!-- ## Basic Principle of Counting
The basic principle of counting states that if two events are independent and the first has $m$ possible outcomes and the second has $n$ possible outcomes, then the events taken together have $mn$ possible outcomes.

Formally, if $A$ is the set of all outcomes of the first experiment and $B$ the second:

$$A=\{a_1,a_2,\cdots,a_m\}\ \ \ \ \ B=\{b_1,b_2,\cdots,b_n\}$$

then the set of combined outcomes is just their [cartesian product](\cartesian-product) $A\times B$:

$$A\times B=\{(a,b)\mid a\in A\wedge b\in B\}=\left\{
\begin{matrix}
    (a_1,b_1), & (a_1,b_2), & \dots & (a_1,b_n), \\
    (a_2,b_1), & (a_2,b_2), & \dots & (a_2,b_n), \\
    \vdots & \vdots & \ddots & \vdots \\
    (a_m,b_1), & (a_m,b_2), & \dots & (a_m,b_n)
\end{matrix}\right\}$$

The basic principle, then, just reiterates that the [product of cardinalities](\cartesian-product#cardinal-multiplication) is equal to the cardinality of the cartesian product:

$$|A\times B|=|A||B|=mn$$

This of course generalizes to, not just two, but any number of independent events due to the properties of multiplication. It even generalizes to infinite cardinalities, although those aren't particularly useful in combinatorics.

#### Independence of Outcomes
It is important to note that if the outcome of the first experiment *does*  affect the second experiment (i.e. not independent), then certain pairs of outcomes may not be possible, e.g. $(a_3,b_2)$. The cartesian product, then, wouldn't represent all possible outcomes as it would include impossible ones as well.

Sometimes if the first event affects the second, it is possible to still use the basic principle regardless of the particular sets of outcomes. For example, if we want the set of all two digit strings with no repeats we have 10 choices of digits for the first digit and 9 choices for the second:

$$|\{(0,1),(2,3),(9,3),\cdots\}|=10\cdot 9=90$$

Notice that while we cannot represent the above as a cartesian product of two sets (i.e. it doesn't have a [cartesian factorization](\cartesian-product#cartesian-factorization)) because the set of possible choices of the second element changes for every choice of the first element, we do know the *cardinality* of the set of second choices and thus can still use the basic principle. -->

## Basic Principle of Counting
[See here.](/the-basic-principle-of-counting)

## Permutations
Given a set of $n$ distinct elements, we can use the basic principle to derive the number of ways we can arrange, or **permutate**, them. If we have $n$ choices for the first element, $n-1$ for the second and so on, we are left with:

$$n(n-1)(n-2)\cdots 3\cdot 2\cdot 1=n!$$

And so there are $n!$ way to rearrange a list of $n$ *distinct* elements. What if they aren't distinct? Given a multiset of size $n$ with $r$ unique elements, each with their own multiplicities $m_i$, the number of permutations is given by:

$$\frac{n!}{m_1!m_2!\cdots m_{r-1}!m_r!}$$

*to be clear $n$ is the sum of the multiplicities of the elements in the multiset: $n=\sum_1^r m_i$*

Dividing by the factorial of each element's multiplicity accounts for all the permutations where identical elements were swapped (leading to no change). Notice that this definition generalizes the unique element case where all the multiplicities are 1.

<!--more-->

## Combinations & Binomial Coefficients
Another combinatorial problem is how many different sets of $r$ groups can be formed from $n$ distinct elements:

$$\frac{n!}{(n-r)!\ r!}=\binom{n}{r}$$

The parenthetical notation above is used for denoting combinations and is read "$n$ choose $r$" and is called a binomial coefficient. Note that we define $\binom{n}{r}=0$ for $r< 0$ because there are no ways to split a set into less than 0 groups, and for $r>n$ because there are no ways to split a set into more groups than there are elements. The binomial theorem, discussed below, provides additional rationale to this definition.

#### Explanation of Formula
Note that the formula is equivalent to:

$$\frac{n!}{(n-r)!\ r!}=\frac{n(n-1)\cdots(n-r+1)}{r!}$$

The numerator applies the basic principle to the $n$ choices for the first group, $n-1$ for the second and so on up to the number of groups $r$. The $r!$ accounts for the groups overcounted by enumerating all their permutations, because order doesn't matter.

#### Recursive Identity
A special identity of the binomial coefficient is:

$$\binom{n}{r}=\binom{n-1}{r-1}+\binom{n-1}{r}$$

The binomial coefficient has many other [interesting identities](https://en.wikipedia.org/wiki/Binomial_coefficient#Identities_involving_binomial_coefficients).

#### Binomial Theorem
The binomial theorem tells us the coefficients of each term in the expansion of the binomial $(x+y)^n$ as we vary $n$:

$$(x+y)^n=\sum^n_{k=0}\binom{n}{k}x^ky^{n-k}$$

We can prove the above statement via induction (I'll do it later).

#### Multinomial Coefficients
Another question a combinatorialist might ask is how many ways a set of $n$ distinct elements can be partitioned into groups of size $n_1,n_2,\cdots,n_r$ where all the groups add up to $n$. We have $n$ choose $n_1$ combinations for the first group, $n-n_1$ choose $n_2$ for the second, and so on giving us:

$$\binom{n}{n_1}\binom{n-n_1}{n_2}\cdots\binom{n-n_1-n_2-\cdots n_{r-1}}{n_r}$$

Note that this gives us a sort of telescoping product where we can cancel out the previous denominator with the next numerator leaving us with:

$$\frac{n!}{(n-n_1)!n_1!}\frac{(n-n_1)!}{(n-n_1-n_2)!n_2!}\cdots\frac{(n-n_1-\cdots-n_{r-1})!}{0!n_r!}=\frac{n!}{n_1!n_2!\cdots n_r!}$$

Analgous to binomial coefficents, we have a special parenthetical notation for these **multinomial coefficients**:

$$\binom{n}{n_1,n_2,\cdots,n_r}=\frac{n!}{n_1!n_2!\cdots n_r!}$$

*where $\sum_i^r n_i=n$*

As you might've guessed, the binomial theorem can be extended to any multinomial using the above in the following way:

$$(x_1+x_2+\cdots+x_r)^n=\sum_{n_1+n_2+\cdots n_r=n}\binom{n}{n_1,n_2,\cdots, n_r}x_1^{n_1}x_2^{n_2}\cdots x_r^{n_r}$$

*Where the sum is taking place over all tuples $(n_1,n_2,\cdots,n_r)$ with $0\le n_i\le n$ that sum to $n$.*

<!-- TODO:
- Pascal's triangle
- Generalization of Pascal's Triangle. -->
