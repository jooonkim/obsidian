*A systematic way of representing probabilistic independence and conditional independence relationships in the world. You take concepts of uncertainty & probability and marry it with efficient computation.* 

**Bayes Network**: a compact representation of a distribution over a joint probability distribution of variables. 

Once you specify a Bayes Network, and you observe, then you can compute variables you cannot observe!

Classic example of a Bayes Network is (A) -> (B) where A is not observable and B is observable. There are child nodes and parent nodes. An arc indicates that the parent node influences the child node. However, the parent nodes influence the child nodes in a *probabilistic* way, not a *deterministic* way.

If you came up with the B.N. in a different order, you might have a different graph. Humans are the ones who make the graph structures, machines are the ones that compute probabilities.

## Calculating Joint Distribution of Bayes Network
Suppose A, B are the parent nodes of C, and C is the parent node of D, E. Then,
$$(PA, B, C, D, E) = P(A) * P(B) * P(C|A, B) * P(D | C) * P(E | C)$$
Joint distributions might require exponential space, but Bayesian Networks give a *factorization of the joint probability distribution that will generally allow us to store them compactly with far fewer parameters.*

We could have needed $2^5 - 1 = 31$ parameters, but now we only really need about $10$. Every variable with $k$ parent nodes requires $2^k$ probability values.

The Bayes Network scales significantly better! This is a key advantage of Bayes Networks.

## D Separation
When you are evaluating the independence of $A$ and $B | C$, ask yourself, "would my knowledge of $C$ cause $A$ to influence $B$ ?" 

Generally if $C$ is an intermediary node (parent to child to grandchild) between $A$ and $B$ in a Bayes Net, the answer is likely no.

One interesting case: $A$ and $B$ are parent nodes of the same node $C$. Then, $A$ is *not independent* of $B|C$ due to the **explain away effect** (if we know $C$ to be true, knowledge of $A$ will substantially affect our beliefs about $B$). 

D Separation is best studied with:
- *Active Triplets*: Render the variables dependent (if all variables are unknown, or if two unknown variables converge on a child node or future successor that is known)
- *Inactive Triplets*: Render the variables independent (if the intermediary variable is known, or if two unknown variables converge on a child node that is unknown)




