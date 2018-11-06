---
layout: post
title: Boolean Logic in Linear Algebra
date: 2018-07-18
tags: computer-science math linear-algebra logic
---
## Introduction
Computation is usually formulated via boolean logic, which in turn makes use of logical connectives like $\wedge,\vee, \neg$ along with the binary digits $0$ and $1$, representing false and true respectively.

There is, however, an alternative: linear algebra. By representing $0$ and $1$ as vectors and logical operations/gates as matrices, we can define computation in the language of linear algebra.

While at first this may seem to be nothing but a novel construction, reformulating computation in terms of linear algebra is precisely what opens the door to quantum computing, which is essentially a more general form of what's shown below.

<!--more-->

## 0 and 1 states
We represent $0$ and $1$ as two orthonormal vectors:

$$
  |0\rangle = \begin{pmatrix}
                  1 \\
                  0 \\
                \end{pmatrix}
$$

$$
  |1\rangle = \begin{pmatrix}
                  0 \\
                  1 \\
                \end{pmatrix}
$$

*Notice my use of bra-ket notation above. This is the standard notation used in quantum mechanics, and thus quantum computing. As such, I'll be using it here for consistency as well as to denote the difference between the state $\|0\rangle$ and the number $0$.*

#### An Example
As an example, let's use the `NOT` operator on the $\|1\rangle$ bit:

$$
  \begin{pmatrix}
    0 & 1 \\
    1 & 0
  \end{pmatrix}
  \begin{pmatrix}
    0 \\
    1 \\
  \end{pmatrix}=
  \begin{pmatrix}
    1 \\
    0 \\
  \end{pmatrix}
$$

or in symbolic notation, where $X$ represents the `NOT` gate:

$$X|1\rangle=|0\rangle$$

## Unary Gates
Since a bit has only $2$ possible input states and $2$ possible output states, there are exactly $2^2=4$ unary bit operations. We can represent them as matrices in the following way:

<!-- #### Identity -->
<details>
<summary><strong>Identity</strong></summary>
The identity gate takes an input and returns it as is (i.e $f(x)=x$). To represent it we simply use the $2 \times 2$ identity matrix:

$$
  I_2 = \begin{pmatrix}
    1 & 0 \\
    0 & 1
  \end{pmatrix}
$$

And indeed, if we apply the gate to both $|0\rangle$ and $|1\rangle$ we find:

$$I_2|0\rangle=|0\rangle$$

$$I_2|1\rangle=|1\rangle$$
</details>

<!-- #### Negation -->
<details>
<summary><strong>Negation (NOT)</strong></summary>
The negation gate takes an input and flips it (i.e $f(x)=\neg x$). We can represent it with the following matrix:

$$
  X = \begin{pmatrix}
    0 & 1 \\
    1 & 0
  \end{pmatrix}
$$

Applying the gate to both $|0\rangle$ and $|1\rangle$ we find:

$$X|0\rangle=|1\rangle$$

$$X|1\rangle=|0\rangle$$
</details>

<!-- #### Constant 0 -->
<details>
<summary><strong>Constant 0</strong></summary>
Outputs $0$ regardless of input (i.e $f(x)=0$). We can represent it with the following matrix:

$$
  C_0 = \begin{pmatrix}
    1 & 1 \\
    0 & 0
  \end{pmatrix}
$$

Applying the gate to both $|0\rangle$ and $|1\rangle$ we find:

$$C_0|0\rangle=|0\rangle$$

$$C_0|1\rangle=|0\rangle$$
</details>

<!-- #### Constant 1 -->
<details>
<summary><strong>Constant 1</strong></summary>
Outputs $1$ regardless of input (i.e $f(x)=1$). We can represent it with the following matrix:

$$
  C_1 = \begin{pmatrix}
    0 & 0 \\
    1 & 1
  \end{pmatrix}
$$

Applying the gate to both $|0\rangle$ and $|1\rangle$ we find:

$$C_1|0\rangle=|1\rangle$$

$$C_1|1\rangle=|1\rangle$$
</details>

## Multiple Bits
Before we can introduce the matrices that correspond to binary operations, we need a way of representing multiple bits as a single vector. This is achieved via the **tensor product** of the $|0\rangle$ and $|1\rangle$ vectors. For example, the two bit state $|10\rangle$ can be constructed as follows:

