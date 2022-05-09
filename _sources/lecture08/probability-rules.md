(lecture08:probility-rules)=
# The basic rules of probability

There are two rules of probability from which everything else can be derived.
These are direct consequences of the desiderata and Cox's theorem (see {ref}`lecture07:common-sense`).
They are:

+ The **obvious rule**:

$$
p(A|I) + p(\neg A|I) = 1.
$$

+ The **product rule** (or Bayes' rule):

$$
p(AB|I) = p(A|BI)p(B|I).
$$

I call it the first rule the "obvious rule" because it is obvious...
It states that either $A$ or its negation $\neg A$ must be True.
That's trivial.
A logical proposition about the world is either True or False.[^footnote1]
Let me stress again that it is vitally important that you do not try to apply probability in a system that includes contradictions.

[^footnote1]: However, according to [Gödel's incompleteness theorem](https://en.wikipedia.org/wiki/Gödel%27s_incompleteness_theorems) there some mathematical statements that are neither True nor False.
These are also excluded.

The product rule is not obvious.
Understanding it requires a bit of meditation.
It states that the probability of A and B is the probability of A given that B is True times the probability that B is True.
We can use the Venn diagram of {numref}`venn-diagram` to understand what it all means.

```{figure} venn.png
:height: 250px
:name: venn-diagram

Venn diagram showing the information $I$, and the logical propositions $A$ and $B$.
```

You can think of a Venn diagram as a 2D representation of everything that can happen in the world.
Each point inside the blue area is a possibility allowed by the information $I$.
The red area marks the possibilities in which $B$ is True and the green area marks the possibilities in which $A$ is True.
The intersection of the red and the green area (brown) marks the possibilities in which both $A$ and $B$ are True.

In Venn diagrams probabilities correspond to normalized areas.
It goes like this:

$$
p(\text{something} | \text{something else}) = \frac{\text{area of intersection of something and something else}}{
  \text{area of something else}}.
$$

Strictly speaking, this is not an equality but a correspondence or analogy.
In our particular case, we have:

$$
\begin{array}{ccc}
p(B|I) &=& \frac{\text{area of intersection of}\;B\;\text{and}\;I\;\text{(red)}}{\text{area of}\;I\;\text{(blue)}}\\
&=& \frac{\text{area of}\;B\;\text{(red)}}{\text{area of}\;I\;\text{(blue)}}.
\end{array}
$$

Similarly:

$$
\begin{array}{ccc}
p(A|BI) &=& \frac{\text{area of the intersection of}\;A\;\text{and}\;\text{B and}\;I\;\text{((brown)}}{\text{area of intersection of}\;B\;\text{and}\;I}\\
&=& \frac{\text{area of the intersection of}\;A\;\text{and}\;\text{B (brown)}}{\text{area of}\;B\;\text{(red)}},
\end{array}
$$

and

$$
p(AB|I) = \frac{\text{area of intersection of}\;A\;\text{and}\;\text{B (brown)}}{\text{area of}\;I\;\text{(blue)}}.
$$

Thus, we have:

$$
\begin{array}{ccc}
p(AB|I) &=& \frac{\text{area of intersection of}\;A\;\text{and}\;\text{B (brown)}}{\text{area of}\;I\;\text{(blue)}}\\
&=&\frac{\text{area of intersection of}\;A\;\text{and}\;\text{B (brown)}}{\text{area of}\;I\;\text{(blue)}}\cdot
\frac{\text{area of}\;B\;\text{(red)}}{\text{area of}\;B\;\text{(red)}}\\
&=&
\frac{\text{area of intersection of}\;A\;\text{and}\;\text{B (brown)}}{\text{area of}\;B\;\text{(red)}}\cdot
\frac{\text{area of}\;B\;\text{(red)}}{\text{area of}\;I\;\text{(blue)}}\\
&=& p(A|BI)p(B|I),
\end{array}
$$

which is the product rule.
Keep in mind that this is not a mathematical proof.
However, it can help you develop a little bit of intuition about the product rule.
