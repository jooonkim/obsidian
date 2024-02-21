*Traditional AI is very logic-driven, but Modern AI is very probability-driven.*

Probability is important because there is a lot of uncertainty in AI. Probability statements are made with respect to a *knowledge state*, not with respect to the "real world." 

- We say “The probability that the patient has a cavity, given that she has a toothache, is 0.8.” If we later learn that the patient has a history of gum disease, we can make a different statement: “The probability that the patient has a cavity, given that she has a toothache and a history of gum disease, is 0.4.” If we gather further conclusive evidence against a cavity, we can say “The probability that the patient has a cavity, given all we now know, is almost 0.” Note that these statements do not contradict each other; each is a separate assertion about a different knowledge state.

The **Qualification Problem** (aka, the "potato in the tailpipe" problem for when your car doesn't start): one event may have so many causes that it's impossible to enumerate all of them.
- See also: The **Ramification Problem**: one cause has too many innumerable effects
- 
## Important Formulas

**Conditional Probability**: The probability of $Y$ given $X$ is equal to the joint probability $P(X,Y)$ (aka the intersection) divided by $P(X)$ 

$$P(Y | X ) = P(X, Y) / P ( X)$$

**Total Probability**: The probability of any random variable $Y$ is equal to the probability of $Y$ given that another random variable $X = i$ multiplied by the probability that $X = i$ .

$$ P(Y) = \sum_{i} P (Y | X = i) * P(X = i) $$
*Useful corollary:*
$$P(A | B) = P(A | B, C) * P(C) + P(A| B, \neg C)* P(\neg C)$$

**Negation of Probabilities**: Note that this doesn't work for the negation of the "denominator"!!!
$$P(\neg X | Y) = 1 - P(X | Y)$$
**Bayes Rule**: where $P(A|B)$ is the *posterior*, $P(B | A)$ is the *likelihood*, $P(A)$ is the *prior*, $P(B)$ is the *marginal likelihood*, 

$$P(A | B) = \frac{P(B | A) * P(A)}{P(B)}$$

Put another way:

$$P(A | B) = \frac{P(B | A) * P(A)}{P(B) = \sum_{a} P (B | A = a) * P(A = a)}$$
*Useful corollary:*
$$P((X, Y) | Z) = P(X | (Y, Z)) * P(Y | Z)$$

Bayes Rule turns upside down the *diagnostic reasoning* (from evidence to its causes) into *causal reasoning* (if we knew the cause, what would be the probability of the evidence we just observed?)

### Diagnostic vs. Causal
Bayes' rule is useful because it enables diagnostic inference!

From Norvig: "The conditional probability $P(effect|cause)$ quantifies the relationship in the **causal** direction, whereas $P(cause|effect)$ describes the **diagnostic** direction. In a task such as medical diagnosis, we often have conditional probabilities on causal relationships. The doctor knows $P(symptoms|disease)$ and wants to derive a diagnosis, $P(disease|symptoms)$."

## Conditional Independence
In a Bayes Network where A "causes" B & C, then given A, B & C are conditionally independent of one another.

$$P(B | A, C) = P(B | A)$$
$$P(C | A, B) = P(C | A)$$
**The general definition of conditional independence is that:**
$$P(X, Y | Z) = P(X | Z) * P(Y | Z)$$

This doesn't mean that B & C are independent of each other if we don't know A. Let's say B & C are two "tests" for cancer. We know that B is positive. That would make us predict that A is more likely to be cancerous, and that would mean that C is more likely to be positive.

*A & B can be conditionally independent with respect to C and still absolutely independent. A & B can be absolutely independent and still considitionally independent with respect to C.*

**Conditional Independence does not imply Independence**

**A useful formula here is:**

$$ 𝑃(𝑌|𝑋,𝑍)𝑃(𝑋|𝑍)=\frac{𝑃(𝑋,𝑌,𝑍)}{𝑃(𝑋,𝑍)}\frac{𝑃(𝑋,𝑍)}{𝑃(𝑍)}=\frac{𝑃(𝑋,𝑌,𝑍)}{𝑃(𝑍)}=𝑃(𝑋,𝑌|𝑍).$$



### Non-Normalized Probabilities
You can compute Bayes Rule differently by basically ignoring the "normalizer."

We know:
$$P(A | B) = \frac{P(B | A) * P(A)}{P(B)}$$
We also know:
$$P(\neg A | B) = \frac{P(B | \neg A) * P(\neg A)}{P(B)}$$
The normalizer $P(B)$ is identical! Also, we know:
$$P(A | B) + P(\neg A | B) = 1$$
So, we can create "fake probabilities":
$$P'(A | B) = P(B | A) * P(A)$$
$$P'(\neg A | B) = P(B | \neg A) * P(\neg A)$$
Then we can recover the original probabilities:
$$P(A | B) = η  P'(A|B)$$
$$P(\neg A | B) = η  P'(\neg A|B)$$
where "eta" the normalizer is: 
$$ η = \frac{1}{P'(A | B) + P'(\neg A | B)} $$
These pseudo-probabilities can get us the correct answer!