$$
  \begin{pmatrix}
    0 \\
    1 \\
  \end{pmatrix}
  \otimes
  \begin{pmatrix}
    1 \\
    0 \\
  \end{pmatrix}=
  \begin{pmatrix}
    0\begin{pmatrix}
      1 \\
      0 \\
    \end{pmatrix} \\
    1\begin{pmatrix}
      1 \\
      0 \\
    \end{pmatrix} \\
  \end{pmatrix}=
  \begin{pmatrix}
    0 \\
    0 \\
    1 \\
    0 \\
  \end{pmatrix}
$$

It can also be written out symbolically as:

$$|1\rangle\otimes|0\rangle=|10\rangle$$

Notice that $10_2=2$ and that the only $1$ in the $\|10\rangle$ vector is at the $2$nd index (indexing starts at $0$). Indeed, it holds true in general that the vector representation of $n$ bits will be a $2^n$ dimensional vector with $0$'s everywhere except for a $1$ at the $i$th index, where $i$ is the value of the bit string:

$$|a\rangle\otimes|b\rangle\otimes|c\rangle\otimes\cdots=|abc\cdots\rangle$$

<!-- *As a side note, the tensor product of two rank $2$ tensors (vectors) $a$ and $b$ is equivalent to $ab^\top$.* -->

## Binary Gates
Now that we can represent bit strings as vectors, it is possible construct operations that take in $2$ bits and output $1$ bit. While there are technically $2^{2^2}=16$ possible binary bit operations, we'll only construct the more useful ones like `AND`, `OR`, `XOR`, etc.

<details>
<summary><strong>Disjunction ($\operatorname{OR}$)</strong></summary>
The $\operatorname{OR}$ gate represents logical disjunction (i.e $f(x,y)=x\vee y$) and is represented by the following matrix:

$$
  \operatorname{OR} = \begin{pmatrix}
    1 & 0 & 0 & 0 \\
    0 & 1 & 1 & 1
  \end{pmatrix}
$$

Applying the gate to all two bit states we find:

$$\operatorname{OR}|00\rangle=|0\rangle$$

$$\operatorname{OR}|01\rangle=|1\rangle$$

$$\operatorname{OR}|10\rangle=|1\rangle$$

$$\operatorname{OR}|11\rangle=|1\rangle$$
</details>


<details>
<summary><strong>Conjunction ($\operatorname{AND}$)</strong></summary>
The $\operatorname{AND}$ gate represents logical conjunction (i.e $f(x,y)=x\wedge y$) and is represented by the following matrix:

$$
  \operatorname{AND} = \begin{pmatrix}
    1 & 1 & 1 & 0 \\
    0 & 0 & 0 & 1
  \end{pmatrix}
$$

Applying the gate to all two bit states we find:

$$\operatorname{AND}|00\rangle=|0\rangle$$

$$\operatorname{AND}|01\rangle=|0\rangle$$

$$\operatorname{AND}|10\rangle=|0\rangle$$

$$\operatorname{AND}|11\rangle=|1\rangle$$
</details>


<details>
<summary><strong>Exclusive Disjunction ($\operatorname{XOR}$)</strong></summary>
The $\operatorname{XOR}$ gate represents exclusive disjunction (i.e $f(x,y)=x\oplus y$) and is represented by the following matrix:

$$
  \operatorname{XOR} = \begin{pmatrix}
    1 & 0 & 0 & 1 \\
    0 & 1 & 1 & 0
  \end{pmatrix}
$$

Applying the gate to all two bit states we find:

$$\operatorname{XOR}|00\rangle=|0\rangle$$

$$\operatorname{XOR}|01\rangle=|1\rangle$$

$$\operatorname{XOR}|10\rangle=|1\rangle$$

$$\operatorname{XOR}|11\rangle=|0\rangle$$
</details>


<details>
<summary><strong>Logical Equivalence ($\operatorname{IFF}$)</strong></summary>
Logical equivalence/biconditional checks if two bits are equal (i.e $f(x,y)=x\iff y$) and is represented by the following matrix:

$$
  \operatorname{IFF} = \begin{pmatrix}
    1 & 1 & 1 & 0 \\
    0 & 0 & 0 & 1
  \end{pmatrix}
$$

<i>Notice that logical equivalence the negation of <code>XOR</code>, <code>XNOR</code> (i.e $x\leftrightarrow y=\neg(x\oplus y)$) meaning all the $0$'s and $1$'s in the $\operatorname{XOR}$ matrix are simply swapped to form the equality one.</i>

