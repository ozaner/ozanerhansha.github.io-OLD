---
layout: post
title: Miscellaneous Probability Problems
date: 2019-02-24
tags: math probability-theory
---
This is a collection of random (ha) exercises I've written up solutions to relating to combinatorics and probability theory. They're all taken from Ross' <i>A First Course in Probability</i>.

<!-- Most of them are taken from Ross' <i>A First Course in Probability<i>. -->

<!--more-->

## Chapter 1 - Combinatorics
<details>
<summary><h4 class="inline">Problem 24</h4></summary>
<b>Question:</b> Expand $(3x^2+y)^5$.
<p></p>
<b>Answer:</b> Let $a=3x^2$ and $b=y$. Now we use the binomial theorem:

$$(a+b)^5=\sum^5_{k=0} \binom{5}{k}a^{5-k}b^k=a^5+5a^4b+10a^3b^2+10a^2b^3+5ab^4+b^5$$

Re-substituting we arrive at:

$$\begin{align*}
(3x^2+y)^5&=(3x^2)^5+5(3x^2)^4y+10(3x^2)^3y^2+10(3x^2)^2y^3+5(3x^2)y^4+y^5\\
&=243x^{10}+405x^8y+270x^6y^2+90x^4y^3+15x^2y^4+y^5
\end{align*}$$
</details>

<details>
<summary><h4 class="inline">Problem 28</h4></summary>
<b>Question:</b> Given $8$ teachers to be divided into $4$ schools, how many divisions are possible? What if each school must receive $2$ teachers?
<p></p>
<b>Answer:</b> First note that the teachers and schools are different, so a school receiving teacher A and B is a different division from them receiving B and C.
<p></p>
With this in mind, in the first case we see that for every teacher there is a choice to be in 1 of 4 schools. Thus, via the <a href="/the-basic-principle-of-counting">principle of counting</a>, we have:

$$\underbrace{\mkern-20mu\overbrace{4}^{4\text{ schools}}\mkern-20mu\cdot4\cdot4\cdot4\cdot4\cdot4\cdot4\cdot4}_{8\text{ teachers}}=4^8=65536\text{ divisions}$$

The above case was for any division (even those in which some schools got no teachers). However in the following case, each school must receive 2 teachers. The number of ways a group of 8 can be split into 4 groups of 2 is given by the following multinomial coefficient:

$$\binom{8}{2,2,2,2}=\frac{8!}{2!2!2!2!}=2520\text{ divisions}$$
</details>

## Chapter 2 - Probability Spaces
<details>
<summary><h4 class="inline">Problem 1</h4></summary>
<b>Question:</b> Consider a box with 1 red, 1 green, and 1 blue marble. Whenever a marble is chosen from the box, it is replaced with a marble of the same color. What sample space $\Omega$ represents picking two marbles from the box? What about when the marble isn't replaced?
<p></p>
<b>Answer:</b> When sample space for picking the first marble is the same as the second, i.e. replacement is in effect:

$$\Omega=\{r,g,b\}^2$$

Without replacement, the sample space looks like:

$$\Omega=\{(r,g),(r,b),(g,r),(g,b),(b,r),(b,g)\}$$

Where the first element of each outcome is the first choice and likewise for the second. Note that this sample space has no <a href="\cartesian-product#cartesian-factorization">cartesian factorization</a>.<p></p>
</details>

<details>
<summary><h4 class="inline">Problem 2</h4></summary>
<b>Question:</b> A die is rolled continually until a 6 appears. Let $E_n$ denote the event that $n$ rolls were needed to end the experiment. What outcomes are in $E_n$? What is the sample space of this experiment? What does $(\bigcup_{n\in\mathbb{N}} E_n)^\complement$ mean?
<p></p>
<b>Answer:</b> First let us define the event $E_n$. That is, the set of all sequences of rolls of length $n$ (each of which must end in a 6):

$$E_n = \{(k_1,k_2,\cdots,k_i,\cdots,k_{n-1},6)\mid k_i\in[1..5]\}$$

The sample space of this experiment is the set of all finite sequences that end with a $6$ (where the experiment ends) <i>as well as</i> the set of all infinite sequences that don't include $6$ (where the experiment goes on forever):

$$\Omega = \underbrace{\left(\bigcup_{n\in\mathbb{N}} E_n\right)}_{\text{finite sequences}}\cup\underbrace{\{(k_1,k_2,\cdots)\mid k_i\in[1..5]\}}_{\text{infinite sequences}}$$

Recall that $\bigcup_{n\in\mathbb{N}} E_n$ is the event that the experiment terminates, i.e. the outcome is of finite length. Thus, its complement $(\bigcup_{n\in\mathbb{N}} E_n)^\complement$ is the event that it does <i>not</i> terminate and is infinite:

$$\left(\bigcup_{n\in\mathbb{N}} E_n\right)^\complement = \underbrace{\{(k_1,k_2,\cdots)\mid k_i\in[1..5]\}}_{\text{infinite sequences}}$$

<i>Its important to note that the infinite sequence outcomes have probability $0$ of occurring because the odds of never landing a $6$ are given by:</i>

 $$\lim_{n\to\infty}\left(\frac{5}{6}\right)^n=0$$
 
<i>I included them because the problem references them but, for practical purposes, they need not be considered.</i><p></p>
</details>

<details>
<summary><h4 class="inline">Problem 3</h4></summary>
<b>Question:</b> Two dice are thrown. Let $E$ be the event that their sum is odd, $F$ that at least one die is a $1$, and $G$ be that their sum is $5$. Give the events $EF$, $E\cup F$, $FG$, $EF^\complement$, and $EFG$.
<p></p>
<b>Answer:</b> $EF$ is the event that the sum of the dice is odd <i>and</i> one of them is a $1$:

$$\begin{align*}
EF&=\{(x,y)\mid x+y \equiv 1 \bmod{2}\wedge (x=1\vee y=1)\}\\
&=\{(1,2),(1,4),(1,6),(6,1),(4,1),(2,1)\}
\end{align*}$$

$E\cup F$ is the event that either the sum is odd <i>or</i> one die is a $1$:

$$E\cup F=\{(x,y)\mid x+y \equiv 1 \bmod{2}\vee (x=1\vee y=1)\}$$

<i>No need to give all these outcomes explicitly.</i>
<p></p>
$FG$ is the event that 1 die is a $1$ <i>and</i> the dice sum to 5. This leaves only two possibilities:

$$FG=\{(1,4),(4,1)\}$$

$EF^\complement$ is the event that the sum is odd and that <i>no</i> die is a $1$:

$$EF=\{(x,y)\mid x+y \equiv 1 \bmod{2}\wedge (x\not=1\wedge y\not=1)\}$$
<i>Again, no need to give all these outcomes explicitly.</i>
<p></p>
And finally, $EFG$ is the event that the sum is odd, there is at least one $1$, <i>and</i> that the sum is $5$. This leaves only two possibilities and is the same as $FG$:

$$EFG=\{(1,4),(4,1)\}$$
</details>

<details>
<summary><h4 class="inline">Problem 4</h4></summary>
<b>Question:</b> Players A, B, and C take turns flipping a coin. The first to get heads wins. The sample space of this experiment is given by the following bit strings:

$$\Omega = \{1,01,001,0001,\cdots,0000\dots\}$$

Interpret the sample space, and define the following events in terms of $\Omega$: Player A wins is event $A$, player B wins is $B$, and $(A\cup B)^\complement$
<p></p>
<b>Answer:</b> The first group of outcomes listed in the sample space each represent which round the game was won by a $1$. Whoever was flipping that round is round-robin assigned to each bit (A is first, B is second, C is third, A is fourth, etc.). The last element listed is the outcome where the game never ends, i.e. an infinite string of $0$'s.
<p></p>
Event $A$ is the set of all outcomes whose length modulo $3$ is $1$, because A takes the first flip. Likewise, event $B$ is the set of all outcomes whose length modulo $3$ is $2$:

$$\begin{align*}
A &= \{1,0001,0000001,0000000001,\cdots\}\\
B &= \{01,00001,00000001,00000000001,\cdots\}
\end{align*}$$ 

And finally, recall that $(A\cup B)^\complement = A^\complement B^\complement$. As such, this is the event that neither A nor B win. Thus, this event contains all outcomes where C wins (i.e. sequences whose length modulo $3$ equals $0$) or the never ending outcome where nobody wins:

$$(A\cup B)^\complement =\{001,000001,000000001,\cdots,0000\dots\}$$

<i>As a side note, the never ending outcome has a $0$ probability of occurring because:</i>

$$\lim_{n\to\infty}\left(\frac{1}{2}\right)^n=0$$
</details>

<details>
<summary><h4 class="inline">Problem 5</h4></summary>
<b>Question:</b> A system has 5 components, each of which is either working or failed. The sample space of observing the status of the system is thus a $5$-tuple where the $i$th element is a $0$ if failed and a $1$ if working. How many outcomes are in the sample space? If the system works when components 1 and 2 are working or when 3 and 4 are working or when 1, 3, and 5 are working, then what is the event $W$ that the system is working? How many outcomes are in the event $A$ that components 4 and 5 have failed? Write out all outcomes of $AW$.
<p></p>
<b>Answer:</b> The sample space is the set of all bit strings (sequences of 0's and 1's) of length 5. And so its size is given by:

$$|\Omega| =|\{0,1\}^5|=2^5=32$$

The system is working when at least 1 of the 3 conditions mentioned are satisfied:

$$\begin{align*}
W=\{(x_1,x_2,x_3,x_4,x_5)\,\mid\, &(x_1=x_2=1)\,\vee\\
&(x_3=x_4=1)\,\vee\\
&(x_1=x_3=x_5=1)\}
\end{align*}$$

The event $A$ is just when 4 and 5 are 0. Only 3 components are free with 2 possible states each, meaning the number of outcomes is:

$$|A|=\left|\{(x_1,x_2,x_3,x_4,x_5)\mid x_4=x_5=0\}\right|=2^3=8$$

Event $AW$ is when the system is working, despite 4 and 5 not working. This only leaves two possibilities (because 3 working is irrelevant):

$$AW=\{(1,1,0,0,0),(1,1,1,0,0)\}$$
</details>

<details>
<summary><h4 class="inline">Problem 8</h4></summary>
<b>Question:</b> $A$ and $B$ are mutually exclusive events with $P(A)=.3$, and $P(B)=.5$. What is the probability of $A\cup B$, $AB^\complement$, and $AB$
<p></p>
<b>Answer:</b> Because they are mutually exclusive $AB=\emptyset$, and thus:

$$P(A\cup B) = P(A) + P(B) - P(AB) = 0.3+0.5+0=0.8$$

Note that because they are mutually exclusive, the probability that $B$ does not occur given $A$ has occurred is 1, giving us:

$$P(AB^\complement)=P(B^\complement|A)P(A)=1\cdot 0.3=0.3$$

And finally, recall that $AB=\emptyset$ and thus:

$$P(AB)=P(\emptyset)=0$$
</details>

<details>
<summary><h4 class="inline">Problem 11</h4></summary>
<b>Question:</b> A total of 28% of American males smoke cigarettes, 7% smoke cigars, and 5% smoke both. What percentage of males smoke neither? What percentage smokes cigars but not cigarettes?
<p></p>
<b>Answer:</b> First we will define $A$ to be someone smokes cigarettes and $B$ to be that they smoke cigars. The event that someone smokes neither is given by:

$$\begin{align*}
P((A\cup B)^\complement)&=1-P(A\cup B)\\
&=1-(P(A)+P(B)-P(AB))\\
&=1-(.28+.07-.05)=.7
\end{align*}$$

The event that someone smokes cigars but not cigarettes, i.e. $BA^\complement$, can be calculated using the law of total probability:

$$\begin{align*}
P(B)&=P(BA)+P(BA^\complement)\\
.07&=.05+P(BA^\complement)\\
&\rightarrow P(BA^\complement)=.02
\end{align*}$$
</details>

## Chapter 3 - Conditional Probability

<details>
<summary><h4 class="inline">Exercise 1</h4></summary>
<b>Question:</b> Two dice are rolled. What is the probability that at least one lands on $6$ given that the dice landed on different numbers? 
<p></p>
<b>Answer:</b> let $E$ represent the event that one die lands on a $6$ and $F$ that the rolls are different. The conditional probability of $E$ occurring given $F$ is:

$$P(E|F)=\frac{P(EF)}{P(F)}$$

To compute the necessary probabilities we first note that this experiment is given by a discrete uniform distribution. As a result, the probability of an event occurring is simply its cardinality over the cardinality of the sample space. So first we compute the cardinalities of each event.
<p></p>
For the sample space $\Omega$, we have two dice each with $6$ independent outcomes, and so <a href="/the-basic-principle-of-counting">the basic principle of counting</a> tells us its size:

$$|\Omega|=6\cdot6=36$$

The number of outcomes in $E$ is given by all the rolls where the first die is a $6$ and the second isn't, where the second die is a $6$ and the first isn't, and where they are both $6$:

$$|E|=5+5+1=11$$

For $F$, there are 6 choices of the first die and only 5 valid choices for the second die (i.e. no repeats) and so, via the basic principle of counting, the number of outcomes is given by:

$$|F|=6\cdot5=30$$

Note that the outcomes in $E$ are all contained in $F$ except the outcome that both rolls are a $6$. As such, the size of $EF$ is given by:

$$|EF|=11-1=10$$

We can now compute the relevant probabilities:

$$P(EF)=\frac{|EF|}{|\Omega|}=\frac{10}{36}\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,P(F)=\frac{|F|}{|\Omega|}=\frac{30}{36}$$

Plugging these probabilities into our original formula we finally arrive at:

$$P(E|F)=\frac{P(EF)}{P(F)}=\frac{10/36}{30/36}=\frac{1}{3}$$

<p></p>
</details>
<!-- 
<details open>
<summary><h4 class="inline">Exercise ?</h4></summary>
<b>Question:</b> 
<p></p>
<b>Answer:</b>
<p></p>
</details> -->

<!-- Problem Template
<details>
<summary><h4 class="inline">Problem ?</h4></summary>
<b>Question:</b> 
<p></p>
<b>Answer:</b>
<p></p>
</details>
-->