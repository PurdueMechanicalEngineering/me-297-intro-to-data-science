(lecture09:probability-mass-function)=
# The probability mass function


Say that $X$ is the result of a coin toss experiment.
As we have already discussed with can code the result of the experiment with
natural numbers.
Here we use 0 for "heads" and 1 for "tails."
If we have a fair coin, we know that $X$ takes the value $0$ with probability
$0.5$ and the value $1$ also with probability $0.5$.
We can write this succinctly as:

$$
X = \begin{cases}
0,\;\text{with probability}\;0.5,\\
1,\;\text{otherwise}.
\end{cases}
$$

But there is another way to write this that is often more convenient.
Here it is:

$$
p(X=0) = \text{probability that}\;X\;\text{takes the value}\;0 = 0.5.
$$

Now, we can use the obvious rule of probability to get:

$$
p(X=1) = 1 - p(X\not=1) = 1 - p(X=0) = 1 - 0.5 = 0.5.
$$

You can now define the following function:

$$
f_X(x) := \text{probability that}\;X\;\text{takes the value}\;x \equiv p(X=x).
$$

This is a function associated with the discrete random variable $X$ (that is why
  $X$ is used as a subscript in $f_X$).
It takes any possible value $x$ for $X$ and responds with the probability of
$X$ taking that value.
It has a special name.
It is called the *probability mass function* or PMF of the discrete random
variable $X$.

```{note}
We have silently introduced the following standard notational conventions:
+ Use upper case letters to represent random variables, like $X, Y, Z$.
+ Use lower case letters to represent the values of random variables,
  like $x, y, z$ can take.
```

The notation $f_X(x)$ for the PMF is a bit of an overkill in my opinion.
It is commonly used in mathematical textbooks where rigor is valued above
everything.
In practice, now on wants to write or type this many symbols.
So, it is a common convention to write $p(x)$ instead of $f_X(x)$ when there is
no ambiguity.
Symbolically, we follow this convention:

$$
p(x) \equiv f_X(x) \equiv p(X=x).
$$

In other words, when you see $p(x)$ we are talking about the PMF of a random
variable $\text{capitalize}(x) = X$ evaluated at $x$.
Similarly, if you see $p(y)$ we are referring to the PMF of the random variable
$Y$ evaluated at $y$.
However, it meaningless to write $p(0)$.
What does it mean? To which random variable do you refer? $X$ or $Y$?
So, in case you want to plug in a specific value you should write $p(X=0)$ or
$p(Y=0)$, etc.

```{note}
In everything I write below there is supposed to be some background information
$I$.
So, I should be really writing $p(X=0|I), p(x|I)$, etc.
However, since $I$ remains fixed I decided to drop it from the notation.
```