Applying the gate to all two bit states we find:

$$\operatorname{IFF}|00\rangle=|1\rangle$$

$$\operatorname{IFF}|01\rangle=|0\rangle$$

$$\operatorname{IFF}|10\rangle=|0\rangle$$

$$\operatorname{IFF}|11\rangle=|1\rangle$$
</details>


<details>
<summary><strong>Material Implication ($\operatorname{IF}$)</strong></summary>
Material implication is a statement of one variable's dependence on another (i.e $f(x,y)=x\implies y$). It's more commonly referred to as an $\operatorname{IF}$ statement in computer science (however this notion of implication is different from the purely logical one above).

$$
  \operatorname{IF} = \begin{pmatrix}
    0 & 1 & 0 & 0 \\
    1 & 0 & 1 & 1
  \end{pmatrix}
$$

Applying the gate to all two bit states we find:

$$\operatorname{IF}|00\rangle=|1\rangle$$

$$\operatorname{IF}|01\rangle=|0\rangle$$

$$\operatorname{IF}|10\rangle=|1\rangle$$

$$\operatorname{IF}|11\rangle=|1\rangle$$
</details><p></p>

You'll notice that the $i$th column of a binary gate matrix is either the $\|0\rangle$ or $\|1\rangle$ vector depending on what the gate outputs given the binary form of $i$ (ex. the $2$nd index corresponds to the input $10_2$). Since these gates only have $2^2=4$ possible inputs, there are $4$ corresponding columns in their matrix representation.

## Putting it Together
We can now appreciate this new formulation of binary computation for what it is, an isomorphism from Booleans to vectors, logical connectives to matrices, and function composition to matrix multiplication.

Here's an example, the half-adder:

![half-adder](/assets/comp_sci/half_adder.png?style=centerme)

We can represent the outputs of the half-adder symbolically as $S=X\oplus Y$ and $C=X\wedge Y$, where $S$ is the <i>sum</i> bit and $C$ is the <i>carry</i> bit. Below is a proof that derives the matrix representation of the half-adder:

<details>
<summary><strong>Proof</strong></summary>
To find the matrix that corresponds to sending two bits through a half adder, we must compute the tensor product of $X$ and $Y$ then compute and solve a series of tensor products:

$$\begin{align}
\text{Let } X&:=
\begin{pmatrix}
  a\\
  b
\end{pmatrix} \wedge X=|0\rangle \oplus X=|1\rangle\\
\text{Let } Y&:=
\begin{pmatrix}
  c\\
  d
\end{pmatrix} \wedge Y=|0\rangle \oplus Y=|1\rangle
\end{align}$$

Notice that $X$ and $Y$ must be the $0$ or $1$ vectors. This condition is what allows us to solve for the gate. But before we do that let us find the tensor product of $X$ and $Y$ so that we may think of them as a 2 bit input:

$$X\otimes Y=
\begin{pmatrix}
  a\\
  b
\end{pmatrix}\oplus
\begin{pmatrix}
  c\\
  d
\end{pmatrix}=
\begin{pmatrix}
  a\begin{pmatrix}
    c \\
    d \\
  \end{pmatrix} \\
  b\begin{pmatrix}
    c \\
    d \\
  \end{pmatrix} \\
\end{pmatrix}=
\begin{pmatrix}
  ac \\
  ad \\
  bc \\
  bd \\
\end{pmatrix}$$

The output bits $S$ and $C$ can now be represented as the following equations:

$$\begin{align}
S&=\operatorname{XOR}(X\otimes Y)=
\begin{pmatrix}
  1 & 0 & 0 & 1 \\
  0 & 1 & 1 & 0
\end{pmatrix}
\begin{pmatrix}
  ac \\
  ad \\
  bc \\
  bd
\end{pmatrix}=
\begin{pmatrix}
  ac+bd \\
  ad+bc
\end{pmatrix}\\

C&=\operatorname{AND}(X\otimes Y)=
\begin{pmatrix}
  1 & 1 & 1 & 0 \\
  0 & 0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
  ac \\
  ad \\
  bc \\
  bd \\
\end{pmatrix}=
\begin{pmatrix}
  ac+ad+bc \\
  bd
\end{pmatrix}\\
\end{align}$$

Their tensor product, i.e the output of the half-adder given an input of $X\otimes Y$, is the following:

$$\begin{align}
S\otimes C&=
\begin{pmatrix}
  ac+bd \\
  ad+bc
