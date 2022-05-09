(lecture09:properties-of-the-probability-mass-function)=
# Properties of the probability mass function

There are some standard properties of the probability mass function that are worth memorizing.

First, he probability mass function is nonnegative:

$$
p(x) \ge 0,
$$

for the possible values $x$ that the random variable $X$ can take.

Second, the probability mass function is normalized:

$$
\sum_x p(x) = 1.
$$

The sum is over all the possible values of $X$.
This is a direct consequence of the fact that $X$ must take some value of
all that are possible.

Finally, you can use the probability mass function to find the probability that
$X$ takes values in any set of possibilities.
For example:

$$
p(X=x_1\;\text{or}\;X=x_2) = p(x_1) + p(x_2),
$$

if $x_1\not= x_2$.

Similarly, if $x_1, x_2,$ and $x_3$ are all different, then:

$$
p(X=x_1\;\text{or}\;X=x_2\;\text{or}\;X=x_3) = p(x_1) + p(x_2) + p(x_3).
$$

An, in general for any set of possible values of $X$, say $A$, the probability
of $X$ taking values in $A$ is:

$$
p(X\in A) = \sum_{x\in A} p(x).
$$

