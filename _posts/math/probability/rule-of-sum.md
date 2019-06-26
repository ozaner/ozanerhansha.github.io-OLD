---
layout: post
title: The Rule of Sum & Product
date: 2019-06-25
tags: math probability-theory set-theory
---

The **rule of sum** and *rule of product*, also referred to as the *basic counting principles*, are fundamental combinatorial principles. They encapsulate two basic intuitions regarding enumeration in terms of set theory.

## The Rule of Sum
Given a set $X$ with $|X|$ elements and a different set $Y$ with $|Y|$ which shares no elements with the first, taken together the sets have $|X|+|Y|$ elements. That is, for two disjoint sets $X,Y$:

$$|X\cup Y|=|X|+|Y|$$

Putting this in terms of probability theory, this means that an event with $x$ outcomes and 

#### $n$ Sets
This can be generalized to any finite collection of sets $\{S_i\}_{i=1}^n$ whose elements are pairwise disjoint (i.e. $i\not= j\rightarrow S_i\cup S_j=\empty$):

$$\left|\bigcup_{i=1}^n S_i\right|=\sum_{i=0}^n|S_i|$$

Thus, the rule of sum is a statement about the cardinality of a pairwise disjoint collection of sets.

#### Example



## Independence of Outcomes