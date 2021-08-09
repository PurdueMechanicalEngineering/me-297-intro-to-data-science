(lecture13:repeated-experiments)=
# Repeated independent experiments

Imagine that we are performing the same experiment $N$ times.
Let's use the random variable $X_i$ to describe the measurement of the
$i$-th experiment.
Take $I$ to be the background information.
This $I$ contains how exactly we prepare the experimental apparatus, the
ambient conditions, etc.
Now, if we are very careful to prepare everything in exactly the same manner,
we can assume that the random variables $X_1, X_2,\dots,X_N$ are independent
conditioned on $I$.
That is, we can assume that the joint PDF factorizes:

$$
p(x_1,\dots,x_N|I) = p(x_1|I)\dots p(x_N|I) = \prod_{i=1}^Np(x_i|I).
$$

Let's introduce the shortcut notation:

$$
x_{1:N} = (x_1,\dots,x_N).
$$

We can rewrite the independence property as:

$$
p(x_{1:N}|I) = \prod_{i=1}^Np(x_i|I).
$$

Remember this:

> If you data coming from independent measurements, then their joint PDF factorizes conditioned on the background information.

Why is this important?
Well, it is important because it allows you to describe a supercomplicated object
like the joint PDF with the product of single-variable PDFs.
As we are going to see in the next section, this observation can lead to a very
famous and versatile model fitting method: the *maximum likelihood principle*.
