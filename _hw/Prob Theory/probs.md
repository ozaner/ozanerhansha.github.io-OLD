## Chapter 2 Examples
#### Example 5h, a
Probability that 1 player get all 13 spades:

$$\begin{align*}
\frac{\overbrace{4\binom{13}{13}}^{4 \text{ hands}}\overbrace{\binom{39}{13}\binom{26}{13}\binom{13}{13}}^{\text{other hands}}}{\binom{52}{13,13,13,13}}=\frac{4\binom{39}{13}\binom{26}{13}}{\binom{52}{13}\binom{39}{13}\binom{26}{13}}=\frac{4}{\binom{52}{13}}
\end{align*}=6.3\cdot 10^{-12}$$

#### Example 5h, b
Probability that each of 4 players gets a spade:

$$\begin{align*}
P(E)&=\frac{\overbrace{4}^{4\text{ spades}}\binom{48}{12}3\binom{36}{12} 2\binom{24}{12}1\binom{12}{12}}{\binom{52}{13}\binom{39}{13}\binom{26}{13}\binom{13}{13}}=\frac{4!\binom{48}{12,12,12,12}}{\binom{52}{13,13,13,13}}\\
&=\frac{4!\frac{48!}{12!12!12!12!}}{\frac{52!}{13!13!13!13!}}=\frac{4!(13!)^448!}{(12!)^452!}=\frac{13^44!}{52\cdot 51\cdot 50\cdot 49}=.1055
\end{align*}$$

<!-- #### Prob 2
Probability person A's hand has at least 1 card form each suit. We'll compute the complement of this first:

$$\begin{align*}
\frac{4\overbrace{\binom{52-13}{13}}^{\text{missing cases}}-\overbrace{\binom{4}{2}\binom{52-26}{13}}^{\text{overcounting}}}{\binom{52}{13}}
\end{align*}$$ -->

## Chapter 2 Problems
#### Problem 1
When sample space for the first half of the experiment is the same as the second, i.e. replacement is in effect:

$$\Omega=\{r,g,b\}^2$$

Without replacement the sample space looks like:

$$\Omega=\{(r,g),(r,b),(g,r),(g,b),(b,r),(b,g)\}$$


#### Extra
Probability of that we have at least 1 card from each suit from drawing 13 cards.


Probability of choosing 4 cards, and having more than 1 from each suit:

$$\frac{13\cdot13\cdot13\cdot13}{\binom{52}{4}}$$

Probability of choosing 5 cards, and having more than 1 from each suit, now one suit of 4 will have 2 cards:

$$\frac{4\binom{13}{2}\cdot13\cdot13\cdot13}{\binom{52}{5}}$$

Probability of choosing 6 cards, and having more than 1 from each suit, now we could have suits numbering $3,1,1,1$ or $2,2,1,1$:

$$\text{case 2}=\frac{\binom{4}{2}\binom{13}{2}\binom{13}{2}\cdot13\cdot13}{\binom{52}{6}}$$


#### HW Prob
choose 26 cards from 52, whats the prob you get at least 2 cards form each suit.
