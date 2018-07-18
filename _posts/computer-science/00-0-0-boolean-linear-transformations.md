---
layout: post
title: Boolean Logic as Linear Transformations
date: 2018-07-18
tags: computer-science math
---
## Introduction
Computation is usually formulated via boolean logic, which in turn makes use of logical connectives like $\wedge,\vee, \neg$ along with the binary digits $0$ and $1$, representing false and true respectively.

There is, however, an alternative: linear algebra. By representing $0$ and $1$ as vectors and logical operations/gates as transformations on those vectors, we can define computation in the language of linear algebra.

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

*Notice my use of bra-ket notation above. This is the standard notation used in quantum mechanics, and thus quantum computing. As such, I used it here for consistency as well as to denote the difference between the state $\|0\rangle$ and the number $0$.*

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
<summary><h4 class="inline">Identity</h4></summary>
The identity gate takes an input and returns it as is (i.e $f(x)=x$). To represent it we simply use the $2 \times 2$ identity matrix:

$$
  I_2 = \begin{pmatrix}
    1 & 0 \\
    0 & 1
  \end{pmatrix}
$$

And indeed, if we apply the gate to both $\|0\rangle$ and $\|1\rangle$ we find:

$$I_2|0\rangle=|0\rangle$$

$$I_2|1\rangle=|1\rangle$$
</details><p></p>

<!-- #### Negation -->
<details>
<summary><h4 class="inline">Negation (NOT)</h4></summary>
The negation gate takes an input and flips it (i.e $f(x)=\neg x$). We can represent it with the following matrix:

$$
  X = \begin{pmatrix}
    0 & 1 \\
    1 & 0
  \end{pmatrix}
$$

Applying the gate to both $\|0\rangle$ and $\|1\rangle$ we find:

$$X|0\rangle=|1\rangle$$

$$X|1\rangle=|0\rangle$$
</details><p></p>

<!-- #### Constant 0 -->
<details>
<summary><h4 class="inline">Constant 0</h4></summary>
Outputs $0$ regardless of input (i.e $f(x)=0$). We can represent it with the following matrix:

$$
  C_0 = \begin{pmatrix}
    1 & 1 \\
    0 & 0
  \end{pmatrix}
$$

Applying the gate to both $\|0\rangle$ and $\|1\rangle$ we find:

$$C_0|0\rangle=|0\rangle$$

$$C_0|1\rangle=|0\rangle$$
</details><p></p>

<!-- #### Constant 1 -->
<details>
<summary><h4 class="inline">Constant 1</h4></summary>
Outputs $1$ regardless of input (i.e $f(x)=1$). We can represent it with the following matrix:

$$
  C_1 = \begin{pmatrix}
    0 & 0 \\
    1 & 1
  \end{pmatrix}
$$

Applying the gate to both $\|0\rangle$ and $\|1\rangle$ we find:

$$C_1|0\rangle=|1\rangle$$

$$C_1|1\rangle=|1\rangle$$
</details><p></p>

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

*As a side note, the tensor product of two rank $2$ tensors (vectors) $a$ and $b$ is equivalent to $ab^\top$.*

## Binary Gates
Now that we can represent bit strings as vectors, it is possible construct operations that take in $2$ bits and output $1$ bit. While there are technically $2^{2^2}=16$ possible binary bit operations, we'll only construct the more useful ones like `AND`, `OR`, `XOR`, etc.

You'll notice that the $i$th column of a binary gate matrix is either the $\|0\rangle$ or $\|1\rangle$ vector depending on what the gate outputs given the binary form of $i$ (so the $2$nd index corresponds to the input $10_2$). Since these gates only have $2^2=4$ possible inputs, there are $4$ corresponding columns in their matrix representation.

<details>
<summary><h4 class="inline">OR</h4></summary>
The <code>OR</code> gate represents logical disjunction (i.e $f(x,y)=x\vee y$) and is represented by the following matrix:

$$
  \text{OR} = \begin{pmatrix}
    1 & 0 & 0 & 0 \\
    0 & 1 & 1 & 1
  \end{pmatrix}
$$

Applying the gate to all two bit states we find:

$$\text{OR}|00\rangle=|0\rangle$$

$$\text{OR}|01\rangle=|1\rangle$$

$$\text{OR}|10\rangle=|1\rangle$$

$$\text{OR}|11\rangle=|1\rangle$$
</details><p></p>


<details>
<summary><h4 class="inline">AND</h4></summary>
The <code>AND</code> gate represents logical conjunction (i.e $f(x,y)=x\wedge y$) and is represented by the following matrix:

