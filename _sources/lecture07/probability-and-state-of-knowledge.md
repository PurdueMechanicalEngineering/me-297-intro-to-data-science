(lecture07:probability-state-of-knowledge)=
# Probability as a representation of our state of knowledge

Probability theory allows us to quantify our uncertainty about stuff.
The "stuff" can be anything.
From the weather to the cracks on a bevel gear, to the structural health of an extraterrestrial habitat, to the predictions of physical models, to the validity of mathematical theories, to any statement about the world.
Paraphrasing the title of {cite}`jaynes03`, *probability theory is the logic of science*.

## Types of uncertainty
In general, we are uncertain about something if we don't know much about it.
Uncertainty may be *aleatory* or *epistemic*.
The difference between the two are is as follows:
+ Aleatory uncertainty is associated with irreducible randomness.
+ Epistemic uncertainty is associated with lack of knowledge.

You can potentially reduce epistemic uncertainty if you are willing to pay the price, e.g., by collecting more data, building a new sensor, doing a better analysis of the data.
There is nothing you can do about aleatory uncertainty.

It is easy to find examples of epistemic uncertainty.
So I take a coin, I put my hands behind my back, I put the coin in one of my hands, I close my fists, and I bring my hands forward so that you can see them.
You do not know where the coin is.
But the coin is in one of my hands. There is nothing random here.
In the same spirit, suppose that some piece of a mechanical system, say the radiator of a cooling system, may or may not have paint damage.
Again, there is nothing random. You just do not know what is its state.

Aleatory uncertainty is a bit trickier.
Take the classic example of a coin toss.
Many people think that coin tosses are random.
What do you think?
Watch this video by [Persi Diaconis](https://en.wikipedia.org/wiki/Persi_Diaconis) the Stanford mathematician (and former professional magician):
<iframe width="640" height="360" src="https://www.youtube.com/embed/AYnJv68T3MM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

So, there is nothing random about coin tosses.
With what you learn in ME 274 (Basic Mechanics II) you are able to describe the dynamics of the coin using Newton's and Euler's equations and you can predict exactly what is going to happen in a coin toss experiment if you know the initial conditions.
The uncertainty about the result of the coin toss is not aleatory.
It is epistemic uncertainty, lack of knowledge about what the initial conditions are.

You have to search hard for true aleatory uncertainty.
Perhaps, the closest you can get is if you look at very small things.
So small that quantum effects start being important.
Many physicists believe that at this most fundamental level, nature is inherently random.
Watch this video on the double slit experiment by [Jim Al-Khalili](https://en.wikipedia.org/wiki/Jim_Al-Khalili) a theoretical physisists from the University of Surrey in the UK:
<iframe width="640" height="360" src="https://www.youtube.com/embed/A9tKncAdlHQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Good. So, at small scales there may be aleatory uncertainty.
But then again, there is [Quantum Bayesianism](https://en.wikipedia.org/wiki/Quantum_Bayesianism)...

So, there is a long and ongoing philosophical debate about the distinction between aleatory and epistemic uncertainty.
We are going to ignore it.
Probability theory is sufficient to describe both types uncertainties and that the distinction in many cases is not important.

## How does the theory look like?

Let's call $I$ all the *information* you have at this given moment.
And I am talking about absolutely everything: what your parents taught you, what you learned in school, what you learned so far in college, any data you may have seen.
Now consider a, well-defined, logical proposition $A$ that says something about the world.
For example, $A$ could be:
+ The result of the next coin toss John performs will be heads.
+ On 7/1/2021, the average temperature in West Lafayette, IN, will be greater than 70 degrees F.
+ The radiator of the cooling system has paint damage.

We want a mathematical theory that can turn all the information $I$ we have into a real number that tells us how plausible it is that $A$ is true.
This is what probability theory does.
It gives us this number.
Call it $p(A|I)$ and read it as "the probability that $A$ is true given that we know $I$."
Let's see what is all about.

```{important}
$$
p(A|I) = \text{the probability that}\;A\;\text{is true given that we know}\;I,
$$

where
+ $A$ is a logical proposition about the world, and
+ $I$ is all the information you have relevant to $A$.
```
