(lecture13:bernoulli-mle)=
# Fitting the Bernoulli with maximum likelihood

Let's look at another example of maximum likelihood estimation.
Assume that we are doing binary experiment with results $1$ (success) and $0$ (failure).
We model the result of the $i$-th experiment using a random variable $X_i$
which follows a Bernoulli distribution with unknown success probability $\theta$, i.e.,
we assume that:

$$
X_i \sim \text{Bernoulli}(\theta).
$$

This tells us what is the PMF of each random variable.
It is:

$$
p(X_i = 1|\theta) = \theta,
$$

and

$$
p(X_i = 0|\theta) = 1 - \theta.
$$

There is a common trick that you can use the express this PMF in a single equation.
If the experimental result is $x_i$ (either 0 or 1), then we can write the PMF
as:

$$
p(X_i = x_i|\theta) = \theta^{x_i}(1-\theta)^{1-x_i}.
$$

Mediate a bit on this.
If $x_i = 1$, then $1-x_i=0$ so the second part of the product becomes
$(1-\theta)^0 = 1$ and you get $\theta$.
Similarly, if $x_i=0$, the first part of the product becomes $\theta^0=1$ and thus you get $1-\theta$.
Nice right?
We will see this trick again in this class.

Now do it $N$ times and collect data $x_{1:N}$.
Paying attention so that the experiments are independent, we get that the data
likelihood is:

$$
p(x_{1:N}|\theta) = \prod_{i=1}^Np(x_i|\theta).
$$

Substituting the expression for the individual PMFs and doing a bit of algebra, we get:

$$
\begin{split}
p(x_{1:N}|\theta) &= \prod_{i=1}^Np(x_i|\theta)\\
&= \prod_{i=1}^N\theta^{x_i}(1-\theta)^{1-x_i}\\
&= \theta^{\sum_{i=1}^Nx_i}(1-\theta)^{\sum_{i=1}^N(1-x_i)}\\
&= \theta^{\sum_{i=1}^Nx_i}(1-\theta)^{N-\sum_{i=1}^Nx_i}.
\end{split}
$$

This has a nice intuitive meaning.
Note that $\sum_{i=1}^Nx_i$ is the number of successes in $N$ experiments.
Similarly, $N - \sum_{i=1}^Nx_i$ is the number of failures in $N$ experiments.

Want to find the maximum likelihood estimator of the parameter $\theta$.
Just like before, we will maximize the logarithm of the likelihood:

$$
\begin{split}
J(\theta) &= \log p(x_{1:N}|\theta)\\
&= \log\left[\theta^{\sum_{i=1}^Nx_i}(1-\theta)^{N-\sum_{i=1}^Nx_i}\right]\\
&= \sum_{i=1}^Nx_i\log \theta + (N-\sum_{i=1}^Nx_i)\log(1-\theta).
\end{split}
$$

We will find the maximum analytically.
To this end, take the derivative of $J$ with respect to $\theta$:

$$
\begin{split}
\frac{dJ(\theta)}{d\theta} &= \frac{d}{d\theta}\left[\sum_{i=1}^Nx_i\log \theta + (N-\sum_{i=1}^Nx_i)\log(1-\theta)\right]\\
&= \sum_{i=1}^Nx_i\frac{1}{\theta} + (N-\sum_{i=1}^Nx_i)\frac{(-1)}{1-\theta}\\
&= \sum_{i=1}^Nx_i\frac{1}{\theta} - (N-\sum_{i=1}^Nx_i)\frac{1}{1-\theta}\\
&= \frac{\sum_{i=1}^Nx_i(1-\theta) - (N-\sum_{i=1}^Nx_i)\theta}{\theta(1-\theta)}\\
&= \frac{\sum_{i=1}^Nx_i - N\theta}{\theta(1-\theta)}.
\end{split}
$$

Setting this to zero and solving for $\theta$ yields:

$$
\hat{\theta} = \frac{1}{N}\sum_{i=1}^Nx_i.
$$

Don't you feel good about this result?
It's telling you the observe success frequency is a good estimate for the probability of success!

```{note}
The MLE becomes better and better as the number of observations increases.
As a matter of fact, you can show that if the model is correctly representing reality,
MLE will converge to the true value of the parameters in the limit of infinite samples.
In practice, however, you never have infinite samples so MLE will not be perfect.
This is fine.
You can use Bootstrapping to get estimate of how much uncertainty there is in the MLE estimate.
Remember how we did it dit it [here](lecture13:fitting-bootstrapping).
Alternatively, you can use a Bayesian approach to estimate the parameters, albeit this is an advanced topic that goes beyond this course.
If you want to learn more about the Bayesian approach look at [ME 53900 Introduction to Scientific Machine Learning](https://github.com/PredictiveScienceLab/data-analytics-se).
```
