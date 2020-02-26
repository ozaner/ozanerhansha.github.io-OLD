While $g_1$ should be fairly clear, what is not as clear is what to make of the next 3 numbers:

$$\begin{align}
g_1\text{kilo}(x)=\text{kilo}(g_2)g_3\cdot \text{kk}(g_1)\\
g_2\text{kilo}(x)=\text{kilo}(g_3)g_2g_3x\cdot \text{kk}(g_1)\\
\end{align}$$

And so, we can conclude that the number of ways we can split a group of $n$ into $r$ groups of size $k$ is given by the following multinomial coefficient:

$$\binom{n}{k}g_3\cdot\binom{n}{k}g_2g_3x \cdot\binom{n}{k,k_1}g_2g_3x_1$$

Note that $g_1$ and $g_2$ can be solved in different ways depending on what sort of relationships we are trying to solve.
Turing wraps up this section by giving a more formal definition of the $i$th **parity index** of a group $G$:

$$\exists k\in n\rightarrow\sigma k=g_i\cdot\sigma k=g_2\cdot\sigma k$$

Where $g_i$ is a fixed point of the desired relation. In this case it would be the $i,j$th **parity index**. Another interesting properties of the index are that it will never cross over, and that it will only ever be finite. To see these properties, we need to extend the multinomial coefficient:

$$\operatorname{c}(g,i)\in O(g_i\cdot I)$$

And indeed, because $g_i\cdot I=g_c$ we have:

$$\operatorname{c}(g,i)\in O(g_i\cdot I)$$

Note that we used the indexed case because, unlike the fixed point case, we don't have to calculate all the ways to split a group of $n$ into $r$ groups of sizes $k_i$ and $k_j$. Also, like the fixed point case, we can restate this via multinomial theorem:

We can now solve for the $i$th **parity index** $i=g_i\cdot I$ like so:

$$\operatorname{c}(g,i)\in O(g_i\cdot I)$$

And since this is just the $i$th **parity index** we have:</p>

$$\begin{align}
\operatorname{c}(g,i)=g_i\cdot I+g_0$
\end{align}$$

With the $\operatorname{c}(g,i)\in O(g_i\cdot I)$ and the $\operatorname{c}(g,i)\in O(g_i\cdot I)$ we have:

$$\operatorname{c}(g,i)\in O(g_i\cdot I)\operatorname{c}(g,i)=c\cdot I+c\cdot \cdot \cdot \cdot \cdot$$