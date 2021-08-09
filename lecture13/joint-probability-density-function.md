(lecture13:joint-probability-density-function)=
# The joint probability density function

Consider two continuous random variables $X$ and $Y$.
The *joint probability density function* of the pair $(X,Y)$ is the function $p(x,y)$ giving the probability density around $X=x$ and $Y=y$.
Mathematically, we have:

$$
p(x,y|I) \approx \frac{p(x\le X \le x + \Delta x, y\le Y \le y+\Delta y,I)}{\Delta x\Delta y},
$$

with equality when the box around $(x,y)$ shrinks to a point.
Here $I$ is any background information we may have.
If there is no ambiguity, we can drop the background information and write $p(x,y)$ instead.
But remember, that there is always some background information...

## Properties of the joint probability density function
+ It is nonnegative:

$$
p(x,y) \ge 0.
$$

+ If you integrate over all the possible values of all random variables, you should get one:

$$
\int p(x,y)dxdy = 1.
$$

+ If you *marginalize* over the values of one of the random variables you get the PDF of the other.
For example:

$$
p(x) = \int p(x,y)dy,
$$

and

$$
p(y) = \int p(x, y)dx.
$$

The marginalization property is a direct consequence of the [sum rule](lecture08:sum-rule) of probability.

+ If you take a subset $A$ of $\mathbb{R}^2$, then the probability that $(X,Y)$
  is in $A$ is given by:

  $$
  p\left((X,Y)\in A\right) = \int_{A} f_{X,Y}(x,y)dxdy.
  $$

This is a standard double integral.

## Conditioning a random variable on another

If we had observed that $Y=y$, how would this change the PDF of $X$?
The answer is given via Bayes' rule.
The PDF of $X$ conditioned on $Y=y$ is:

$$
p(x|y) = \frac{p(x,y)}{p(y)}.
$$

This is called the conditional PDF of $X$ given $Y=y$.

## Independent random variables

We say that two random variables $X$ and $Y$ are independent given the background information $I$
if and only if conditioning on one does not tell you anything about the other, i.e.,

$$
p(x|y, I) = p(x|I).
$$

We may be dropping $I$ if it is fixed.
A very important property of independent random variables is that their joint
PDF is the product of individual PDFs:

$$
p(x,y|I) = p(x|I)p(y|I).
$$

You can prove this very easily using the product rule and the definition of
independence. Here it is:

$$
p(x,y|I) = p(x|y,I)p(y|I) = p(x|I)p(y|I).
$$

It is also very easy to show that if $Y$ does not give any information about $X$,
then the reverse also holds:

$$
p(y|x,I) = p(y|I).
$$

## The joint PDF of more than two random variables
Finally, note that the concept of joint PDF and independence, generalizes to
arbitrary number of random variables.
For example, you could have $p(x, y, z)$ or $p(x, y, z, w)$, etc.
You can do all sorts of things with these object, e.g., your can marginalize
any number of them to get the joint PDF of the rest:

$$
p(x,y) = \int p(x,y,z,w)dzdw,
$$

or you can condition on one or more of the random variables.

$$
p(z, w) = \frac{p(x,y,z,w)}{p(x, y)},
$$

If they were all independent, then the joint PDF would factorize like this:

$$
p(x, y, z, w) = p(x)p(y)p(z)p(w).
$$

There is a lot of meat here, but it is beyond the scope of this class to cover everything...