$$
  \text{AND} = \begin{pmatrix}
    1 & 1 & 1 & 0 \\
    0 & 0 & 0 & 1
  \end{pmatrix}
$$

Applying the gate to all two bit states we find:

$$\text{AND}|00\rangle=|0\rangle$$

$$\text{AND}|01\rangle=|0\rangle$$

$$\text{AND}|10\rangle=|0\rangle$$

$$\text{AND}|11\rangle=|1\rangle$$
</details><p></p>


<details>
<summary><h4 class="inline">XOR</h4></summary>
The <code>XOR</code> gate represents exclusive disjunction (i.e $f(x,y)=x\oplus y$) and is represented by the following matrix:

$$
  \text{XOR} = \begin{pmatrix}
    1 & 0 & 0 & 1 \\
    0 & 1 & 1 & 0
  \end{pmatrix}
$$

Applying the gate to all two bit states we find:

$$\text{XOR}|00\rangle=|0\rangle$$

$$\text{XOR}|01\rangle=|1\rangle$$

$$\text{XOR}|10\rangle=|1\rangle$$

$$\text{XOR}|11\rangle=|0\rangle$$
</details><p></p>


<details>
<summary><h4 class="inline">Equality (XNOR)</h4></summary>
Equality checks if two bits are equivalent (i.e $f(x,y)=x\iff y$) and is represented by the following matrix:

$$
  \text{IFF} = \begin{pmatrix}
    1 & 1 & 1 & 0 \\
    0 & 0 & 0 & 1
  \end{pmatrix}
$$

<i>Notice that equality is equivalent to the negation of XOR, <code>XNOR</code> (i.e $x\leftrightarrow y=\neg(x\oplus y)$) meaning all the $0$'s and $1$'s in the <code>XOR</code> matrix are simply swapped to form the equality one.</i><p></p>

Applying the gate to all two bit states we find:

$$\text{IFF}|00\rangle=|1\rangle$$

$$\text{IFF}|01\rangle=|0\rangle$$

$$\text{IFF}|10\rangle=|0\rangle$$

$$\text{IFF}|11\rangle=|1\rangle$$
</details><p></p>


<details>
<summary><h4 class="inline">Implication (IF)</h4></summary>
Material implication is a statement of one variable's dependence on another (i.e $f(x,y)=x\implies y$). It's more commonly referred to as an <code>IF</code> statement in computer science.

$$
  \text{IF} = \begin{pmatrix}
    0 & 1 & 0 & 0 \\
    1 & 0 & 1 & 1
  \end{pmatrix}
$$

Applying the gate to all two bit states we find:

$$\text{IF}|00\rangle=|1\rangle$$

$$\text{IF}|01\rangle=|0\rangle$$

$$\text{IF}|10\rangle=|1\rangle$$

$$\text{IF}|11\rangle=|1\rangle$$
</details><p></p>

## Putting it Together
We can now appreciate this new formulation of binary computation for what it is, an isomorphism from booleans to vectors, logical connectives to matrices, and function composition to matrix multiplication.

Here's an example, the half-adder:

![half-adder](/assets/comp_sci/half_adder.png?style=centerme)

We can represent this algebraically as $S=X\oplus Y$ and $C=X\wedge Y$, where $S$ is the *sum* bit and $C$ is the *carry* bit.

Remember, however, that a bit string is represented as the tensor product of its component bits. As such, we must find the tensor product of the matrices represented by the logical operations:

$$
  S=\text{XOR}(A\otimes B)
$$

$$
  C=\text{AND}(A\otimes B)
$$

<!-- <details>
<summary>Explicit Form</summary>

$$
S=\begin{pmatrix}
  1 & 0 & 0 & 1 \\
  0 & 1 & 1 & 0
\end{pmatrix}
\left(
\begin{pmatrix}
  a \\
  b \\
\end{pmatrix}
\otimes
\begin{pmatrix}
  c \\
  d \\
\end{pmatrix}
\right)
$$

$$
  C = \begin{pmatrix}
    1 & 1 & 1 & 0 \\
    0 & 0 & 0 & 1
  \end{pmatrix}
  \left(
  \begin{pmatrix}
    a \\
    b \\
  \end{pmatrix}
  \otimes
  \begin{pmatrix}
    c \\
    d \\
  \end{pmatrix}
  \right)
$$

</details><p></p> -->


<details>
<summary>"Proof"</summary>

<a href="../html-link.htm"><img src="/assets/comp_sci/half_adder_proof.jpg" style="centerme" title="White flower" alt="half adder proof"></a>

</details><p></p>

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
</details><p></p>
