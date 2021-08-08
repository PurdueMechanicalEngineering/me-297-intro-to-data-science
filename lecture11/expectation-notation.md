(lecture11:expectation-notation)=
# Simplifying our notation about expectations

We saw that for discrete random variables we need to write:

$$
\mathbf{E}[X] = \sum_x xp(x),
$$

while for a continuous random variable we need to write:

$$
\mathbf{E}[X] = \int_{-\infty}^{+\infty} xp(x).
$$

Let's make the following convention.
We are going to write:

$$
\mathbf{E}[X] = \int xp(x),
$$

no matter what the nature of $X$ is is.
If it is discrete, we will sum over its values.
If it is continuous, we will integrate over its values.
This is the notation most commonly used in practice.
