(lecture13:normal-MLE)=
# Fitting the parameters of a Normal using the maximum likelihood principle

As before we have $N$ independent measurements.
Assume that the measurement $X_i$ follows a Normal distribution with parameters $\mu$ and $\sigma^2$:

$$
p(x_i|\mu,\sigma^2) = f(x_i;\mu,\sigma)=\frac{1}{\sqrt{2\pi\sigma^2}}\exp\left\{-\frac{(x_i-\mu)^2}{2\sigma^2}\right\}.
$$

So, in this case:

$$
\theta = (\mu, \sigma^2),
$$

and

$$
f(x;\theta) = \frac{1}{\sqrt{2\pi\sigma^2}}\exp\left\{-\frac{(x-\mu)^2}{2\sigma^2}\right\}.
$$

The likelihood of the data is:

$$
\begin{split}
p(x_{1:N}|\theta) &= \prod_{i=1}^Nf(x_i;\theta)\\
&= \prod_{i=1}^N\frac{1}{\sqrt{2\pi\sigma^2}}\exp\left\{-\frac{(x_i-\mu)^2}{2\sigma^2}\right\}\\
&= (2\pi\sigma^2)^{-\frac{N}{2}}\prod_{i=1}^N\exp\left\{-\frac{(x_i-\mu)^2}{2\sigma^2}\right\}\\
&= (2\pi\sigma^2)^{-\frac{N}{2}}\exp\left\{-\sum_{i=1}^N\frac{(x_i-\mu)^2}{2\sigma^2}\right\}.
\end{split}
$$

According to the maximum likelihood principle, we must pick $\mu$ and $\sigma^2$ that maximizes the logarithm of this expression.
Let's find the logarithm first.
I am going to call it $J(\mu,\sigma^2)$:

$$
J(\mu,\sigma^2) = \log p(x_{1:N}|\theta) = -\frac{N}{2}\log (2\pi) - \frac{N}{2}\log\sigma^2 - \frac{1}{2\sigma^2}\sum_{i=1}^N(x_i-\mu)^2.
$$

So, now model training has become a calculus problem.
You need to maximize the two-variable function $J(\mu,\sigma^2)$ with respect to
$\mu$ and $\sigma^2$.
How do you proceed?
We could either employ an optimization algorithm or we could do it analytically.
Let's do it analytically in this simple case.
A necessary condition is that the derivative of $J$ with respect to the parameters is zero.
Let's find the derivative of $J$ with respect to $\mu$.
It is:

$$
\begin{split}
\frac{\partial J}{\partial \mu} &=
\frac{\partial}{\partial \mu}\left[-\frac{N}{2}\log (2\pi) - \frac{N}{2}\log\sigma^2 - \frac{1}{2\sigma^2}\sum_{i=1}^N(x_i-\mu)^2\right]\\
&= \frac{\partial}{\partial \mu}\left[-\frac{1}{2\sigma^2}\sum_{i=1}^N(x_i-\mu)^2\right]\\
&= -\frac{1}{2\sigma^2}\sum_{i=1}^N\frac{\partial}{\partial \mu}(x_i-\mu)^2\\
&= -\frac{1}{2\sigma^2}\sum_{i=1}^N2(x_i-\mu)\frac{\partial}{\partial \mu}(x_i-\mu)\\
&= -\frac{1}{2\sigma^2}\sum_{i=1}^N2(x_i-\mu)(-1)\\
&= \frac{1}{\sigma^2}\sum_{i=1}^N(x_i-\mu)\\
&= \frac{1}{\sigma^2}\left[\sum_{i=1}^Nx_i - \sum_{i=1}^N\mu\right]\\
&= \frac{1}{\sigma^2}\left[\sum_{i=1}^Nx_i - N\mu\right].
\end{split}
$$

Alright, that wasn't too bad!
Now set this derivative equal to zero and you can solve for $\mu$.
You get:

$$
\hat{\mu} = \frac{1}{N}\sum_{i=1}^Nx_i.
$$

This is nice! It is exactly what we would expect! It also matches what we got using the method of moments.
Let's proceed to $\sigma^2$.
We need to find the derivative of $J$ with respect to it.

$$
\begin{split}
\frac{\partial J}{\partial \sigma^2} &=
\frac{\partial}{\partial \sigma^2}\left[-\frac{N}{2}\log (2\pi) - \frac{N}{2}\log\sigma^2 - \frac{1}{2\sigma^2}\sum_{i=1}^N(x_i-\mu)^2\right]\\
&= \frac{\partial}{\partial \sigma^2}\left[-\frac{N}{2}\log (2\pi) - \frac{N}{2}\log\sigma^2 - \left(\sigma^2\right)^{-1}\frac{1}{2}\sum_{i=1}^N(x_i-\mu)^2\right]\\
&= -\frac{N}{2}\frac{\partial}{\partial \sigma^2}\log\sigma^2
- \frac{\sum_{i=1}^N(x_i-\mu)^2}{2}\frac{\partial}{\partial \sigma^2}\left(\sigma^2\right)^{-1}\\
&=-\frac{N}{2}\frac{1}{\sigma^2} - \frac{\sum_{i=1}^N(x_i-\mu)^2}{2}(-1)\left(\sigma^2\right)^{-2}\\
&= -\frac{N}{2\sigma^2} + \frac{\sum_{i=1}^N(x_i-\mu)^2}{2\sigma^4}\\
&= \frac{-N\sigma^2 + \sum_{i=1}^N(x_i-\mu)^2}{2\sigma^4}.
\end{split}
$$

Setting this equal to zero and solving for $\sigma^2$, yields:

$$
\hat{\sigma}^2 = \frac{1}{N}\sum_{i=1}^N(x_i-\hat{\mu})^2,
$$

where I substituted $\hat{\mu}$ for $\mu$.
With a little bit of algebra you can show that this is exactly the same as the result obtained with the method of moments, i.e., it can be rewritten as:

$$
\hat{\sigma}^2 = \frac{1}{N}\sum_{i=1}^Nx_i^2-\hat{\mu}^2.
$$

We are not going to give a new example of this as the estimate is exactly the same to what we saw in [](lecture12:fitting-normals-to-data).
