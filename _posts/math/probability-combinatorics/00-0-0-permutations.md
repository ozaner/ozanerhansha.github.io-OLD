---
layout: post
title: Permutations
date: 2019-08-25
tags: math combinatorics
---
## Definition
A **permutation** on a set $S$ is a bijective function $\sigma$ from $S$ to itself:

$$\sigma:S\to S$$

While permutations are commonly thought of as sequences of a set of elements with no repeats, we can see that the modern mathematical definition of permutation is a bit different.

We can distinguish between these two types by calling the function definition an *active* permutation and the sequence definition a *passive* permutation. In this way we can continue using the word 'permutation' in both situations and simply infer the definition from context.

<!--more-->

## Notation
Permutations are functions commonly denoted by lowercase greek letters (e.g. $\sigma, \pi, \alpha$) and can be written in a variety of special notations, two of which are covered below.

### Two-Line Notation
A common way to define a permutation $\sigma$ on a finite set with $n$ elements, each denoted $s_i\in S$, is via **two-line notation**:

$$\sigma=\begin{pmatrix}s_{1}&s_{2}&\cdots&s_{i}&\cdots &s_{n}\\\sigma (s_{1})&\sigma (s_{2})&\cdots&\sigma (s_{i})&\cdots &\sigma (s_{n})\end{pmatrix}$$

<details>
<summary><h4 class="inline">Example</h4></summary>
For example, a permutation on $\{1,2,3\}$ with $\sigma(1)=3,\sigma(2)=1,\sigma(3)=2$ would be denoted:

$$\sigma=\begin{pmatrix}1&2&3\\3&1&2\end{pmatrix}=\begin{pmatrix}2&3&1\\1&3&3\end{pmatrix}$$

</details>

### One-Line Notation
A more compact notation can be used in liu of the two-line notation if there is some accepted or implied order to the elements of the $S$. In this case there is no need to write the first line as it is implied, giving us the **one-line notation**:

$$\sigma=\begin{pmatrix}\sigma (s_{1})&\sigma (s_{2})&\cdots&\sigma (s_{i})&\cdots &\sigma (s_{n})\end{pmatrix}$$

<details>
<summary><h4 class="inline">Example</h4></summary>
For example, we know there is a common ordering of the natural numbers (i.e. $0,1,2,3,\cdots$) and so we can rewrite our previous example permutation as:

$$\sigma=\underbrace{\begin{pmatrix}3&1&2\end{pmatrix}}_{\text{one-line}}=\underbrace{\begin{pmatrix}1&2&3\\3&1&2\end{pmatrix}}_{\text{two-line}}$$

</details>
<p></p>
You'll notice that in this notation, our permutations look identical to the common notion of permutation. That is, a rearranging of the elements of a sequence.

## Symmetric Group
Under function composition, the set of all permutations of a set $S$ forms a group called the **symmetric group** of $S$:

$$\begin{gather*}
\text{Sym}(S)=(G,\circ)\\
G=\{\sigma\in S\times S\mid\sigma\text{ is a bijection}\}
\end{gather*}$$

*Where denotes $\circ$ function composition over $S\times S$.*

That this is indeed a group can be seen from the following 4 facts:

- Function composition is **associative**.
- The **identity** function is a permutation.
- Because they are bijections, every permutation has an **inverse** which are also permutations since $S=\text{domain}=\text{codomain}$.
- The composition of a bijection with a bijection is also bijection and, because $S=\text{domain}=\text{codomain}$, we have that permutations are **closed** under function composition.

#### Notation
When talking about symmetric groups in general, it is common to denote the symmetric group of an $n$ element set as $S_n$, with the actual elements of the group being unimportant.

## Counting Permutations
The number of different permutations of a set (i.e. the cardinality of it's symmetric group) is one of the most, arguably *the* most, fundamental principles of combinatorics.

Note that for a finite set with $n$ elements, we have $n$ choices for what to map the first element to, $n-1$ choices for the second element, and so on until we reach the $n$th element which has only $1$ choice left to map to.

Thus, by the [principle of counting](/principle-of-counting), the number of distinct permutations of an $n$ element set $S$ is given by the [factorial](\superfactorial-and-hyperfactorial):

$$|\text{Sym}(S)|=n(n-1)(n-2)\cdots3\cdot2\cdot1=n!$$

#### Infinite Sets
While the principle of counting generalizes to infinite sets, it doesn't apply to our argument. Sparing the details of the proof and how it establishes bounds, the number of permutations of an infinite set $S$ with cardinality $\kappa$ is given by:

$$|\text{Sym}(S)|=\kappa^\kappa=2^\kappa=|\mathcal{P}(S)|$$

*Keep in mind that $\vert\text{Sym}(S)\vert$ refers to the order of the group.*

## Generalizations
We now detail two generalizations of passive permutations. One that includes only some elements, and one of multisets. These generalizations are also important to combinatorics and thus have special notations associated to them.

### Partial Permutations
A **$k$-permutation** $\sigma$ of a set $S$ is a sequence of $k$ distinct elements from $S$:

$$\sigma:k\to S,\,\,\,\,(\forall i,j\in k)\,\,\,\,\sigma(i)\not=\sigma(j)$$

*Note this definition only considers $k\le n.$*

#### Counting Partial Permutations
The number of different $k$-permutations a set with $n$ elements has is denoted $_nP_k$, or more commonly in statistics as `nPr(n,k)`. Via the principle of counting, it is given by:

$$_nP_k=n(n-1)(n-2)\cdots(n-k+1)=n^{\underline {k}}$$

Which we can see is just the $k$th falling factorial of $n$. Another way to see this is to recognize that there are $\binom{n}{k}$ combinations of $k$ elements each with $k!$ permutations, giving us:

$$_nP_k=\binom{n}{k}k!=\frac{n!}{(n-k)!k!}k!=\frac{n!}{(n-k)!}=n^{\underline{k}}$$

### Multiset Permutations
Given a multiset $S$ of size $n$, a **multiset permutation** $\sigma$ is a sequence of $S$ in which each element $s_i$ appears exactly as many times as is their multiplicity $k_i$:

$$\sigma:n\to S,\,\,\,\,\big|\{i\in n\mid\sigma(i)=s_i\}\big|=k_i$$

#### Counting Multiset Permutations
The number of different multiset permutations a multiset $S$ of size $n$ has is simply $n!$ divided by the number of permutations of identical elements, i.e. the factorial of each element's multiplicity:

$$\frac{n!}{k_1!k_2!\cdots k_r!}=\binom{n}{k_1,k_2,\cdots,k_r}$$

*Where the number of distinct elements in $S$ is $r$.*

You'll notice that this is equivalent to the above multiset coefficient, which gives the number of different ways to split a set of $n$ elements into groups of $k_1,k_2,\cdots,k_r$.

#### Partial Multiset permutations
Analogous to normal permutations, a partial multiset permutation of length $k$ is called a **$k$-multiset permutation**. That is, a sequence of length $k$ on a multiset $S$ where no element $s_i$ appears more times that its multiplicity $k_i$:

$$\sigma:k\to S,\,\,\,\,\big|\{i\in k\mid\sigma(i)=s_i\}\big|\le k_i$$

To my knowledge, however, it does not have a concise formula like the others.