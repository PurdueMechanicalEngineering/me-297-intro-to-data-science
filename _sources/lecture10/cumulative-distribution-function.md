(lecture10:cumulative-distribution-function)=
# The cumulative distribution function

Take a continuous random variable $X$.
The *cumulative distribution function* (CDF) $F_X(x)$ gives you the probability
that $X$ is smaller than $x$, i.e., the definition is:

$$
F_X(x) := p(X\le x).
$$

Notice that the $X$ is a subscript here.
This is because each random variable has its own CDF.
Now to save me some typing, I am going to write $F(x)$ instead of $F_X(x)$.
We only have one random variable anyway.

There are certain properties that the CDF satisfies.
We visualize the properties in {numref}`cdf-shape`.
It is very instructive to go through the proof of these properties.
The remarkable thing is that the proofs only use the basic probability rules.

```{figure} cdf.png
:height: 250px
:name: cdf-shape

The CDF of a typical continuous random variable looks like this.
It is an increasing function.
It converges to zero for very small values.
It converges to one for very large values.
The probability of the random variable being within a given interval is
the difference of CDF values at the endpoints of that interval.
In this figure, $p(1 < X \le 3) = F(3) - F(1)$.
```

## CDF property 1: The CDF is an increasing function of $x$

This property makes a lot of intuitive sense if you think about what the CDF
means:

+ The CDF at $x$ is the probability that the random variable $X$ is smaller
than $x$.
+ If you increase $x$, then the probability that $X$ is smaller than $x$ should
increase.

This is pretty much it.
But let's actually prove it rigorously.
Take two values $x_1$ and $x_2$ such that $x_1 < x_2$.
We need to show that $F(x_1)\le F(x_2)$.
Here it is:

$$
\begin{split}
F(x_2) &= p(X \le x_2)\;\text{(definition)}\\
&= p(X \le x_1 \;\text{or}\; x_1 < X \le x_2)\;\text{(logic)}\\
&= p(X \le x_1) + p(x_1 < X \le x_2)\;\text{(sum rule)}\\
&= F(x_1) + p(x_1 < X \le x_2)\;\text{(definition)}\\
&\ge F(x_1),
\end{split}
$$

because $p(x_1 < X \le x_2)\ge 0$.
This concludes the proof.

## CDF property 2: The CDF goes to zero for very small values

Mathematically, this is written as:

$$
F(-\infty) = \lim_{x\rightarrow -\infty} F(x) = 0.
$$

Again, this is easy to understand:

+ The CDF at $x$ is the probability that the random variable $X$ is smaller
than $x$.
+ Make the $x$ very very small, smaller than any of the values $X$ can take,
and you get zero probability.

## CDF property 3: The CDF goes to one for very large values

Mathematically, this is written as:

$$
F(+\infty) = \lim_{x\rightarrow +\infty} F(x) = 1.
$$

Use your intuition:

+ The CDF at $x$ is the probability that the random variable $X$ is smaller
than $x$.
+ Make the $x$ very very large, larger than any of the values $X$ can take,
and you get probability one.

## CDF property 4: Probability of values in interval

This property says that the probability of the random variable $X$ taking values
inside an interval $[a,b]$ is given by the difference of the values of CDF at
$b$ and $a$.
Mathematically:

$$
p(a < X \le b) = F(b) - F(a).
$$

This is obviously extremely useful because it tells you how to find any interval
probability if you know the CDF.
The proof is not that trivial.
But it only uses the common rules.
Let's do it:

$$
\begin{split}
p(a < X \le b) &= 1 - p(X \le a\;\text{or}\; X>b)\;\text{(obvious rule)}\\
&= 1 - \left[p(X \le a) + p(X > b)\right]\;\text{(sum rule)}\\
&= 1 - \left[p(X \le a) + 1 - p(X\le b)\right]\;\text{(obvious rule)}\\
&= p(X\le b) - p(X \le a)\;\text{(definition)}\\
&= F(b) - F(a).
\end{split}
$$

A corollary of this property is that if $F(x)$ is a continuous function for all
$x$, then the probability that $X$ takes exactly a given value is always zero.
Here is how you can see this.
Take the probability that $X$ is between $x$ and $x + \Delta x$ for some small
$\Delta x$. It is:

$$
p(x < X \le x + \Delta x) = F(x + \Delta x) - F(x).
$$

Now, take $\Delta x \rightarrow 0$.
The left hand side goes to $p(X=x)$.
The right hand side goes to zero if $F(x)$ is continuous at $x$.
Thus:

$$
p(X = x) = 0,
$$

if $F(x)$ is continuous at $x$.

All of the continuous random variables we will consider in this class satisfy
this property.
