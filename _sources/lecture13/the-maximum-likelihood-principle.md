(lecture13:the-maximum-likelihood-principle)=
# The maximum likelihood principle

Assume that we have observed some data:

$$
x_{1:N} = (x_1,\dots,x_N),
$$

coming from $N$ independent measurements.
Let's say that we model its observation with a random variable $X_i$.
Now these random variables will be independent (conditional on the details of the experiment).
So, the joint PDF of $X_1,\dots,X_N$ will factorize.
Furthermore, because the experimental measurements are prepared in the same way,
the PDF of each one of the $X_i$'s will be the same function.
For example, we can assume that the PDF of $X_i$ is given by:

$$
p(x_i|\theta) = f(x_i;\theta),
$$

where $f(x_i;\theta)$ is some functional form with unknown parameters $\theta$.
So, here $f(x;\theta)$ is essentially our model of the experiment and $\theta$ are the unknown parameters that we need to determine from the experimental data.
The maximum likelihood principle gives us a way to pick $\theta$ using the data $x_{1:N}$.
Here is what it is all about.

First, write down the joint PDF of the experimental data conditioned on the parameters.
It is:

$$
p(x_{1:N}|\theta) = \prod_{i=1}^Nf(x_i;\theta).
$$

This expression is called the *likelihood of the data* given the model parameters $\theta$.
Intuitively, it gives you the probability of observing $x_{1:N}$ if the model parameters were $\theta$.
We are ready for the maximum likelihood principle.
The *maximum likelihood principle* tells you that you should pick the parameters that maximize the likelihood.
In other words, pick the parameters that make your data most probable.
So, the training problem becomes now an optimization problem:

$$
\max_{\theta} p(x_{1:N}|\theta) = \max_{\theta}\prod_{i=1}^Nf(x_i;\theta).
$$

In practice, we maximize the logarithm of the likelihood instead of directly the likelihood, i.e., we solve this optimization problem:

$$
\max_{\theta} \log p(x_{1:N}|\theta) = \max_{\theta}\sum_{i=1}^N\log f(x_i;\theta);
$$

Because the logarithm is an increasing function $\theta$ the two problems are mathematically equivalent.
But the second problem behaves better numerically.

The estimate of $\theta$ you obtain in this way is called the *maximum likelihood estimate* or MLE.
Let's now look at a concrete example.
