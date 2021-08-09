(lecture07:common-sense)=
# The common sense assumptions that give rise to the basic probability rules.

```{epigraph} Probability theory is nothing but common sense reduced to calculation.

-- [Pierre-Simon Laplace](https://en.wikipedia.org/wiki/Pierre-Simon_Laplace), Théorie analytique des probabilités (1814)
```

Consider the following three ingredients:
+ $A$: a logical proposition about the world,
+ $B$: another logical proposition about the world, and
+ $I$: all the information we know relevant to $A$ and $B$.

We do not impose any other restriction apart that $A$ and $B$ are not contradictions.

We need a bit of notation so that we write less math.
We will use the following conventions:

+ $\text{not}\;A \equiv \neg A$
+ $A\;\text{and}\;B \equiv A, B \equiv AB$
+ $A\;\text{or}\;B \equiv A+B$

Now, let's try to make a robot that can argue under uncertainty.
It should be able to take logical propositions (such as $A$ and $B$ above) and argue about them using all the information it has.
What sort of system should govern this robot?
The following desiderata, see Ch. 2 of {cite}`jaynes03`, seem reasonable:

+ Degrees of plausibility are represented by real numbers.
+ The system should have a qualitative correspondence to common sense.
+ The system should be consistence in the sense that:
   - If a conclusion can be reached in two ways, each way must lead to the same result.
   - All evidence relevant to a question should be taken into account.
   - Equivalent states of knowledge must be represented by equivalent plausibility assignments.

Cox's theorem, see {cite}`VANHORN20033`, shows that:

> The desiderata are enough to derive the mathematical foundations of probability theory.

The theory of probability assigns numbers to mathematical expressions like $p(A|I)$, $p(B|I)$, $p(A|BI)$, etc.

```{important}
We read the expression $p(A|BI)$ as:
+ the probability of A being true given that we know that B and I are true, or
+ the probability of A being true given that we know that B is true, or
+ the probability of A given B.
```

Note that the mathematical theory is not unique.
The is some indeterminacy equivalent to picking probability units.
Of course, we will follow the common assumption of using zero for impossibility and one for certainty.

```{important}
The probability $p(A|BI)$ is a number between zero and one quantifying the degree of plausibility that A is true given B and I.
Specifically:
+ $p(A|B,I) = 1$ when we are certain that A is true if B is true (and I).
+ $p(A|B,I) = 0$ when we are certain that A is false if B is true (and I).
+ $0< p(A|B,I) < 1$ when we are uncertain about A if B is true (and I).
+ $p(A|B,I) = \frac{1}{2}$ when we are completely ignorant about A if B is true (and I).
```
