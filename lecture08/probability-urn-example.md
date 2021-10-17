(lecture08:urn-example)=
# Example - Drawing balls from a box without replacement

Consider the following information I:

> We are given a box with 10 balls 6 of which are red and 4 of which are blue. The box is sufficiently mixed so that when we get a ball from it, we don't know which one we pick. When we take a ball out of the box, we do not put it back.

```{figure} urn.png
:height: 250px
:name: urn-example

A box with 10 balls.
```

Now, let's say that we draw the first ball.
Let $B_1$ be the logical proposition:

> The first ball we draw is blue.

What is the probability of $B_1$?
Our intuition tells us to set:

$$
p(B_1|I) = \frac{4}{10} = \frac{2}{5}.
$$

This is known as the *principle of insufficient reason*.
We can now use the **obvious rule** to find the probability of drawing a red ball, i.e., of $\neg B_1$.
Of course, $\neg B_1$ is just the sentence:

> The first ball we draw is red.

So, let's also call $\neg B_1$ with the name $R_1$.
It is:

$$
p(R_1|I) = p(\neg B_1|I) = 1 - p(B_1|I) = 1 - \frac{2}{5} = \frac{3}{5}.
$$

Great! Let's continue with drawing a second ball.
Consider the sentence $R_2$:

> The second ball we draw is red.

What is the probability of $R_2$ given that $B_1$ is true?
We just need to use common sense to find this probability:
+ We had 10 balls, 6 red and 4 blue.
+ Since $B_1$ is true (the first ball was blue), we now have 6 red and 3 blue balls.
+ Therefore, the probability that we draw a red ball next is:
+
$$
p(R_2|B_1,I) = \frac{6}{9} = \frac{2}{3}.
$$

Similarly, we can find the probability that we draw a red ball in the second draw given that we drew a red ball in the first draw:
+ We had 10 balls, 6 red and 4 blue.
+ Since $R_1$ is true (the first ball is red), we now have 5 red and 4 blue balls.
+ Therefore, the probability that we draw a red ball next is:

$$
p(R_2|R_1,I) = \frac{5}{9}.
$$

All, this was easy.
Let's find the probability that we draw a blue ball in the first draw and a red ball in the second draw.
This time, we have to use the **product rule**:

$$
p(B_1, R_2|I) = p(R_2|B_1,I) p(B_1|I) = \frac{2}{3}\frac{2}{5} = \frac{4}{15}.
$$
