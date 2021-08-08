(lecture15:regression-with-one-variable-revisited)=
# Regression with one variable revisited

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
The parameters $w_0$ and $w_1$ are called the regression *weights* and we need to find them using the observations $x_{1:N}$ and $y_{1:N}$.

In the previous lecture, we fitted the model by minimizing the sum of square errors:

$$
L(w_0, w_1) = \sum_{i=1}^N(y_i - w_0 - w_1 x_i)^2.
$$

Now we are going to express this equation using linear algebra.
We do this for two reasons:

+ It is a lot of fun!
+ It is essential for formulating the fitting problem for more complicated models.


We will need the *design matrix*:

$$
\mathbf{X} =
\begin{bmatrix}
1 & x_1 \\
1 & x_2 \\
\vdots & \vdots \\
1 & x_N
\end{bmatrix}.
$$

The design matrix $\mathbf{X}$ is a $N\times 2$ matrix with the first column being just one and the second column being the observed inputs.
We will also need, the *vector of observed outputs*:

$$
\mathbf{y} = y_{1:N} = (y_1, \dots, y_N),
$$

and the *vector of weights*:

$$
\mathbf{w} = (w_0, w_1).
$$

I hope that you remember how to do [matrix-vector multiplication](https://en.wikipedia.org/wiki/Matrix_multiplication).
Notice what we get when we multiply the design matrix $\mathbf{X}$ with the weight vector $\mathbf{w}$:

$$
\begin{split}
\mathbf{X}\mathbf{w} &=
\begin{bmatrix}
1 & x_1 \\
1 & x_2 \\
\vdots & \vdots \\
1 & x_N
\end{bmatrix}\cdot
\begin{bmatrix}
w_0\\
w_1
\end{bmatrix}\\
&=
\begin{bmatrix}
w_0 + w_1 x_1 \\
w_0 + w_1 x_2 \\
\vdots\\
w_0 + w_1 x_N
\end{bmatrix}.
\end{split}
$$

Wow! So, $\mathbf{X}\mathbf{w}$ is an $N$-dimensional vector that contains the predictions of our linear model at the observed inputs.
If we subtract this vector from the vector of observed outputs $\mathbf{y}$, we get the prediction errors:

$$
\mathbf{y} - \mathbf{X}\mathbf{w} =
\begin{bmatrix}
y_1 - w_0 - w_1 x_1\\
y_2 - w_0 - w_1 x_2\\
\vdots
y_N - w_0 - w_1 x_N
\end{bmatrix}.
$$

Okay. Now recall that the [Euclidian norm](https://en.wikipedia.org/wiki/Norm_(mathematics) $\parallel\mathbf{v}\parallel$ of a vector is the square root of the sum of the squares of its components.
Hmm.
Let's take the square of the Euclidian norm of the error vector.
It is:

$$
\parallel \mathbf{y} - \mathbf{X}\mathbf{w}\parallel^2 =
\sum_{i=1}^N(y_i - w_0 - w_1x_i)^2.
$$

But this is just sum of square errors, i.e., we have shown that:

$$
L(w_0, w_1) = L(\mathbf{w}) = \parallel \mathbf{y} - \mathbf{X}\mathbf{w}\parallel^2.
$$

We have managed to express the loss function using linear algebra.
The mathematical problem of finding the best weight vector is now:

$$
\min_{\mathbf{w}} L(\mathbf{w}) = \min_{\mathbf{w}} \parallel \mathbf{y} - \mathbf{X}\mathbf{w}\parallel^2.
$$

This form is much more convenient mathematically.
Remember that to solve the minimization problem, we need to take the gradient of $L(\mathbf{w})$ with respect to $\mathbf{w}$ and set the result equal to zero.
This form, allows us to take derivatives in a much easier way.
But there is one more thing that we could do before we take the gradient.
Notice that the Euclidian norm of a vector $\mathbf{v}$ satisfies:

$$
\parallel \mathbf{v}\parallel^2 = \mathbf{v}^T\mathbf{v},
$$

where we are thinking of $\mathbf{v}$ as a column matrix and $\mathbf{v}^T$ is the transpose of $\mathbf{v}$, i.e., a row matrix.
To prove the equality, we start from the right hand side:

$$
\begin{split}
\mathbf{v}^T\mathbf{v} &=
\begin{bmatrix}
v_1 & v_2 & \cdots & v_N
\end{bmatrix}\cdot
\begin{bmatrix}
v_1\\
v_2\\
\vdots\\
v_N
\end{bmatrix}\\
&= \sum_{i=1}^N v_i^2\\
&= \parallel \mathbf{v}\parallel^2.
\end{split}
$$

Interesting! So we can rewrite the sum of square errors as:

$$
\begin{split}
L(\mathbf{w}) &= \parallel \mathbf{y} - \mathbf{X}\mathbf{w}\parallel^2
&= \left(\mathbf{y} - \mathbf{X}\mathbf{w}\right)^T\left(\mathbf{y} - \mathbf{X}\mathbf{w}\right)\\
&= \left[\mathbf{y}^T - \left(\mathbf{X}\mathbf{w}\right)^T\right]\left(\mathbf{y} - \mathbf{X}\mathbf{w}\right)\\
&= \left(\mathbf{y}^T - \mathbf{w}^T\mathbf{X}^T\right)\left(\mathbf{y} - \mathbf{X}\mathbf{w}\right)\\
&= \mathbf{y}^T\mathbf{y} - \mathbf{w}^T\mathbf{X}^T\mathbf{y}
- \mathbf{y}^T\mathbf{X}\mathbf{w} + \mathbf{w}^T\mathbf{X}^T\mathbf{X}\mathbf{w}
\end{split}
$$

Now, because $\mathbf{w}^T\mathbf{X}^T\mathbf{y}$ is just a number (think about the dimensions $(1\times 2)\times (2\times N)\times (N \times 1) = 1\times 1$), it is the same as its transpose, i.e.,

$$
\mathbf{w}^T\mathbf{X}^T\mathbf{y} = \left(\mathbf{w}^T\mathbf{X}^T\mathbf{y}\right)^T =
\mathbf{y}^T\mathbf{X}\mathbf{w}.
$$

Using this fact, we can write:

$$
L(\mathbf{w}) = \mathbf{y}^T\mathbf{y} - 2\mathbf{w}^T\mathbf{X}^T\mathbf{y}
 + \mathbf{w}^T\mathbf{X}^T\mathbf{X}\mathbf{w}.
$$

Now we can take the gradient with respect to $\mathbf{w}$.

$$
\begin{split}
\nabla_{\mathbf{w}}L(\mathbf{w}) &=
\nabla_{\mathbf{w}}\left[\mathbf{y}^T\mathbf{y} - 2\mathbf{w}^T\mathbf{X}^T\mathbf{y}
 + \mathbf{w}^T\mathbf{X}^T\mathbf{X}\mathbf{w}\right]\\
&= -2\mathbf{X}^T\mathbf{y} + 2\mathbf{X}^T\mathbf{X}\mathbf{w}.
\end{split}
$$

Okay, I do admit that I did some derivative magic there.
But the result is correct.
If you really want to understand it, you would have to work out the gradient of the following $\mathbf{w}^T\mathbf{u}$ and $\mathbf{w}^T\mathbf{A}\mathbf{w}$ where $\mathbf{u}$ is a 2-dimensional vector and $\mathbf{A}$ is a $2\times 2$ matrix.

Setting the gradient to zero, yields the following linear system:

$$
\mathbf{X}^T\mathbf{X}\mathbf{w} = \mathbf{X}^T\mathbf{y}.
$$  

The bottom line: to find the best $\mathbf{w}$ you must solve this linear system!
As I will show you in a while, for more complex models that remain linear in the parameters you basically have to do exactly the same thing but with a different design matrix.
By the way, if you work out the analytical solution for a linear model with 2 parameters you will get exactly the expression with the correlation between $X$ and $Y$ we derived in the [previous lecture](lecture14:linear-regression-with-one-variance).
