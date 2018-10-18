---
layout: post
title: (Unsorted) List
date: 2018-10-11
tags: computer-science abstract-data-type
---
A list is an abstract data type that generalizes the implementation of a particular data structure. Namely, a sequence of values (of the same type) that may include repeats. This is analogous to the more pure mathematical notion of a finite sequence.

*Note that while the elements must be of the same type, that type could be a generic as object itself.*

Further, a **sorted list** is one whose elements are arranged in ascending (or descending) order. This is only possible if the data type being stored in the list possess some total order. A list that doesn't satisfy this is dubbed an **unsorted list**. The rest of the post will focus on this more general case.

## Core Operations
These are the operations that the list requires to be useful as a data structure. Here I'll discuss what these operations do as well as give their time complexity.

*For all of these operations, we will denote the type of the elements in the list `T` and the actual target value $t$*

Because lists are similar to finite sequences, we also can phrase these operations in terms of mathematical functions. Let $L$ be the pointer to the current list (a finite sequence) and $L_i$ the $i$th element. Also let the size $n$ be the ordered indexing set and a subset of the [naturals](/natural-numbers):

$$L:=(L_i)_ {i\in n}$$

### Append
The append, or add, operation is a *mutator* that takes a target $t$ of type `T` and places it at the end of the list. This operation generally has a constant running time, that is $O(1)$.

Mathematically, this is equivalent to adding a new pair to the mapping from $n$ to the list, increasing its size:

$$\begin{align*}
L:=&\ L\cup\{(n+1, t)\}\\
=&\ (L_i)_ {i\in n+1}
\end{align*}$$

### Contains
The contains operation is an *accessor* that takes a target $t$ of type `T` and returns whether an instance of it exists in the list, in the form of a boolean.

*Whether the element is deemed to be in the list depends on the particular implementation of equality used to compare them.*

With no assumed structure besides being linearly ordered, there's really only one reasonable search algorithm that can be implemented in a generic list: [sequential search](\sequential-search). This gives it a worst/average complexity of $O(n)$.

Mathematically, this is equivalent to the following proposition:

$$\left(\exists i\in n\right)L_i=t$$

### Remove
The remove operation is a *mutator* that takes a target of type `T` and deletes the first instance of it in the list. If there is no such element in the list, an exception may be thrown.

*Again, whether the element is deemed to be equal to that of the one in the list depends on the particular implementation of equality used to compare them.*

Mathematically, this is equivalent to removing the first item in the sequence that is equal to $t$ and shifting everything back:


### Enumerate
The enumerate operation actually consists of two operations, first and next. First sets the **cursor**, or index, to the first element of the list and returns it. Next moves the cursor to the next element in the list and returns it.


## Auxiliary Operations
These are operations that could in theory be implemented by the user via the core operations, but would be useful to have regardless. Just like before I will detail what they are as well as complexity and implementation details.

### Size

### Is Empty

### Remove All

### Clear

## Implementation
There are two primary data structures used to implement generic, unsorted lists: arrays and linked lists. Below we will implement a list in Java with both structures, elaborating when necessary.

*Note that the Java standard library already has an interface (abstract data type) `List<T>`. It also contains implementations of list with both arrays and linked lists in the form of `ArrayList` and `LinkedList` respectively.*

### List
```java
interface List<T> {

}

```

### Array
Note that, due to the fixed length of arrays, append is **amortized** $O(1)$. This is because even though running time is constant in most cases, in some cases (i.e when the array is full) the array has to be remade with more space allocated (usually double) which takes at least $O(n)$ time. Used in this way, arrays are called **dynamic arrays**.

### Linked List

Traversing the entire list to find the last element would take $O(n)$ time. This can be improved, however, by simply storing a pointer to the last node in the list. This allows for appending to take $O(1)$ time.
