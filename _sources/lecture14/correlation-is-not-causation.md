(lecture14:correlation-is-not-causation)=
# Correlation is not causation

I do think that that I have to stress this too much on you because you are
engineers!
But let me at least state it once:

> Correlation does not imply causation.

When you have two random variables $X$ and $Y$ and you find that they are
correlated, you cannot tell just from this observation that any of the following is
true:
- $X$ is causing $Y$,
- $Y$ is causing $X$, or that
- $X$ and $Y$ have a common (unobserved) cause $Z$,
- or a myriad of other possibilities.

There is nothing in probability theory or statistics that can help you distinguish
between these three cases.
You need something more.
What more? Well, you need some physical knowledge.

In our example on smart buildings we saw that the external temperature `t_out`
and energy consumption `hvac` were correlated.
From our understanding of the situation, we consider much more likely that
the external temperature affects the energy consumption and not the other way around!

The bottom line is that you cannot do anything useful with data science unless
you augment the models you build with the causal mechanisms you (think) you know.
In the jargon, you have to make your causal assumptions clear.
So, resist the temptation to just apply a technique to get a quick answer.
Think about your problem. Write down what you know.
Write down what you think is the causal mechanism.
And then do data science.

It is actually beyond the scope of this class to teach you how to do this.
Here I am just giving you the very basics.
If you want to learn more, a good starting point is the following keynote
lecture by Judea Pearl (Turing award) on the science of causality:

<iframe width="793" height="446" src="https://www.youtube.com/embed/ZaPV1OSEpHw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
