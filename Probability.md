Probability is important because there is a lot of uncertainty in AI.

## Important Formulas

**Conditional Probability**: The probability of $Y$ given $X$ is equal to the joint probability $P(X,Y)$ (aka the intersection) divided by $P(X)$ 

$$P(Y | X ) = P(X, Y) / P ( X)$$

**Total Probability**: The probability of any random variable $Y$ is equal to the probability of $Y$ given that another random variable $X = i$ multiplied by the probability that $X = i$ .

$$ P(Y) = \sum_{i} P (Y | X = i) * P(X = i) $$

**Negation of Probabilities**: Note that this doesn't work for the negation of the "denominator"!!!
$$P(\neg X | Y) = 1 - P(X | Y)$$
**Bayes Rule**: where $P(A|B)$ is the *posterior*, $P(B | A)$ is the *likelihood*, $P(A)$ is the *prior*, $P(B)$ is the *marginal likelihood*, 

$$P(A | B) = \frac{P(B | A) * P(A)}{P(B)}$$

Put another way:

$$P(A | B) = \frac{P(B | A) * P(A)}{P(B) = \sum_{a} P (B | A = a) * P(A = a)}$$
Bayes Rule turns upside down the *diagnostic reasoning* (from evidence to its causes) into *causal reasoning* (if we knew the cause, what would be the probability of the evidence we just observed?)

## Bayes Networks
They take concepts of uncertainty & probability and marry it with efficient computation.

Classic example of a Bayes Network is (A) -> (B) where A is not observable and B is observable.



There are child nodes and parent nodes. An arc indicates that the parent node influences the child node. However, the parent nodes influence the child nodes in a *probabilistic* way, not a *deterministic* way.

**Bayes Network**: a compact representation of a distribution over a joint probability distribution of variables.

Once you specify a Bayes Network, and you observe, then you can compute variables you cannot observe!



