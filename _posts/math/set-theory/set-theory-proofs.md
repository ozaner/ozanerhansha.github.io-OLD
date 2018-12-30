---
layout: post
title: Miscellaneous Set Theory Proofs
date: 2018-09-18
tags: math set-theory
---
A collection of set theory proofs too specific to include in any other page.

<!-- These could be made more rigorous, that is only referring to the axioms, but that is needless given the purpose of these proofs. -->

<!--more-->

<p></p>
<details>
<summary><h3 class="inline">Nonequality of Unions or Intersections</h3></summary>

If two sets are not equal, then either those sets *unioned* with another set are not equal or those sets *intersected* with another set are not equal. Formally this means that: $\forall A,B,C$:

$$A\not=B\rightarrow\left(A\cup C\not=B\cup C\right)\vee\left(A\cap C\not=B\cap C\right)$$

*We'll call this proposition $P$ for convenience.*

Notice that, by definition, $A$ being distinct from $B$ means that there exists at least one element $x$ that is in one of the sets and not in the other. Thus, without loss of generality (because $\not=$ is symmetric), we will say:

$$A\not=B\rightarrow \left(\exists a\right)a\in A \wedge a\not\in B$$

Now notice that, from the law of the excluded middle, that $a$ is either in or not in $C\text{:}$

$$\begin{align}
&a\in C\vee\neg\left(a\in C\right)\\
\equiv\ &a\in C\vee a\not\in C\\
\end{align}$$

Now we can split the proof into two cases, one where $a\in C$ and one where $a\not\in C$:
<p></p>

<details><summary><b>First case: $a\in C$</b></summary>
The definition of the intersection of two sets is the set whose elements are in both sets. More formally $A\cap C$ is defined as:

$$A\cap C=\{x\mid x\in A\wedge x\in C\}$$

Notice that because $a\in A$ and, in this case, $a\in C$ it must be in $A\cap C$ because it satisfies the condition to be in it:

$$a\in A \wedge a\in C\rightarrow a\in A\cap C$$

Conversely, notice that because $a\not\in B$, it does not satisfy the condition to be in $B\cap C$:

$$B\cap C=\{x\mid x\in B\wedge x\in C\}$$

And so:

$$\neg(a\in B\wedge a\in C)\rightarrow a\not\in B\cap C$$

And because there exists an element that is in one set $A\cap C$ but not in the other $B\cap C$, then they must not be equal:

$$(a\in A\cap C)\wedge(a\not\in B\cap C)\rightarrow A\cap C\not= B\cap C$$

As a result we have proved the proposition $P$ is true assuming $a\in C$:

$$a\in C\rightarrow P$$
</details>

<details><summary><b>Second case: $a\not\in C$</b></summary>
Similar to the above case, we are going to show that $a\not\in C$ implies that the $A\cup C$ and $B\cup C$ cannot be equal. To start we'll define $A\cup C$ which is just the set of all elements in both $A$ and $C$:

$$A\cup C=\{x\mid x\in A\vee x\in C\}$$

Notice that because $a\in A$ that it is also in $A\cup B$:

$$a\in A\rightarrow a\in A\cup C$$

Also notice that $a\not\in B\cup C$. This can be made clear by its definition:

$$B\cup C=\{x\mid x\in B\vee x\in C\}$$

Remember that $a\not\in B$ by definition an that, in this case, $a\not\in C$. As such it doesn't satsify the condition to be in $B\cup C$:

$$(a\not\in B)\wedge(a\not\in C)\rightarrow a\not\in B\cup C$$

And because there exists a set $a$ that is in $A\cup C$ but not in $B\cup C$, they cannot be equal:

$$(a\in A\cup C)\wedge(a\not\in B\cup C)\rightarrow A\cup C\not= B\cup C$$

As a result we have proved the proposition $P$ is true assuming $a\not\in C$:

$$a\not\in C\rightarrow P$$
</details>
<p></p>

In these two cases we have shown that if $a\in C$ or $a\not\in C$ that the proposition $P$ is true. Since $a$ must be either in $C$ or not, we can say:

$$\begin{align}
a\in C\vee a\not\in C\\
a\in C\rightarrow P\\
a\not\in C\rightarrow P\\
\hline P
\end{align}$$

And we are done. $\square$

</details>
