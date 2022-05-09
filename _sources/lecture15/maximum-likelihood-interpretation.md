(lecture15:maximum-likelihood-interpretation)=
# Maximum likelihood interpretation of least squares

I will now show you how to derive least squares from the [maximum likelihood principle](lecture13:the-maximum-likelihood-principle).
Recall that the maximum likelihood principle states that you should pick the model parameters that maximize the probability of the data conditioned on the parameters.

Just like before assume that we have $N$ observations of inputs $\mathbf{x}_{1:N}$ and outputs $\mathbf{y}_{1:N}$.
We model the map between inputs and outputs using a generalized linear model with $M$ basis functions:

$$
y(\mathbf{x};\mathbf{w}) = \sum_{j=1}^{M} w_{j}\phi_{j}(\mathbf{x}) = \mathbf{w}^T\boldsymbol{\phi}(\mathbf{x})
$$

Now here is the difference with what we did before.
Instead of directly picking a loss function to minimize we come up with a probabilistic description of the measurement process.
In particular, we *model the measurement process* using a **likelihood** function:

$$
\mathbf{y}_{1:N} | \mathbf{x}_{1:N}, \mathbf{w} \sim p(\mathbf{y}_{1:N}|\mathbf{x}_{1:N}, \mathbf{w}).
$$

What is the interpretation of the likelihood function?
Well, $p(\mathbf{y}_{1:N} | \mathbf{x}_{1:N}, \mathbf{w})$ tells us how plausible is it to observe $\mathbf{y}_{1:N}$ at inputs $\mathbf{x}_{1:N}$, if we know that the model parameters are $\mathbf{w}$.

The most common choice for the likelihood of a single measurement is to pick it to be Normal.
This corresponds to the belief that our measurement is around the model prediction $\mathbf{w^{T}\boldsymbol{\phi}(\mathbf{x})}$
but it is contaminated with Gaussian noice of variance $\sigma^2$.
Mathematically, we have:

$$
\begin{split}
p(y_i|\mathbf{x}_i, \mathbf{w}, \sigma) &= N\left(y_i| y(\mathbf{x}_i;\mathbf{w}), \sigma^2\right)\\
&= N\left(y_i | \mathbf{w}^{T}\boldsymbol{\phi}(\mathbf{x}_i), \sigma^2\right),
\end{split}
$$

where $\sigma^2$ models the **variance of the measurement noise**.
Note that here I used the notation $N(y|\mu,\sigma^2)$ to denote the PDF of a Normal with mean $\mu$ and variance $\sigma^2$, i.e.,

$$
N(y|\mu,\sigma^2) := (2\pi\sigma^2)^{-\frac{1}{2}}\exp\left\{-\frac{(y-\mu)^2}{2\sigma^2}\right\}.
$$

Since, in almost all the cases we encounter, the measurements are independent conditioned on the model, then likelihood of the data factorizes as follows:

$$
\begin{split}
p(\mathbf{y}_{1:N}|\mathbf{x}_{1:N}, \mathbf{w}) &= \prod_{i=1}^Np(y_i|\mathbf{x}_i, \mathbf{w})\\
&= \prod_{i=1}^NN\left(y_i | \mathbf{w^{T}\boldsymbol{\phi}(\mathbf{x}_i)}, \sigma^2\right)\\
&= \prod_{i=1}^N(2\pi\sigma^2)^{-\frac{1}{2}}\exp\left\{-\frac{\left[y_i-\mathbf{w}^{T}\boldsymbol{\phi}(\mathbf{x}_i)\right]^2}{2\sigma^2}\right\}\\
&= (2\pi\sigma^2)^{-\frac{N}{2}}\exp\left\{-\sum_{i=1}^N\frac{\left[y_i-\mathbf{w}^{T}\boldsymbol{\phi}(\mathbf{x}_i)\right]^2}{2\sigma^2}\right\}\\
&= (2\pi\sigma^2)^{-\frac{N}{2}}\exp\left\{-\frac{1}{2\sigma^2}\sum_{i=1}^N\left[y_i-\mathbf{w}^{T}\boldsymbol{\phi}(\mathbf{x}_i)\right]^2\right\}\\
&= (2\pi\sigma^2)^{-\frac{N}{2}}\exp\left\{-\frac{1}{2\sigma^2}\parallel \mathbf{y}_{1:N}-\boldsymbol{\Phi}\mathbf{w}\parallel^2\right\},
\end{split}
$$

where $\boldsymbol{\Phi}$ is the $N\times M$ design matrix.

Now we are ready to apply the maximum likelihood function to find all the parameters.
This includes both the weight vector $\mathbf{w}$ and the measurement variance $\sigma^2$.
We need to solve this:

$$
\max_{\mathbf{w},\sigma^2}\log p(\mathbf{y}_{1:N}|\mathbf{x}_{1:N}, \mathbf{w}) =
\max_{\mathbf{w},\sigma^2}\left\{
-\frac{N}{2}\log (2\pi) - \frac{N}{2}\log \sigma^2 -\frac{1}{2\sigma^2}\parallel \mathbf{y}_{1:N}-\boldsymbol{\Phi}\mathbf{w}\parallel^2
  \right\}
$$

Notice that the rightmost part is actually the negative of the sum of square errors.
So, by maximizing the likelihood with respect to $\mathbf{w}$ we are actually minimizing the sum of square errors.
This means that the maximum likelihood weights and the least square weights are exactly the same!
We do not even have to do anything further.
The weights should satisfy this linear system:

$$
\boldsymbol{\Phi}^T\boldsymbol{\Phi}\mathbf{w} = \boldsymbol{\Phi}^T\mathbf{y}_{1:N}.
$$

This is nice.
The probabilistic interpretation above gives the same solution as least squares!
But there is more.
Notice that it can also give us an estimate for the measurement noise variance $\sigma^2$.
All you have to do is maximize likelihood with respect to $\sigma^2$.
If we take the derivative of the log-likelihood with respect to $\sigma^2$, set it equal to zero and solve for $\sigma^2$ you get:

$$
\sigma^2 = \frac{\parallel\mathbf{\Phi}\mathbf{w} - \mathbf{y}_{1:N}\parallel^2}{N}.
$$

Finally, you can incorporate this measurement uncertainty when you are making predictions.
This is done through the **point predictive distribution**, which is Normal in our case:

$$
p(y|\mathbf{x}, \mathbf{w}, \sigma^2) =
\mathcal{N}\left(y\middle|\mathbf{w}^T\mathbf{\phi}(\mathbf{x}), \sigma^2\right).
$$

In other words, your prediction about the measured output $y$ is that it will be Normally distributed around your model prediction with a variance $\sigma^2$.
You can use this to find a 95% credible interval.
Let's demonstrate with an example.s
