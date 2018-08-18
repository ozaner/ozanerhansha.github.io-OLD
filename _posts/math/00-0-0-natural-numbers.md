---
layout: post
title: Natural Numbers
date: 2018-05-25
tags: math set-theory
---
## What are Natural Numbers?
The natural numbers are considered the most *natural* set of numbers humans can begin to think of, observe and calculate. They are the numbers we count with $0,1,2,3,4,5,\cdots$

When used to denote the *order* of objects, they are considered **ordinal** numbers. When used to describe the quantity of a set of objects, they are considered **cardinal** numbers. This distinction becomes important when the naturals are extended to include transfinite numbers.

#### Is $0$ an element of $\mathbb{N}$?
Some definitions of the natural numbers don't include $0$ but, all things considered, including it makes defining the naturals as well as expressing a variety formulae easier. As such, whenever I reference the set of naturals it will always contain $0$. The [notation](#notation) for different variations is cleared up below.

<!--more-->

## Definition
The natural numbers are constructed by defining the empty set as zero, then defining the next number, or **successor**, as the set of all previous numbers:

$$\begin{align}
0&\equiv\emptyset\\
1&\equiv\{0\}=\{\emptyset\}\\
2&\equiv\{0,1\}=\{\emptyset,\{\emptyset\}\}\\
3&\equiv\{0,1,2\}=\{\emptyset,\{\emptyset\},\{\emptyset,\{\emptyset\}\}\}\\
&\ \ \vdots\\
n&\equiv\{0,1,2,3,\cdots,n-1\}\\
\end{align}$$

