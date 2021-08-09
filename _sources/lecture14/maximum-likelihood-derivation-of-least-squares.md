(lecture15:maximum-likelihood-derivation-of-least-squares)=
# Maximum likelihood derivation of least squares

Let's say that we have a $N$ observations consisting of inputs (features):

$$
x_{1:N} = (x_1,\dots,x_N),
$$

and outputs (targets):

$$
y_{1:N} = (y_1,\dots,y_N).
$$

We want to learn the map (function) that connects the inputs to the outputs.
We say that we have a *regression* problem when the outputs are continuous quantities, e.g., mass, height, price.
When the outputs are discrete, e.g., colors, numbers, then we say that we have a *classification* problem.
In this lecture, the focus will be on regression.

To proceed, you need to make a model that connects the inputs to the outputs.
The simplest such model is:

$$
y = w_0 + w_1 x + \text{measurement noise}.
$$

This is the linear model we saw in the previous lecture with $w_0 = b$ and $w_1 = a$.
The parameters $\mathbf{w} = (w_0, w_1)$ are called the regression *weights* and we need to find them using the observations $x_{1:N}$ and $y_{1:N}$.

In the previous lecture, we fitted the model by minimizing the sum of square errors:

$$
L(w_0, w_1) = \sum_{i=1}^N(y_i - w_0 - w_1 x_i)^2.
$$

Now, I am going to show you how this is the same as maximizing the likelihood of the data under the assumption that the measurement noise is Normal!
Here is how we think.
First, we make the $i$-th a random variable:

$$
Y_i = w_0 + w_1 x_i + Z_i,
$$

where $x_i$ is given and $Z_i$ is a Normal random variable modeling the measurement noise.
We will take it to be:

$$
Z_i \sim N(0, \sigma^2),
$$

where $\sigma^2$ is the measurement variance, one more parameter that we would like to find.
