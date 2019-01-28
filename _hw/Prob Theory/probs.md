## Chapter 2 Problems
#### Example 5h, a
Probability that 1 player get all 13 spades:

$$\begin{align*}
\frac{\overbrace{4\binom{13}{13}}^{4 \text{ hands}}\overbrace{\binom{39}{13}\binom{26}{13}\binom{13}{13}}^{\text{other hands}}}{\binom{52}{13,13,13,13}}=\frac{4\binom{39}{13}\binom{26}{13}}{\binom{52}{13}\binom{39}{13}\binom{26}{13}}=\frac{4}{\binom{52}{13}}
\end{align*}=6.3\cdot 10^{-12}$$

#### Example 5h, b
Probability that each player gets a spade:

$$\begin{align*}
P(E)&=\frac{\overbrace{4}^{4\text{ spades}}\binom{48}{12}3\binom{36}{12} 2\binom{24}{12}1\binom{12}{12}}{\binom{52}{13}\binom{39}{13}\binom{26}{13}\binom{13}{13}}=\frac{4!\binom{48}{12,12,12,12}}{\binom{52}{13,13,13,13}}\\
&=\frac{4!\frac{48!}{12!12!12!12!}}{\frac{52!}{13!13!13!13!}}=\frac{4!(13!)^448!}{(12!)^452!}=\frac{13^44!}{52\cdot 51\cdot 50\cdot 49}=.1055
\end{align*}$$

<!-- #### Prob 2
Probability person A's hand has at least 1 card form each suit. We'll compute the complement of this first:

$$\begin{align*}
\frac{4\overbrace{\binom{52-13}{13}}^{\text{missing cases}}-\overbrace{\binom{4}{2}\binom{52-26}{13}}^{\text{overcounting}}}{\binom{52}{13}}
\end{align*}$$ -->
