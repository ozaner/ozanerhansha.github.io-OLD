---
layout: post
title: Sequential Search
date: 2018-10-09
tags: computer-science algorithms
---
**Sequential search**, or linear search, is a search algorithm usually implemented on lists. It is one of the most intuitive (some might say naïve) approaches to search: simply look at all entries until the element is found.

Given a **target** value, the algorithm iterates through every entry on the list and compares it to the target. If they match then it is a **successful search** and the algorithm returns true. If the end of the list is reached and no match was found, it is an **unsuccessful search** and the algorithm returns false.

<!--more-->

## Implementation
### Pseudocode
Given a list $L$ of length $n$ with the $i$th element denoted $L_i$ and the target value denoted $T$:
1. Set variable $i:=0$
2. If $L_i=T$, return true **END**
3. Increment index $i:=i+1$
4. If $i<n$, goto step 2; Else return false **END**

### Java
````java
boolean search(List<T> list, T target) {
  Iterator<T> items = list.iterator();
  while(items.hasNext())
    if(target.equals(item.next()))
      return true;
  return false;
}
````
Notice we used `target`'s implementation of the `equals` method rather than `item.next()`'s. We do this because we can change how we define equality by extending `T` and overloading the method. This gives us greater flexibility in our criterion for search.

<!-- ### Python
````python
def search(L, T):
  for True in range(len(L)):
    if L[i] == T:
      return True
  return False
```` -->

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

But this assumes the target only appears once on the list. In general, it could appear $k$ times (randomly strewn about) in which case there is a more general average case:

$$\frac{n+1}{k+1}$$

Either way, the average case complexity of sequential search is $O(n)$
<p></p>

<i>Note that this analysis assumes each element has an equal probability of being the target. This assumption is removed in one of the variations of sequential search shown below.</i>
</details>

### Space Complexity
The algorithm is iterative, meaning the only space needed is the single variable that keeps track of the index of the current element being checked. As such sequential search always has a constant spatial complexity $O(1)$.

## Variations
#### Probabilistic Search
Note that if we knew what frequency with which certain targets are searched for, we could rearrange the list such that things more often search are near the beginning. This would reduce the overall running average running time.

*A way to implement this might be to move the most recently searched target to the front of the list, assuming the order of the elements is not crucial.*

In this probabilistic case, the formula for computing the average running time is weighted:

$$p_0s_0+p_1s_1+\cdots+p_ns_n=\sum_{i\in n}p_is_i$$

<i>Where $\sum_{i\in n} p_i=1$. Also notice that in the equal probability case, each $p_i=\frac{1}{n}$.</i><br>

What this probability distribution is will determine the average case complexity of this variation on sequential search.

#### Ordered Search
Another assumption we can remove is that the list is unordered, that is the arrangement of the list has no specific meaning and can even be changed on the fly. If we instead assume that the list *is* ordered we can improve the number of comparisons linear search takes. This is because we can stop checking once we have passed a value greater than the target. Here is some pseudocode:

Given a list $L$ of length $n$ with the $i$th element denoted $L_i$ the target value denoted $T$ and $L_0\le L_1\le \cdots\le L_n$:
1. Set variable $i:=0$
2. If $L_i\ge T$, goto step 4
3. Increment index $i:=i+1$ and goto step 2
4. Return $L_i=T$ **END**

Of course, because we have stipulated that the list be ordered, there are now faster search algorithms that can be used on it, namely binary search. This obviates the use of sequential sort.
