(lecture09:discrete-random-variables)=
# Discrete Random variables

## Definition
Imagine that you are conducting an experiment, e.g. a coin toss, throwing a die.
How can you talk about the result of the experiment before you actually do it?
This is where the concept of a *random variable* comes to the rescue.
You can simply use a letter like $X$ to indicate the result of the experiment
before you actually do it.
So, remember:
> A random variable $X$ models the result of a random experiment.

```{note}
There is a precise mathematical definition of random variables.
However, it requires introducing some advanced concepts (probability spaces,
  measurable functions, etc.) which are all well beyond the scope of this
  couse.
We should be fine with our informal definition of a random variable within this
course.
```

## Discrete vs continuous random variables
Now, if the result of experiment is discrete consists of discrete labels, we say
that we have a *discrete random variable*.
The result of a coin toss is a discrete random variable because there are only
two possibilities (heads and tails).
The result of throwing a six-sided die is also a discrete random variable
because there are six possibilities.
However, there are many experiments that do not have discrete outcomes.
For example, consider the experiment that measures the mass of a manufactured
steel ball.
This is a scalar number.
Such experiments require *continuous random variables* which will be the subject
of {ref}`lecture10`.
From now on, we will restrict our attention to discrete random variables.

## Coding the result of an experiment with discrete number of outcomes
So, discrete random variables can really take any type of value.
For example, the coin toss results in "heads" or "tails".
The six-sided die in 1, 2, 3, 4, 5, or 6.
Other possibilities of discrete random variable values are colors: "red," "yellow," "green," etc.
There is no end to this.
However, since these are types have discrete labels you can always code them
using natural numbers 0, 1, 2, 3, etc.
For example, when we are dealing with a coin toss we can code "heads" with 0
and "tails" with 1.
Or when we are dealing with color labels, we can code "red" with 0, "yellow"
with 1 and "green" with 2.
So, there is no loss of generality in assuming that the result of a
an experiment resulting in a discrete random variable is some number 0, 1, 2, ...
Finally, notice that we allow for an infinite number of possibilities as soon as
they remain discrete.