Defining the naturals in this way is consistent with the construction of the [von Neumann ordinals](http://mathworld.wolfram.com/OrdinalNumber.html).

#### Successor Function
This definition of the naturals can be more succinctly written via the successor function $S(n)$ which returns the number that comes after $n$:

$$S(n)=n\cup\{n\}$$

For example, we define the number $1$ to be the successor, or number that comes after, $0$. Since $0=\emptyset$ we can say:

$$\begin{align}
1&\equiv S(0)\\
&=0\cup\{0\}\\
&=\{0\}\\
&=\{\emptyset\}
\end{align}$$

We can keep going with $2\equiv S(1)$, $3\equiv S(2)$ and in general, we can say $n+1\equiv S(n)$ for all natural numbers.

#### Existence in ZFC
While it is possible to construct the successor of every natural number, using the axiom of pairing (to prove the existence of the singleton set) and the axiom of union, we can only prove that any *finite* natural number exists. No matter how many successors we compute, there will always be another.

So how do we prove the existence of the entire infinite set of natural numbers and not just an arbitrarily large, finite subset? Well as it turns out, the only way to do this is to simply declare that such a set exists. This is the **axiom of infinity**:

$$\exists S\left(\emptyset\in S\land\forall x\in S\left(\left(x\cup\{x\}\right)\in S\right)\right)$$

In English, the above statement asserts that there exists a set $S$ that contains the empty set $\emptyset$ as well as the successor (i.e $x\cup\\{x\\}$) to every one of its members. Notice that since we can always take the successor of another number, this set is *necessarily* infinite. Indeed all infinite sets in ZFC originate from this set $S$ which, while we don't know its exact composition, is by definition at least a superset of (if not equal to) the natural numbers: $\mathbb{N}\subseteq S$. Via the axiom of subset, we can thus guarantee the existence of the natural numbers.

## Notation
The set of natural numbers is denoted by the double struck capital letter $\mathbb{N}$. But there are variations on the set that do/don't include $0$ as well as ones that include all natural numbers up to and including $n$:

$$\begin{alignat*}{2}
&\mathbb{N}&&=\{0,1,2,3,4,5,\cdots\}\\
&\mathbb{N}^* &&=\{1,2,3,4,5,\cdots\}\\
&\mathbb{N}_n&&=\{0,1,2,3,4,\cdots,n\}\\
&\mathbb{N}^* _ n&&=\{1,2,3,4,\cdots,n\}\\
\end{alignat*}$$

The last one in particular, the set of all non-zero natural numbers up to $n$, can be written as the integer interval $[1\ldotp\ldotp n]$ to avoid confusion.

## Structure on the Naturals
<details>
<summary><h3 class="inline">Addition</h3></summary>
Using the successor function and two rules, we can <i>inductively</i> define an operation $+$ such that it forms a commutative monoid $(\mathbb{N},+)$ with identity $0$ on the naturals:

$$a+0=0 \tag{1}$$
$$a+S(b)=S(a+b) \tag{2}$$

<details><summary><strong>Example</strong></summary>

$$\begin{align}
2+2&=2+S(1) \tag{def of $2\equiv S(1)$}\\
&=S(2+1) \tag{addition rule #2}\\
&=S(2+S(0)) \tag{def of $1\equiv S(0)$}\\
&=S(S(2+0)) \tag{addition rule #2}\\
&=S(S(2)) \tag{addition rule #1}\\
&=S(3) \tag{def of $3\equiv S(2)$}\\
&=4 \tag{def of $4\equiv S(3)$}\\
\end{align}$$
</details>
<p></p>

This monoid is also <b>cancellative</b>, meaning that an equation is still true even if we add or remove the same number on both sides:

$$a+c=b+c\implies a=b$$

It is from the addition operation $+$ (and successor function $S(n)$) that we can define all the other operations/relations on the naturals.
</details>

<details>
<summary><h3 class="inline">Subtraction</h3></summary>
We can define subtraction in terms of addition as so:

$$a-b=c\iff a=b+c$$

<!-- The set that represents this binary operation would be constructed like this:

$$-\equiv\{(a,b,c)\in\mathbb{N}^3\mid a=b+c\}$$ -->

But note that the difference between two natural numbers $a-b$ exists only if $a\ge b$. As such, subtraction is not defined for any two natural numbers and so is not closed. Moreover, subtraction isn't associative: $(a-b)-c\not=a-(b-c)$.

<h4>Truncated Subtraction</h4>
However, it is possible to define a meaningful notion of subtraction on the naturals. It's called <b>truncated subtraction</b>, denoted $\dot-$, and forms the magma $(\mathbb{N},\dot-)$.

Using the definition of subtraction above, we can define truncated subtraction as:

$$a\ \dot- \ b=
\begin{cases}
    0,& a<b\\
    a-b,& a\ge b
\end{cases}$$

If we want to define it purely in terms of natural arithmetic, we can <i>inductively</i> define $\dot-$ similar to how we defined $+$:

$$a\ \dot- \ 0=a \tag{1}$$
$$0\ \dot- \ a=0 \tag{2}$$
$$S(a)\ \dot- \ S(b)=a\ \dot- \ b \tag{3}$$

<details><summary><strong>Examples</strong></summary>
When $a>b$
$$\begin{align}
5\ \dot- \ 3&=S(4)\ \dot- \ S(2) \tag{def of $5$ & $3$}\\
&=4\ \dot- \ 2 \tag{subtraction rule #3}\\
&=S(3)\ \dot- \ S(1) \tag{def of $4$ & $2$}\\
&=3\ \dot- \ 1 \tag{subtraction rule #3}\\
&=S(2)\ \dot- \ S(0) \tag{def of $3$ & $1$}\\
&=2\ \dot- \ 0 \tag{subtraction rule #3}\\
&=2 \tag{subtraction rule #1}\\
\end{align}$$

When $a<b$
$$\begin{align}
3\ \dot- \ 5&=S(2)\ \dot- \ S(4) \tag{def of $3$ & $5$}\\
&=2\ \dot- \ 4 \tag{subtraction rule #3}\\
&=S(1)\ \dot- \ S(3) \tag{def of $2$ & $4$}\\
&=1\ \dot- \ 3 \tag{subtraction rule #3}\\
&=S(0)\ \dot- \ S(2) \tag{def of $1$ & $3$}\\
&=0\ \dot- \ 2 \tag{subtraction rule #3}\\
&=0 \tag{subtraction rule #2}\\
\end{align}$$
</details>
<p></p>

In conjunction with the commutative monoid on the naturals $(\mathbb{N},+)$, this operator is referred to as a <b>monus</b> and forms a CMM, commutative monoid with monus: $(\mathbb{N},+,\dot-)$.
</details>

<details>
<summary><h3 class="inline">Multiplication</h3></summary>
We can define the multiplication of natural numbers in terms of repeated addition such that it forms a commutative monoid $(\mathbb{N},\times)$:

$$a\times b=c\iff \underbrace{a+a+\cdots+a}_{b\text{ copies}}=c$$

<!-- The set that represents this binary operation would be constructed like this:

$$\times\equiv\{(a,b,c)\in\mathbb{N}^3\mid\underbrace{a+a+\cdots+a}_{b\text{ copies}}=c\}$$ -->

We can also <i>inductively</i> define $\times$ with 2 rules:

$$a\times 0=0 \tag{1}$$
$$a\times S(b)=(a\times b) + a \tag{2}$$

<details><summary><strong>Example</strong></summary>
$$\begin{align}
2\times 3&=2\times S(2) \tag{def of $3\equiv S(2)$}\\
&=(2\times 2)+2 \tag{multiplication rule #2}\\
&=(2\times S(1))+2 \tag{def of $2\equiv S(1)$}\\
&=((2\times 1)+2)+2 \tag{multiplication rule #2}\\
&=((2\times S(0))+2)+2 \tag{def of $1\equiv S(0)$}\\
&=(((2\times 0)+2)+2)+2 \tag{multiplication rule #2}\\
&=((0+2)+2)+2 \tag{multiplication rule #1}\\
&=(2+2)+2\\
&=4+2\\
&=6\\
\end{align}$$
</details>
<p></p>

Like with addition, this monoid is almost <i>cancellative</i>:

$$a\times c=b\times c\implies a=b$$

However it is not fully due to the fact that the above only holds true when $a,b,c\not=0$.

<h4>Commutative Semiring</h4>
Even further, if we combine the $\times$ operator with the monoid  $(\mathbb{N},+)$ and the fact that it is distributive over $+$:

$$a\times(b+c)=(a\times b)+(a\times c)$$

we obtain the commutative semiring $(\mathbb{N},+,\times)$. It is <i>semi</i> because the $+$ operator has no inverse operation, which is necessary for a full ring.
</details>

<details>
<summary><h3 class="inline">Division</h3></summary>
We can define the division of natural numbers in terms of multiplication:

$$a\div b=c\iff a=b\times c$$

<!-- The set that represents this binary operation would be constructed like this:

$$\div\equiv\{(a,b,c)\in\mathbb{N}^3\mid a=b\times c\}$$ -->

However, like subtraction, division isn't defined for all the naturals and so isn't closed (and certainly isn't associative).

<h4>Euclidean Division</h4>
But, like truncated subtraction, it is possible to define a meaningful division operation on the naturals in terms of $+$ and $\times$. This operation is known as <b>Euclidean division</b> (which I'll denote $\div_E$). It divides two natural numbers $a$ and $b$ and returns a <b>quotient</b> $q$ and a <b>remainder</b> $r$:

$$a\div_E b=(q,r)\iff (a=b\times q+r) \land (r<b)$$

For every pair of naturals there is a <i>unique</i> pair of resultants. As such, you can consider $\div_E$ as a function that maps two naturals to two other naturals:

$$\div_E:\mathbb{N}^2\to\mathbb{N}^2$$

<!-- The set that represents this binary operation would be constructed like this:

$$\div_E\equiv\{(a,b,q,r)\in\mathbb{N}^4\mid a=b\times q+r \land r<b\}$$ -->

<!-- We can *inductively* define division with 2 rules: -->
</details>

<details>
<summary><h3 class="inline">Order</h3></summary>
We can define a total order $\le$ on the natural numbers as so:

$$a\le b\iff(\exists c\in\mathbb{N})\ a+c=b$$

<!-- The set that represents this binary relation would be constructed like this:

$$\le\equiv\{(a,b)\in\mathbb{N}^2\mid(\exists c\in\mathbb{N})\ a+c=b\}$$ -->

The naturals along with this binary relation form a totally ordered set $(\mathbb{N},\le)$ that also happens to be well-ordered. Its order type is $\omega$, the first infinite ordinal.

<h4>Ordered Structures</h4>
In conjunction with some of the algebraic structures mentioned above, the $\le$ relation forms an ordered algebraic structure. To be able to be ordered, the structure's operation must preserve order (which is similar to the cancellative property).

For addition we can create the ordered monoid $(\mathbb{N},+,\le)$ because:

$$a\le b\iff (\forall c\in\mathbb{N})\ a+c\le b+c$$

For multiplication, if we remove $0$ from the naturals, we can create the ordered monoid $(\mathbb{N}^* ,\times,\le)$ because:

$$a\le b\iff (\forall c\in\mathbb{N})\ a\times c\le b\times c$$

Combining these two ordered monoids, we can further create the ordered semiring $(\mathbb{N},+,\times,\le)$

Note that we cannot order the monoid $(\mathbb{N},\times)$ and the magma $(\mathbb{N},\dot-)$ because they do not preserve the ordering in all cases:

<details><summary><strong>Proof of $(\mathbb{N},\times)$</strong></summary>
$$\begin{align}
10\le5&\iff \ 10\times 0\le 5\times 0\\
F&\iff \ 0\le 0\\
F&\iff \ T\\
\therefore\ &\hline{a\le b\nLeftrightarrow (\forall c\in\mathbb{N})\ a\times c\le b\times c}\\
\end{align}$$
</details>

<details><summary><strong>Proof of $(\mathbb{N},\dot-)$</strong></summary>
$$\begin{align}
10\le5&\iff \ 10\ \dot-\ 500\le 5\ \dot-\ 500\\
F&\iff \ 0\le 0\\
F&\iff \ T\\
\therefore\ &\hline{a\le b\nLeftrightarrow (\forall c\in\mathbb{N})\ a\ \dot-\ c\le b\ \dot-\ c}\\
\end{align}$$
</details>

<!-- $$a\le b\iff (\forall c\in\mathbb{N})\ a\ \dot-\ c\le b\ \dot-\ c$$

For truncated subtraction we can create the ordered magma $(\mathbb{N},\dot-,\le)$ and the ordered CMM $(\mathbb{N},+,\dot-,\le)$. -->
</details>
