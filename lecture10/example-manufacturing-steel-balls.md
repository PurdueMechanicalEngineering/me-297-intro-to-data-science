(lecture10:example-manufacturing-steel-balls)=
# Example: Uncertainties in steel ball manufacturing

Steel balls are an essential component of ball bearings, an essential component
of axles in bikes, cars, etc.
Watch this video to see how they are manufactured:

<iframe width="500" height="281" src="https://www.youtube.com/embed/19duYMdiXi0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

It is very important to tightly control the properties of the ball, e.g.,
diameter and steel density.
Any slight variation increases undesired vibrations and as a consequence results
in noise and faster degradation of ball bearings.

How do you characterize the manufacturing uncertainty on steel ball properties?
Well, you can use continuous random variables for that.
For example $X$ could be the random variable that gives you the diameter of a
ball (assuming they are perfectly spherical - they are not).

Assume that we know that the balls have a diameter that is greater than 0.95 mm
and smaller than 1.05 mm.
What sort of random variable should we assign to the diameter?
Let's call this random variable $X$.
We know a few things right away about it.
First, $X$ cannot be smaller than 0.95 mm.
So:

$$
p(X < 0.95\;\text{mm}) = 0.
$$

Second, $X$ cannot be greater than 1.05 mm.
So:

$$
p(X > 1.05\;\text{mm}) = 0.
$$

Then, we also know that $X$ should be between 0.95 mm and 1.05 mm.
That is:

$$
p(0.95\;\text{mm} \le X \le 1.05\;\text{mm}) = 1.
$$

All, this is trivial.
Is there anything non-trivial we can say?
Take a diameter $x$ from 0.95 mm to 1.05 mm and consider a small window
$\Delta x$ around it.
What is the probability that $X$ takes values between $x$ and $x+\Delta x$?
Mathematically, what is $p(x \le X \le x + \Delta x)$?
For this particular example, it makes sense to assume that
$p(x \le X \le x + \Delta x)$ is proportional to $\Delta x$:

$$
p(x \le X \le x + \Delta x) = c \Delta x,
$$

where $c > 0$ is a proportionality constant.
The bigger $\Delta x$ is, the higher the probability.
What is the proportionality constant?
You can find the proportionality constant by considering an extreme case.
Pick $x=0.95\;\text{mm}$ and $\Delta x = 0.1\;\text{mm}$.
Then:

$$
c \cdot 0.1\;\text{mm} = p(0.95\;\text{mm} \le X \le 1.05\;\text{mm}) = 1,
$$

from which we get that:

$$
c = 10\;\text{mm}^{-1}.
$$

The constant $c$ is some sort of density.
It gives you how much probability you get per unit of $x$.
In this particular case, the probability density is just a constant (i.e., it
  does not depend on $x$).
However, in general it may be depend on $x$ and then we call it a
*probability density function*.
We will talk about probability density functions in a while.

If you have the probability density, you can find any probability regarding $X$ you want.
For example, the probability that $X$ is between 1 mm and 1.03 mm is:

$$
\begin{split}
p(1\;\text{mm} \le X \le 1.03\;\text{mm}) &=
p(1\;\text{mm} \le X \le 1\;\text{mm} + 0.03\;\text{mm})\\
&= c\Delta x\\
&= 10\;\text{mm}^{-1}\cdot 0.03\;\text{mm}\\
&= 0.3.
\end{split}
$$

Here is another one.
Say that you want to find the probability that $X$ is smaller than 0.99 mm or
greater than 1.03 mm. How do you do that?
Well, here it is:

$$
\begin{split}
p(X < 0.99 \;\text{mm}\;\text{or}\;X > 1.03\;\text{mm}) &=
1 - p(0.99\;\text{mm} \le X \le 1.03\;\text{mm})\\
&= 1 - p(0.99\;\text{mm} \le X \le 0.99\;\text{mm} + 0.04\;\text{mm})\\
&= 1 - 10\;\text{mm}^{-1}\cdot 0.04\;\text{mm}\\
&= 1 - 0.4\\
&= 0.6.
\end{split}
$$

Finally, let's consider the function that gives you the probability that $X$ is
smaller than a value $x$.
Mathematically this:

$$
F(x) = p(X \le x).
$$

This has a special name.
It is called the *cumulative distribution function*.
We will examine its properties in detail as well in subsequent sections.
But for now, let's see how it looks like for our particular example.
Pick an $x$ smaller than 0.95 mm.
Then, we should have $F(x) = 0$ because $X$ cannot take values that are so small.
What about an $x$ greater than 1.05 mm.
Then, we should have $F(x) = 1$ because $X$ takes for sure values that are smaller
than 1.05 m.
Now for an $x$ between 0.95 mm and 1.05 mm, we have:

$$
\begin{split}
F(x) &= p(X \le x)\\
&= p(0.95\;\text{mm}\le X \le 0.95\;\text{mm} + (x-0.95\;\text{mm}))\\
&= 10\;\text{mm}^{-1}\cdot (x-0.95\;\text{mm}).
\end{split}
$$

Putting everything together, we find:

$$
F(x) = p(X\le x) = \begin{cases}
0,&\;\text{if}\;x<0.95\;\text{mm},\\
10\;\text{mm}^{-1}\cdot (x-0.95\;\text{mm}),&\;\text{if}\;0.95\;\text{mm}\le x\;1.05\;\text{mm},\\
1,&\;\text{otherwise}.
\end{cases}
$$

You can use the cumulative distribution function to find probabilities about $X$.
Of course, $F(x)$ is the probability $p(X\le x)$.
But you can also use it to find the probability that $X$ is greater than $x$.
Here is how:

$$
\begin{split}
p(X > 1.02\;\text{mm}) &= 1 - p(X\le 1.02\;\text{mm})\\
&= 1 - F(1.02\;\text{mm})\\
&= 1 - 10\;\text{mm}^{-1}\cdot (1.02\;\text{mm}-0.95\;\text{mm})\\
&= 1 - 10\;\text{mm}^{-1}\cdot 0.07\;\text{mm}\\
&= 1 - 0.7\\
&= 0.3.
\end{split}
$$

Okay. Time to define the concepts properly.
