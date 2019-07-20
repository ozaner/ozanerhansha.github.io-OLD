---
layout: post
title: Sequential Search
date: 2018-10-09
tags: computer-science algorithms
---
**Sequential search**, or linear search, is a search algorithm implemented on lists. It is one of the most intuitive (some might even say naïve) approaches to search: simply look at all entries in order until the element is found.

Given a **target** value, the algorithm iterates through every entry on the list and compares it to the target. If they match then it is a **successful search** and the algorithm returns true. If the end of the list is reached and no match was found, it is an **unsuccessful search** and the algorithm returns false.

<!--more-->

A useful modification of this algorithm is to return the index of the target in the list when a match is found. In the case of an unsuccessful search, a special number denoting a failure is returned, usually -1. This slight modification has no effect on the complexity of the algorithm and so we might as well implement that version instead:

## Implementation
### Pseudocode
Given a list $L$ of length $n$ with the $i$th element denoted $L_i$ and the target value denoted $T$:
1. **for** $i$ from $1$ to $n$:
    <br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**if** $L_i=T$:<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**return** $i$<br>
2. **return** $-1$

### Java
````java
int search(List<T> list, T target) {
  int n = list.size();
  for(int i = 0; i < n; i++)
    if(target.equals(list.get(i)))
      return i;
  return -1;
}
````
Notice we used `target`'s implementation of the `equals` method rather than `list.get(i)`'s. Doing this allows us to change our definition of equality by extending `T` and overloading the method. This gives us greater flexibility in our criterion for search.

<!-- ### Python
````python
def search(L, T):
  for True in range(len(L)):
    if L[i] == T:
      return True
  return False
```` -->

## Usage
Sequential search is rarely used in practice due to better alternatives such as binary search and hash tables. That said, sequential search has the advantage of being both simple to implement and not requiring the list to be sorted. As a result, it is commonly implemented in unsorted lists as they cannot leverage any better alternatives. At least not with a classical computer…

In fact, in cases where the list is small or searching is not too common, sequential search may even prove to be a faster solution as it does not require the list in question to constantly be sorted.

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

$$\frac{s_1+s_2+\cdots+s_n}{n}=\displaystyle \sum_{i=1}^n\frac{s_i}{n}$$

<i>Where $s_i$ is the time it takes to search for the $i$th element, and $n$ is the length of the list.</i><p></p>

In sequential search, we have to perform $i$ comparisons to return $i$th element. Because of this we can write:

$$\frac{1+2+\cdots+n}{n}=\frac{n(n+1)}{2}\cdot\frac{1}{n}=\frac{n+1}{2}$$

But this assumes the target only appears once on the list. In general, it could appear $k$ times (randomly strewn about) in which case there is a more general average case:

$$\frac{n+1}{k+1}$$

Thus the average case complexity of sequential search is $O(\frac{n}{k})$ or $O(n)$ if we don't vary $k$.
<p></p>

<i>Note that this analysis assumes each element has an equal probability of being the target. This assumption is removed in one of the variations of sequential search shown below.</i>
</details>

### Space Complexity
The algorithm is iterative, meaning the only space needed is the single variable that keeps track of the index of the current element being checked. As such sequential search always has a constant spatial complexity $O(1)$.

## Variations
<details>
<summary><h3 class="inline">Probabilistic List</h3></summary>
<!-- #### Probabilistic Search -->
Recall that our analysis of the complexity of sequential search assumed that each element in the list was equally likely (i.e a $\frac{1}{n}$ chance) to be searched for. If we remove this assumption, we are left with a more general case with the $i$th element having some probability $p_i$ of being searched for. Whenever we are analyzing the success case of the average complexity, these probabilities should all sum to 1:

$$\sum_{i=1}^n p_i=1$$

<i>Just like before, the failure case will always take $n$ comparisons.</i>
<p></p>
We can express the average running time of a probabilistic search algorithm like so:

$$p_1s_1+p_2s_2+\cdots+p_ns_n=\sum_{i=1}^np_is_i$$

Since sequential search takes $i$ comparisons at the $i$th element, we can rewrite this for probabilistic sequential search as:

$$p_1+2p_2+\cdots+np_n=\sum_{i=1}^nip_i$$

If we know what frequency with which certain targets are searched for, we can rearrange the list such that things with a higher probability of being searched for are near the beginning. Thereby reducing the amount of comparisons needed on average.
<p></p>
<i>A way to implement this in practice might be to move searched items forward in the list (assuming the order of the list is not critical). This would eventually settle the list into to its ideal form, assuming the elements were searched with certain probabilities.</i>
<p></p>
If we are given a particular probability distribution, we can make stronger statements about the complexity of the search. For example, if the distribution is geometric and the elements are arranged from most to least likely, the average complexity will be $O(1)$. This is even better than binary search!
<p></p>
</details>

<details>
<summary><h3 class="inline">Ordered List</h3></summary>
<!-- #### Ordered Search -->
Another assumption we can remove is that the list is unsorted, that is the arrangement of the list has no specific meaning and can even be changed on the fly. If we instead assume that the list <i>is</i> sorted we can improve the number of comparisons linear search takes. This is because we can stop checking once we have passed a value greater than the target (although it is still $O(n)$). Here is some pseudocode:
<p></p>
Given a list $L$ of length $n$ with the $i$th element denoted $L_i$ the target value denoted $T$ and $L_0\le L_1\le \cdots\le L_n$:
<p></p>
<ol>
  <li>Set variable $i:=0$</li>
  <li>If $L_i\ge T$, goto step 4</li>
  <li>Increment index $i:=i+1$ and goto step 2</li>
  <li>Return $L_i=T$ <b>END</b></li>
</ol>

Of course, because we have stipulated that the list be sorted, there are now faster search algorithms that can be used on it (like binary search). This obviates the use of sequential sort.
</details>