\end{pmatrix}
\begin{pmatrix}
  ac+ad+bc \\
  bd
\end{pmatrix}\\
&=\begin{pmatrix}
  (ac)^2+a^2cd+abc^2+abcd+abd^2+b^2cd \\
  abcd+bd^2\\
  a^2cd+(ad)^2+abcd+abcd+(bc)^2\\
  abd^2+b^2cd
\end{pmatrix}
\end{align}$$

While this result may seem unwieldy, recall the stipulation on the vectors $X$ and $Y$ we made when we defined them: they must be each equal to $|0\rangle$ or $|1\rangle$. We can phrase this in terms of their components:

$$\begin{align}
(a=1\wedge b=0)&\vee(a=0\wedge b=1)\\
(c=1\wedge d=0)&\vee(c=0\wedge d=1)
\end{align}$$

Because of this, we can simplify many of the expressions above (example $ab=0$ b.c either $a$ or $b$ is $0$) to form a more simpler vector:
$$\begin{pmatrix}
  (ac)^2+a^2cd+abc^2+abcd+abd^2+b^2cd \\
  abcd+bd^2\\
  a^2cd+(ad)^2+abcd+abcd+(bc)^2\\
  abd^2+b^2cd
\end{pmatrix}=\begin{pmatrix}
  ac\\
  bd\\
  bc+ad\\
  0
\end{pmatrix}$$
<i>We can also think of this finding non-contingent statements and simplifying them.</i><p></p>

Now we are simply left with the following equation:
$$\operatorname{Half-Adder}(X\otimes Y)=(S\otimes C)$$

We can now solve for the $\operatorname{Half-Adder}$ matrix by explicitly writing out the above equation:

$$
\begin{pmatrix}
  ? &? &? &?\\
  ? &? &? &?\\
  ? &? &? &?\\
  ? &? &? &?
\end{pmatrix}
\begin{pmatrix}
  ac \\
  ad \\
  bc \\
  bd \\
\end{pmatrix}
=\begin{pmatrix}
  ac\\
  bd\\
  bc+ad\\
  0
\end{pmatrix}$$

From the rules of matrix multiplication, it is clear that the sole matrix that solves this equation is:

$$
\begin{pmatrix}
  1 & 0 & 0 & 0 \\
  0 & 0 & 0 & 1 \\
  0 & 1 & 1 & 0 \\
  0 & 0 & 0 & 0
\end{pmatrix}$$

</details>






#### Shortcut
While we could multiply through all the matrices and solve for what the matrix representation of a given boolean circuit is, there is a way to bypass all this. Just like how we constructed the unary and binary logic gates, we can simply construct a **truth table** of what inputs give what outputs. We then construct the matrix from this, setting the $i$th column as the output of the half-adder given the input $i$. Doing this we arrive at the following:

$$\text{Half-Adder}=
\begin{pmatrix}
  1 & 0 & 0 & 0 \\
  0 & 0 & 0 & 1 \\
  0 & 1 & 1 & 0 \\
  0 & 0 & 0 & 0
\end{pmatrix}$$

<details>
<summary><h3 class="inline">CNOT and Quantum Computing</h3></summary>
<!-- ### Sidenote: CNOT -->
As a final example, and lead in into quantum computing, I'll describe a binary gate that outputs two bits rather than one: the controlled NOT or <code>CNOT</code> gate.

Its function is pretty simple: the gate acts as a NOT gate on the second bit, but only if the first bit is $1$. If this first bit, dubbed the <b>control bit</b>, is $0$ then the second bit, dubbed the <b>target bit</b>, won't be affected at all. The first, unchanged, bit and the second, possibly negated, bit are then outputted. Its matrix looks like this:

$$
  \text{CNOT} = \begin{pmatrix}
    1 & 0 & 0 & 0 \\
    0 & 1 & 0 & 0 \\
    0 & 0 & 0 & 1 \\
    0 & 0 & 1 & 0
  \end{pmatrix}
$$

$$\text{CNOT}|00\rangle=|00\rangle$$

$$\text{CNOT}|01\rangle=|01\rangle$$

$$\text{CNOT}|10\rangle=|11\rangle$$

$$\text{CNOT}|11\rangle=|10\rangle$$

While the gate may not seem particularly interesting (and indeed it isn't as far as classical computing is concerned) its real power shows when the control bit is in a superposition of both $|0\rangle$ and $|1\rangle$, ala quantum computing.
</details>
