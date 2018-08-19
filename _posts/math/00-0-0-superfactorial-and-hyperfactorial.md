---
layout: post
title: Superfactorial and Hyperfactorial
date: 2018-04-18
tags: math
---
## Factorial
The factorial function $n!$ is the product of the first $n$ [natural numbers](/natural-numbers):

$$n!=\prod_{k=1}^{n}k=1\times2\times3\times\cdots\times n$$

*The factorials are sequence [A000142](https://oeis.org/A000142) in the OEIS.*

It's important to note that $0!$ is defined as $1$ because it is an [empty product](https://en.wikipedia.org/wiki/Empty_product). This is not an arbitrary definition and in fact simplifies many formulas involving factorials.

The function is a mapping from the natural numbers to itself:

$$!:\mathbb{N}\rightarrow\mathbb{N}$$

*Using [analytic continuation](https://en.wikipedia.org/wiki/Analytic_continuation), the factorial function can be generalized to complex numbers. The resulting function is dubbed the $\Gamma(z)$ [gamma function](https://en.wikipedia.org/wiki/Gamma_function).*

While there is much to discuss about the factorial function, this post concerns itself with two particular variations of the factorial. Namely the superfactorial and the hyperfactorial.

<!--more-->

## Superfactorial
We denote the superfactorial of $n$ as $n{$}$. It is defined as the product of the first $n$ factorials:

$$n$=\prod_{k=1}^{n}k!=1!\times2!\times3!\times\cdots\times n!$$

*The superfactorials are sequence [A000178](https://oeis.org/A000178) in the OEIS.*

*The above definition of the superfactorial was created by Neil J.A. Sloane and Simon Plouffe (co-authors of the OEIS). Another definition of superfactorials exists: $n{\$}=n!\uparrow\uparrow n!$ where the double arrows denote [tetration](https://en.wikipedia.org/wiki/Tetration).*

And, like the factorial function, it is a map from the naturals onto itself:

$$$:\mathbb{N}\rightarrow\mathbb{N}$$

*Like factorial, the superfactorial function can be generalized to the complex numbers, resulting in $G(z)$ the [Barnes G-function](https://en.wikipedia.org/wiki/Barnes_G-function).*

## Hyperfactorial
The hyperfactorial of $n$ is denoted $H(n)$ and is defined as:

$$H(n)=\prod_{k=1}^{n}k^k=1^1\times2^2\times3^3\times\cdots\times n^n$$

*The hyperfactorials are sequence [A002109](https://oeis.org/A002109) in the OEIS.*

Again, we can consider this function to be a map from the naturals onto itself:

$$H:\mathbb{N}\rightarrow\mathbb{N}$$

*The hyperfactorial too can be generalized to the complex numbers. The resulting function is known as $K(z)$ the [K-function](https://en.wikipedia.org/wiki/K-function).*

## Factorial Identity
It is possible to relate all three of these factorial variants (factorial, superfactorial and hyperfactorial):

$$n{$}\cdot H(n)=n!^{n+1}$$

<details>
<summary><h4 class="inline">Proof</h4></summary>

We can prove the above statement, which we'll call $P(n)$, by induction:

$$P(n)\equiv n{$}\cdot H(n)=n!^{n+1}$$

First we multiply both sides of the equation by $(n+1)!(n+1)^{n+1}$:

$$\begin{align}n{$}\cdot H(n)&=n!^{n+1}\\
(n+1)!(n+1)^{n+1}& \ \ \ \ \ (n+1)!(n+1)^{n+1}
\end{align}$$

Now let's simplify the left hand side first. Notice that $n{\$}\cdot(n+1)!=(n+1){\$}$ and that $H(n)\cdot(n+1)^{n+1}=H(n+1)$. From this the left hand side simply becomes:

$$(n+1){$}\cdot H(n+1)$$

Now let's deal with right hand side. Notice that the expression can be rewritten as:

$$\begin{align}
n!^{n+1} \color{green}{(n+1)!}(n+1)^{n+1}&=n!^{n+1}\color{green}{n!(n+1)}(n+1)^{n+1}\\
&=n!^{n+2}(n+1)^{n+2}\\
&=(n+1)!^{n+2}\\
\end{align}$$

Putting the right and left hand sides back together we can see that we just proved $P(n+1)$:

$$P(n+1)\equiv(n+1){$}\cdot H(n+1)=(n+1)!^{n+2}$$

However $P(n+1)$ was proved under the assumption that $P(n)$ was true. Thus:

$$P(n)\implies P(n+1)$$

But, notice that $P(1)$ is true:

$$\begin{align}
P(1)&\equiv 1{$}\cdot H(1)=(1!)^{1+1}\\
&\equiv1\cdot1=1\\
&\equiv T
\end{align}$$

Because $P(1)$ is true, this means that $P(1+1)=P(2)$ is true. This implies that $P(2+1)=P(3)$ is true and so on and so forth for all integers above $1$. Thus by induction:

$$\begin{align}
&P(n)\implies P(n+1)\\
&P(1)\\
\therefore\ &\hline{\forall n\in \mathbb{N},\ P(n)}\\
\end{align}$$
