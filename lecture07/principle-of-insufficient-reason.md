(lecture07:principle-of-insufficient-reason)=
# The principle of insufficient reason

```{epigraph} The theory of chance consists in reducing all the events of the same kind to a certain number of cases equally possible, that is to say, to such as we may be equally undecided about in regard to their existence, and in determining the number of cases favorable to the event whose probability is sought. The ratio of this number to that of all the cases possible is the measure of this probability, which is thus simply a fraction whose numerator is the number of favorable cases and whose denominator is the number of all the cases possible.

-- [Pierre-Simon Laplace](https://en.wikipedia.org/wiki/Pierre-Simon_Laplace)
```

The *principle of insufficient* reason tells us how we should pick probabilities for simple logical propositions before we see any data.
It is often the starting point of any further analysis.
The idea is straightforward.
Take $I$ to be the background information and $A$ be a logical proposition.
Then the principle states:

$$
p(A|I) = \frac{\text{Number of ways}\;A\;\text{can be True under}\;I}{\text{Number of things that can happen under}\;I}.
$$

The idea is best illustrated through examples.

(lecture07:coin-toss)=
## Coin toss experiment
Let's look first at a simple coin toss experiment.
The background information $I$ you typically have is like this:
> Bob has a coin in his pocket. I have no reason to believe that it is biased. Bob puts his hand in his pocket, shakes it for a while, and then makes a fist around the coin. He takes his hand out with the coin hidden in his fist. He then throws the coin up and he lets it fall on the ground and stop moving.

Now take the logical proposition $H$:
> The top face of the coin shows heads.

The principle of insufficient reason tells you what number you should assign to the probability of heads given the information you have.
Since there two possible results and heads is one of them the principle dictates that you should assign probability $1/2$, i.e.,

$$
p(H|I) = \frac{1}{2}.
$$

(lecture07:six-sided-die)=
## Six-sided die
The background information $I$ is:
> Alice has a six-sided die in her pocket. The die is well-balanced. She puts her hand in her pocket, shakes it for a while, and then makes a fist around the die. She takes her hand out with the die in her fist. She throws the die up and she lets it fall on the ground and stop moving.

Take the logical proposition $A_1$:
> The top face of the die shows the number 1.

Since $A_1$ is one of the six events allowed under $I$, then by the principle of insufficient reason you should pick:

$$
p(A_1|I) = \frac{1}{6}.
$$

(lecture07:two-six-sided-dice)=
## Two six-sided dice
Let's make things a bit more complicated by taking two dice.
The background information $I$ is:
> Alice has two six-sided dice in her pocket. The dice are well-balanced and indistinguishable. She puts her hand in her pocket, shakes them for a while, and then makes a fist around the dice. She takes her hand out with the dice in her fist. She throws the dice up and she lets them fall on the ground and stop moving.

Now take the logical proposition $A$:
> The top face of one die shows the number $1$ and the top face of the other die shows the number $2$.

In how many ways can this happen? There are 36 possible outcomes ($36 = 6\times 6$) and out of those the logical proposition $A$ is True two times (either the first die shows $1$ and the second $2$ or the first shows $2$ and the second $1$).
So:

$$
p(A|I) = \frac{2}{36} = \frac{1}{16}.
$$

Let's do one more.
Consider the logical proposition $B$:
> The sum of the top faces of the dice equals $7$.

Again, there are $36$ possibilities under $I$.
We can get a total sum of $7$ in the following $6$ ways:

```{list-table} Outcomes of two six-sided dice experiment that sum to $7$.
:header-rows: 1
:name: dice-outcomes

* - Die 1
  - Die 2
* - 1
  - 6
* - 2
  - 5
* - 3
  - 4
* - 4
  - 3
* - 5
  - 2
* - 6
  - 1
```

So, by the principle of insufficient reason, we can assign:

$$
p(B|I) = \frac{6}{36} = \frac{1}{6}.
$$

(lecture07:principle-of-insufficient-reason:questions)
## Questions

+ What is the probability that sum of two six-sided dice is $5$?
