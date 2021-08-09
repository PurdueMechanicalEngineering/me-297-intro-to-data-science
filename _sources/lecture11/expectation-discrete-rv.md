(lecture11:expectations)=
# Expectation of discrete random variables

Let $X$ be a discrete random variable taking values $0,1,2,\dots$.
The *expectation* of $X$ is defined by:

$$
\mathbf{E}[X] = \sum_x xp(x),
$$

where $p(x)$ is the PMF and the summation is over all discrete values of $X$.

```{note}
The expectation of a random variable is also known as the *mean* of the random
variable.
```

You can think of the expectation as the value one should "expect" to get.
However, take this interpretation with a grain of salt because the expectation
may not even be a value that the random variable can take...
Let's look at some examples.
