(lecture08:urn-example-sum-rule)=
# Example - Drawing balls from a box without replacement (sum rule)

We now continue our analysis of {ref}`lecture08:urn-example`.
Let us consider the probability of getting a red ball in the second draw without observing in the first draw $p(B_1|I)$.
We have two possibilities for the first draw.
We either got a blue ball (B_1 is true) or we got a red ball (R_1 is true).
In other words $B_1$ and $R_1$ cover all possibilities and are mutually exclusive.
We can use the sum rule:

$$
\begin{split}
p(R_2|I) &=& p(R_2|B_1,I)p(B_1|I) + p(R_2|R_1,I)p(R_1|I)\\
&=& \frac{2}{3}\frac{2}{5} + \frac{5}{9}\frac{3}{5}\\
&=& 0.6.
\end{split}
$$
