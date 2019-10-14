---
layout: post
title: Combinations & Binomial Coefficients
date: 2019-09-09
tags: math combinatorics
---
## Combinations
A **$k$-combination** of a set $S$ is a subset $A$ of $S$ with $k$ elements:

$$A\subseteq S,\,\,\,|A|=k$$

As we can see, combinations themselves aren't all too interesting. Instead it is their enumeration that is of interest, as we'll see below.

<!--more-->

## Binomial Coefficient
The number of $k$-combinations of a finite set $S$ with $n$ elements is given by the **binomial coefficient**:

$$\binom{n}{k}=\frac{n!}{k!(n-k)!}=\frac{n^{\underline {k}}}{k!}=|\{A\subseteq S: |A|=k\}|$$

<details>
<summary><strong>Proof</strong></summary>
Note that the number of ways we can arrange $k$ elements from $n$ is given by <a href="the-basic-principle-of-counting">the principle of counting</a>:

$$n(n-1)(n-2)\cdots3\cdot2\cdot1=n^{\underline {k}}$$

However, this count is of all $k!$ <a href="/permutations">permutations</a> of each set of $k$ elements. So, to get the count of distinct sets of $k$ elements, we simply divide by $k!$:

$$\binom{n}{k}=\frac{n^{\underline {k}}}{k!}$$

</details>
<p></p>
With the term $\binom{n}{k}$ being read as *"$n$ choose $k$"*. The binomial coefficient has combinatorial significance in that it gives the number of ways to choose $k$ elements from a group of $n$ where order doesn't matter.

