---
layout: post
title: Sequential Search
date: 2018-10-08
tags: computer-science algorithms
---
**Sequential search**, or linear search, is a search algorithm usually implemented on lists. It is one of the most intuitive (some might say naïve) approaches to search: simply look at all entries until the element is found.

Given a **target** value, the algorithm iterates through every entry on the list and compares it to the target. If they match then it is a **successful search** and the algorithm returns true. If the end of the list is reached and no match was found, it is an **unsuccessful search** and the algorithm returns false.

<!--more-->

## Implementation
### Pseudocode
Given a list $L$ of length $n$ with the $i$th element denoted $L_i$ and the target value denoted $T$:
1. Set variable $i:=0$
2. If $L_i=T$, return true. END
3. Increment index $i:=i+1$
4. If $i<n$, goto step 2; Else return false. END

### Python
````python
def search(L, T):
  for True in range(len(L)):
    if L[i] == T:
      return True
  return False
````

## Usage
Sequential search is very rarely used in practice due to better alternatives such as binary search and hash tables. That said, sequential search has the advantage of being both simple to implement and detached from any particular data structure.

As a result, sequential search is commonly implement in data structures such as unordered lists as they cannot leverage any better alternatives.

## Analysis
### Time Complexity
The basic and dominant operation of sequential search (and search algorithms in general) is comparison. Thus we can measure the running time of this algorithm by counting the number of comparisons made by it given a list of size $n$.

<details>
<summary><strong>Best Case</strong><br></summary>
The best case of sequential search is if the first element of the list is the target. In this case it takes only 1 comparison to return the successful search. Thus the best case complexity is $O(1)$.
<p></p></details>

<details>
<summary><strong>Worst Case</strong><br></summary>
The worst case of sequential search is if either the last element was the target or if the target was not even in the list. Both cases would take $n$ comparisons, with $n$ being the size of the list in question. Thus the worst case complexity is $O(n)$.
<p></p></details>

<details>
<summary><strong>Average Case</strong><br></summary>
The average case complexity of a search algorithm is the sum of the times it takes to search for each element divided by the number of elements. More formally:

$$\frac{s_0+s_1+\cdots+s_n}{n}=\frac{\sum_{i\in n}s_i}{n}$$

<i>Where $s_i$ is the time it takes to search for the $i$th element. And $n$ is a <a href="\natural-numbers">natural number</a>.</i><p></p>

In sequential search, we have to perform $i$ comparisons to search for the $(i-1)$th element (the $-1$ is because we index starting at $0$). Because of this we can write:

$$\frac{1+2+\cdots+n}{n}=\frac{n(n+1)}{2}\cdot\frac{1}{n}=\frac{n+1}{2}$$

Thus the average case complexity of sequential search is $O(n)$
<p></p>

<i>Note that this analysis assumes each element has an equal probability of being the target. This assumption is removed in one of the variations of sequential search shown below.</i>
</details>

### Space Complexity
The algorithm is iterative, meaning the only space needed is the single variable that keeps track of the index of the current element being checked. As such sequential search always has a constant spatial complexity $O(1)$.

## Variations
#### Probabilistic Search

#### Ordered Search
