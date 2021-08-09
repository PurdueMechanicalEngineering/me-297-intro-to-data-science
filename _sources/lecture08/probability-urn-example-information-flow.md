(lecture08:urn-example-information-flow)=
# Example - Drawing balls from a box without replacement (information flow)

There is one more point that I would like to make on {ref}`lecture08:urn-example`.
If you paid close attention, in all our examples the conditioning we did followed the causality.
For instance, in the urn example we where writing $p(R_2|B_1,I)$ for the probability of getting a red ball in the second draw after having observed the blue ball in the first draw.
However, conditioning on stuff **does not have to follow the causal links**.
It is completely legitimate to ask what is the probability of a blue ball in the first draw given that you have observed that the result of the second draw is a red ball.

That is, you can write down the mathematical expression $p(B_1|R_2,I)$.
This does not mean that $R_2$ is causing $B_1$.
What happens here is that observing $R_2$ changes your state of knowledge about $B_1$.
This is an example of information flowing in the reverse order of a causal link.
Let's solve it analytically.
We have by applying the product rule:

$$
\begin{split}
p(B_1|R_2,I) &=& \frac{p(B_1,R_2|I)}{p(R_2|I)}\\
&=& \frac{\frac{4}{15}}{0.6}\\
&\approx& 0.44.
\end{split}
$$

This is greater than the probability of drawing a blue ball in the first place, $p(B_1|I) = 0.4$.
Does this make sense?
Yes it does!
Here is how you should think:
+ You draw a ball without seeing it and you put it in another box.
+ You draw the second ball and you see that it is a red one.
+ This means that this particular red ball was not picked in the first draw.
+ So, it is as if in the first draw you had one less red to worry about which increases the probability of a blue.
+ So, it is as if you had 5 red balls and 4 blue balls giving you a probability of blue $\frac{4}{9}\approx 0.44$.

This is amazing!
It agrees perfectly with the prediction of the product rule.
This was one of our desiderata (if you compute something in two different ways you should get the same result).
You can rest assured that as soon as you use the product rule and the sum rule and logic, it is impossible to get the wrong answer.
That is, if you can actually carry out the computations.
