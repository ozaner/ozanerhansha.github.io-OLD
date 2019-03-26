---
layout: post
title: Sequences
date: 2019-03-30
tags: math set-theory
---
Sequences are ordered lists of elements. These are realized as functions from an ordinal number to some set. The term *sequence* on its own usually refers to a sequence whose domain is the natural numbers. A *finite sequence* is one whose domain is an element of the natural numbers, and a *transfinite sequence* is one whose domain is an ordinal number larger than $\omega$.

Sequences are used to formalize ideas like infinite series, complete metric spaces, strings, transfinite induction, etc.

## Definition
An $X$ sequence $S$ is a function from some ordinal $\alpha\in\text{Ord}$ to $X$:

$$S:\alpha\to X$$

## Bi-infinite Sequences
There is another popular notion of sequence called a **bi-infinite sequence** that ranges over all integers rather than just nonnegative ones. Such sequences are usually denoted like so:

$$S=(s_n)_ {n=-\infty}^\infty=(\cdots, s_{-2},s_{-1},s_0,s_1,s_2,\cdots)$$

#### $n$-infinite Sequences
Notice that we can generalize bi-infinite sequences, which are just sequences of order $\omega\cdot2$, to **$n$-infinite sequences** which are
sequences of order $\omega\cdot n$ for some $n\in\mathbb N$.
