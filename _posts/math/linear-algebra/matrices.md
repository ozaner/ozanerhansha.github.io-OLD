---
layout: post
title: Matrices
date: 2018-09-04
tags: math linear-algebra
---
A matrix is a $2$-dimensional array of elements, usually from a ring or field.

<!--more-->

## Definition
An $m\times n$ matrix $\mathbf A$ over some set $S$ is defined as a function from the [cartesian product](\cartesian-product) of $\mathbb{N}_n$ and $\mathbb{N}_m$ to $S$:

$$\mathbf A:\mathbb{N}_m\times \mathbb{N}_n\to S$$

## notes
- $M^T+N^T=(M+N)^T$ idempotency
- identity matrix krockner delta
- rotation matrix 2x2 (3x3?)
- vector multi, matrix multi
- tensor multi
- generalized def

## Notation
Shown below is the $m\times n$ matrix $\mathbf A$. When a matrix is given *explicitly* it is written in this form with elements in each entry.

$$
\mathbf A = \underbrace{
      \begin{bmatrix}
      a_{11} & a_{12} & \dots & a_{1j} & \dots & a_{1m} \\
      a_{21} & a_{22} & \dots & a_{2j} & \dots & a_{2m} \\
      \vdots & \vdots & \ddots & \vdots & \vdots & \vdots \\
      a_{i1} & a_{i2} & \dots & a_{ij} & \dots & a_{im} \\
      \vdots & \vdots & \vdots & \vdots & \ddots & \vdots &\\
      a_{n1} & a_{n2} & \dots & a_{nj} & \dots & a_{nm}
      \end{bmatrix}}_{m \text{ columns}}

      \left.\vphantom{\begin{bmatrix}
      a_{11} & a_{12} & \dots & a_{1j} & \dots & a_{1m} \\
      a_{21} & a_{22} & \dots & a_{2j} & \dots & a_{2m} \\
      \vdots & \vdots & \ddots & \vdots & \vdots & \vdots \\
      a_{i1} & a_{i2} & \dots & a_{ij} & \dots & a_{im} \\
      \vdots & \vdots & \vdots & \vdots & \ddots & \vdots &\\
      a_{n1} & a_{n2} & \dots & a_{nj} & \dots & a_{nm}
      \end{bmatrix}}\right\}\scriptsize{n\text{ rows}}
$$

*The ellipses denote that an unspecified amount of entries have passed.*

#### Dimensions of a Matrix
A matrix, being a $2$-dimensional array, has $2$ dimensions. The number of columns in the matrix is usually denoted $m$ while the number of rows is denoted $n$. The set of all $m\times n$ matrices on a set $S$ is denoted:

$$S^{m\times n}$$

While $m$ and $n$ are usually finite, there do exist valid notions of infinite dimensional matrices. Such a matrix would be defined as a function whose domain is the cartesian product of one or more indexed infinite sets (not necessarily $\mathbb{N}$). An example of an infinite matrix might be the derivative operator acting on the vector space of infinite polynomials.

#### Entries in a Matrix
When referring to a particular element, or **entry** in a matrix, it is convention to denote it as a lower case letter with the first subscript referring to the column number and the second the row number (ex. the element in column $3$, row $4$ of $\mathbf A$ is $a_{34}$).

When referring to a general element of the matrix $\mathbf A$, it is common to use $i$ and $j$ to refer to the column and row numbers respectively, thus $a_{ij}$. It is common to define matrices as a function of a given $i$ and $j$. For example:

$$x_{ij}=2i+j \implies X=\begin{bmatrix}
3 & 4 & 5\\
5 & 6 & 7
\end{bmatrix}=(x_{ij})$$

Of course, for this method to work, the size of the matrix in question must be defined beforehand. In the case above, $X$ is a $3\times 2$ matrix. Also notice that we can refer to a matrix by putting parenthesis around its generic entry form.

Other notations include:

$$a_{ij}=\mathbf{A}[i,j]=A[i,j]=A_{i,j}$$

## Structure
