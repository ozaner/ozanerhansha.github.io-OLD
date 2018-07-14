---
layout: post
title: Classical Computation in Linear Algebra
date: 2018-07-14
tags: computer-science math
---
## Introduction
While computation is usually formulated using logical connectives like $\wedge,\vee, \neg$ along with the binary digits $0$ and $1$, there is another way to formulate binary computation: linear algebra. We can represent $0$ and $1$ as vectors and logical gates as transformations on those vectors.

While this may at first seem to only be a novel construction, reformulating computation in terms of linear algebra is precisely what opens the door to quantum computation, which is essentially a more general form of what is shown below.

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

*Notice my use of bra-ket notation above. This is the standard notation used in quantum mechanics, and thus quantum computing. As such I used it here for consistency as well as to denote the difference between the state $\|1\rangle$ and the number $1$.*

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

## Unitary Gates
Since a bit has only $2$ possible input states and $2$ possible output states, there are exactly $2^2=4$ unary logical gates. We can represent them as matrices in the following way:

#### Identity
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

#### Negation
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

#### Constant 0
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

#### Constant 1
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


## Binary Gates
We can now introduce gates that take in

#### CNOT