#### Alternative Notation
Complementary to the notation for [partial permutations](/permutations#partial-permutations), the binomial coefficient is denoted $_nC_k$ and `nCr(n,k)`.

### Binomial Theorem
This eponymous theorem tells us that the expansion of a binomial raised a nonnegative integer power $n$ is given by:

$$(x+y)^n=\sum_{k=0}^n\binom{n}{k}x^{n-k}y^k$$

While powerful, we'll see below that theorem can be generalized to more than two terms.

#### Identities
The binomial coefficient has associated with it a mountain of identities, theorems, and equalities. Listing them all here would be superfluous but we'll prove a two popular ones:

<details>
<summary><strong>Sum of all Binomial Coefficients</strong></summary>
The sum of all binomial coefficients for a given $n$ is:

$$\sum_{k=0}^n\binom{n}{k}=2^n$$

We can prove this via binomial theorem with $x=y=1$:

$$\sum_{k=0}^n\binom{n}{k}1^{n-k}1^k=(1+1)^n=2^n$$

This identity becomes even clearer when we recall that $\binom{n}{k}$ gives the number of $k$ sized subsets of a set $S$ with $n$ elements. And so summing the number of subsets from $0$ to $n$ gives us the number of all subsets of an $n$ element set, or the size of its power set:

$$|\mathcal{P}(S)|=2^n$$

</details>

<details>
<summary><strong>Pascal's Rule</strong></summary>
Pascal's rule is the following recurrence relation:

$$\binom{n-1}{k}+\binom{n-1}{k-1}=\binom{n}{k}$$

We can prove this via the following chain of equalities:

$$\begin{align*}
\binom{n-1}{k}+\binom{n-1}{k-1}&=\frac{(n-1)!}{k!(n-k-1)!}+\frac{(n-1)!}{(k-1)!(n-1-k+1)!}\tag{def. of binomial coefficient}\\
&=(n-1)!\left(\frac{1}{k!(n-k-1)!}+\frac{1}{(k-1)!(n-k)!}\right)\tag{algebra}\\
&=(n-1)!\left(\frac{n-k}{k!(n-k)!}+\frac{k}{k!(n-k)!}\right)\tag{$(n+1)!=(n+1)\cdot n!$}\\
&=(n-1)!\left(\frac{n}{k!(n-k)!}\right)\tag{algebra}\\
&=\frac{n!}{k!(n-k)!}=\binom{n}{k}\tag{def. of binomial coefficient}

\end{align*}$$

Note an alternate form of this identity can be found by increasing both $n$ and $k$ by $1$:

$$\binom{n}{k+1}+\binom{n}{k}=\binom{n+1}{k+1}$$

As we'll see in the next section, this identity provides the basis for a particularly interesting visualization of the binomial coefficient.
</details>

#### Infinite Cardinals
Up until now, we've only been counting combinations of finite sets. That said, the binomial coefficient generalizes to infinite cardinals as well. For any set $A$ with cardinality $\alpha$:

$$\binom{\alpha}{\beta}=|\{B\subseteq A:|B|=\beta\}|$$

## Pascal's Triangle
**Pascal's triangle** is a visual representation of the binomial coefficients that not only serves as an easy to construct good lookup table, but also makes it easy to visualize a variety of identities relating to the binomial coefficient:

![pascal](/assets/math/pascals-rule.png?style=centerme)

Each row is represented by a natural number starting from $0$, and the same for each column. The number in row $n$ and column $k$ is given by $\binom{n}{k}$.

*While the staggering of the rows may make this unclear, the $k$th element of row $n$ is said to be in column $k$.*

As we can see, by starting with just the first two rows, we can iteratively construct Pascal's triangle using Pascal's rule which we proved earlier.

Not only can we see that identity in the triangle, but we can also see that for any row the sum of all it's entries is a power of $2$, just as we proved earlier.

We can generalize Pascal's triangle to a pyramid and, more generally, an $n$ dimensional simplex via the multinomial version of Pascal's rule discussed further below.

## Multinomial Coefficient
Recall that the binomial coefficient gives us the number of ways to pick $k$ items from a group of $n$. Note that this leaves $n-k$ items left over, so it could also be interpreted as being the number of ways to split a group of $n$ into two groups of size $k$ and $n-k$ respectively.

The **multinomial coefficient** generalizes this combinatorial problem, giving the number of ways to split a group of $n$ into $r$ groups of sizes $k_1,k_2,\cdots,k_r$ where $\sum_{i=0}^r k_i=n$. It is given by:

$$\binom{n}{k_1,k_2,\cdots,k_r}=\frac{n!}{k_1!k_2!\cdots k_r!}$$

<details>
<summary><strong>Proof</strong></summary>
We have $n$ choose $k_1$ combinations for the first group, $n-k_1$ choose $k_2$ for the second, and so on. The principle of counting tells us then that the number is:

$$\binom{n}{k_1}\binom{n-k_1}{k_2}\cdots\binom{n-k_1-k_2-\cdots k_{r-1}}{k_r}$$

This gives us a sort of telescoping product where we can cancel out the previous denominator with the next numerator leaving us with:

$\require{cancel}$

$$\frac{n!}{k_1!\cancel{(n-k_1)!}}\frac{\cancel{(n-k_1)!}}{k_2!\cancel{(n-k_1-k_2)!}}\cdots\frac{\cancel{(n-k_1-\cdots-k_{r-1})!}}{0!k_r!}=\frac{n!}{k_1!k_2!\cdots k_r!}$$

</details>
<p></p>
It's easy to see that the binomial coefficient is a special case of multinomial coefficient:

$$\binom{n}{k}=\frac{n!}{k!(n-k)!}=\binom{n}{k,n-k}=\binom{n}{k_1,k_2}$$

The multinomial coefficient is also used in counting the number of [permutations of a multiset](/permutations#multiset-permutations).

### Multinomial Theorem
This generalization of the binomial theorem, allows us to expand any multinomial raised to some nonnegative integer power $n$ in the following manner:

$$(x_1+x_2+\cdots+x_r)^n=\sum_{k_1+k_2+\cdots k_r=n}\binom{n}{k_1,k_2,\cdots, k_r}x_1^{k_1}x_2^{k_2}\cdots x_r^{k_r}$$

*Where the sum is over all tuples $(k_1,k_2,\cdots,k_r)\in\mathbb{N}^r$ whose elements sum to $n$.*

#### Identities
Below we state and prove the same two identities we proved earlier but generalized for the multinomial coefficient.

<details>
<summary><strong>Sum of all Multinomial Coefficients</strong></summary>
The sum of all multinomial coefficients with $r$ terms for a given $n$ is:

$$\sum_{k_1+k_2+\cdots k_r=n}\binom{n}{k_1,k_2,\cdots,k_r}=r^n$$

Analogous to the binomial case, we can prove this via multinomial theorem with $x_i=1$ for all $i\in[0..r]$:

$$\sum_{k_1+k_2+\cdots k_r=n}\binom{n}{k_1,k_2,\cdots, k_r}1^{k_1}1^{k_2}\cdots 1^{k_r}=(1+1+\cdots+1)^n=r^n$$
</details>

<details>
<summary><strong>Multinomial Pascal's Rule</strong></summary>
$$\begin{gather*}
\binom{n-1}{k_1-1,k_2,\cdots,k_r}+\binom{n-1}{k_1,k_2-1,\cdots,k_r}+\cdots+\binom{n-1}{k_1,k_2,\cdots,k_r-1}
\\=\binom{n}{k_1,k_2,\cdots,k_r}
\end{gather*}$$

We can prove this in a similar way as before:

$$\begin{align*}
&\phantom{=}\binom{n-1}{k_1-1,k_2,\cdots,k_r}+\binom{n-1}{k_1,k_2-1,\cdots,k_r}+\cdots+\binom{n-1}{k_1,k_2,\cdots,k_r-1}\\
&=\frac{(n-1)!}{(k_1-1)!k_2!\cdots k_r!}+\frac{(n-1)!}{k_1!(k_2+1)!\cdots k_r!}+\cdots+\frac{(n-1)!}{k_1!k_2!\cdots (k_r-1)!}\\
&=(n-1)!\left(\frac{1}{(k_1-1)!k_2!\cdots k_r!}+\frac{1}{k_1!(k_2-1)!\cdots k_r!}+\cdots+\frac{1}{k_1!k_2!\cdots (k_r-1)!}\right)\\
&=(n-1)!\left(\frac{k_1}{k_1!k_2!\cdots k_r!}+\frac{k_2}{k_1!k_2!\cdots k_r!}+\cdots+\frac{k_r}{k_1!k_2!\cdots k_r!}\right)\\
&=(n-1)!\left(\frac{k_1+k_2+\cdots+k_r}{k_1!k_2!\cdots k_r!}\right)=(n-1)!\left(\frac{n}{k_1!k_2!\cdots k_r!}\right)\\
&=\frac{n!}{k_1!k_2!\cdots k_r!}=\binom{n}{k_1,k_2,\cdots,k_r}
\end{align*}$$

Using the multinomial coefficient and the recurrence relation above, we can create Pascal's pyramid for trinomials or, more generally, Pascal's simplex for some arbitrary number of dimensions.
</details>

## Multiset Coefficient
A **$k$-multicombination** of a set $S$ is a multisubset of cardinality $k$:

$$A\subseteq S,\,\,\,|A|=k$$

*Note that $k$ can be any cardinality, since we can add an arbitrary number of copies of any single element (unless $S=\emptyset$).*

This, like before, comes with its own notation for counting the number of possible $k$-multisubsets of a set with $n$ elements:

$$\left(\!\!{n \choose k}\!\!\right)=\binom{n+k-1}{k}=\frac{(n+k-1)!}{k!(n-1)!}=\frac{n^{\overline {k}}}{k!}$$

Where $\left({n \choose k}\right)$ is read *"$n$ multichoose $k$"*.

The multiset coefficient comes in handy for a variety of combinatoric problems:

- It is the number of ways we can split a group of $k$ things into $n$ groups (with groups of $0$ being allowed).

- Equivalently, it is the number of ways to choose $k$ elements from a group of $n$ *with* replacement, as opposed to *without* for a normal combination.

<!-- https://en.wikipedia.org/wiki/Stars_and_bars_(combinatorics) -->

<!-- Just like with the normal binomial coefficient, a variety of identities can be proved with the multiset coefficient, such as the multiset version of Pascal's rule. We'll shelve the exploration of said identities however. -->