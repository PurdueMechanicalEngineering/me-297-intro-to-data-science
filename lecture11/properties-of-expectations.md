(lecture11:properties-of-expectations)=
# Properties of expectations

There are few very important properties that expectations satisfy.
Let's introduce them one by one.
In what follows $X$ is a random variable, either discrete or continuous.

(lecture11:expectation-property-1)=
## Expectation Property 1: The expectation of a scalar times a random variable

Take any scalar $\lambda$.
Then:

$$
\mathbf{E}[\lambda X] = \lambda \mathbf{E}[X].
$$

The proof is super easy. It follows directly from the properties of integrals
and summations.

(lecture11:expectation-property-3)=
## Expectation Property 2: The expectation of a function of a random variable

Let $f(x)$ be any function defined over the support of the random variable $X$.
Then:

$$
Z = f(X),
$$

is a new random variable.
It is just a random variable that is induced by transforming the values generated
by $X$ through the function $f(x)$.
Then, the expectation of $Z$ is:

$$
\mathbf{E}[Z] \equiv \mathbf{E}[f(X)] = \int f(x) p(x) dx.
$$

```{note}
We will not prove this property.
The proof is non-trivial and requires expressing the PDF of $Z=f(X)$ in terms
of the PDF of $X$.
Because people tend to take this property for granted, it is known as
[the law of the unconscious statistician](https://en.wikipedia.org/wiki/Law_of_the_unconscious_statistician)...
```

This formula is, of course, extremely convenient for calculating expectations
of functions of random variables.
Let's see an example.
Assume that $X$ is a uniform:

$$
X \sim U([0,1]).
$$

Then:

$$
\begin{split}
\mathbf{E}[X^2] &= \int x^2 p(x) dx\\
&= \int_0^1 x^2 dx\\
&= \frac{x^3}{3} |_0^1\\
&= \frac{1}{3}.
\end{split}
$$

Similarly,

$$
\mathbf{E}[e^X] = \int_0^1 e^x dx = e.
$$

And so on and so forth.

```{warning}
I have to say this because I have seen it many times...
You may get the urge to write:

$$
\mathbf{E}[f(X)] = f\left(\mathbf{E}[X]\right).\;\text{(WRONG)}.
$$

Please don't. This formula does not hold unless $f(x)$ is a linear function
(i.e., $f(x) = ax + b$).

Things are way more complicated than this.
For example, for [convex functions](https://en.wikipedia.org/wiki/Jensen%27s_inequality) you have that:

$$
f\left(\mathbf{E}[X]\right) \le \mathbf{E}[f(X)]\;(f\text{convex}).
$$

For concave functions you have the opposite inequality.
For arbitrary functions it could go in any direction.
```

(lecture11:expectation-property-3)=
## Expectation Property 3: The expectation of a random variable plus a scalar

This property is a direct corollary of the second property, but it is worth
spelling it out on its own.
Take a scalar $\lambda$.
Then:

$$
\mathbf{E}[X + \lambda] = \mathbf{E}[X] + \lambda.
$$

The property makes a lot of intuitive sense.

Let's actually do the proof of this one.
We have:

$$
\begin{split}
\mathbf{E}[X+\lambda] &= \int (x + \lambda)p(x)dx\;\text{(property 2)}\\
&= \int x p(x) dx + \lambda\int p(x) dx\;\text{(integral properties)}\\
&= \mathbf{E}[X] + \lambda\;\text{(PDF integrates to one)}.
\end{split}
$$
