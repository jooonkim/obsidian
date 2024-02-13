Some core questions:

1. How do we keep our AI agent from making moves that lead to a losing branch?

2. How do we know the best moves? -> Minimax Algorithm

AI games that are most commonly studied are "perfect information" (i.e., fully observable) and "zero-sum" (i.e., what is good for one player is bad for another). We can superimpose *search trees* over a state space graph where the vertices are states, the edges are moves, and a state might be reached by multiple paths. A complete *game tree* is a search tree that follows every sequence of moves towards a *terminal state* (i.e., when the game has ended).
## Minimax Algorithm

The goal is to create an outcome that is "guaranteed" no matter what the other side does. We're assuming that both players are playing optimally here until the end of the game. You are only ever moving one player (yourself). You use "MIN" as an opportunity to *forecast* your opponent's move. You don't make the move in minimax, you simply return your best move.

Suppose your AI agent is the "MAX" and the opponent is "MIN." You can find the *minimax value* of each state in the tree as follows: "The minimax value is the utility (for MAX) of being in that state, assuming that both players play optimally from there to the end of the game." In other words, **the minimax value is its utility**.

**MAX prefers a state of maximum value, and MIN prefers a state of minimum value (that is, minimum value for MAX and thus maximum value for MIN).**

We will propagate wins and losses up a game tree so that a computer player can make a decision. Computing values for nodes from bottom to top. For example, for each max node, pick the maximum value among child nodes.
## Evaluation Functions

The best one is determined after considering the nature of the game and whether it captures the behavior we want to capture. Sometimes you can tune the evaluation function with different weights to influence behavior.

One *Evaluation Function* idea is maximizing the number of open moves for our agent vs. the opponent (as we lose the game when we no longer have any more moves left).
## Branching Factors & Depth Limited Search

Think of branching factor as... how many different move choices on average are possible per move?

We can approximate the number of nodes MINIMAX will need to visit with **b^d** where b is the branching factor, d is the number of nodes.

Only going as far as we think that we can (given our branching factor) is called *Depth Limited Search*. Calling Minimax with a depth limited search can lead to the AI agent choosing a different move choice depending on the depth to which it goes. If the "recommended branches" (the best next moves depending on the depth searched), there might be a critical decision being made at the depth. When the recommended branches don't change much, we're in good shape. This is *Quiescent Search* (basically, until we reach *Quiescence*).

  

## Iterative Deepening

  

*Iterative Deepening*:

1. Go to a certain depth and pick what we think is the best answer.

2. "Keep" that answer.

3. Search again to a deeper depth again and again until we run out of time.

4. Return our best answer

  

When we search for a best move, we only have a certain amount of time. We also don't know how deep we will be able to search in that amount of time. Perhaps the search space is highly branched, meaning we won't be able to search to a target depth without timing out. Perhaps the search space is lowly branched, and we will miss out on an opportunity to search deeper. The value of iterative deepening is that we can store the best move from our search to depth - 1 and then return it when we run out of time.

  

It turns out that a huge portion of the search space, especially for highly branched trees, is made up of leaf nodes. This means that we do not wind up wasting very much time by recalculating internal nodes multiple times.

  

Iterative deepening doesn't waste that much time, surprisingly. It's usually only (branching factor) times the number of nodes a depth-limited search would have done at the same level. It's basically (all the nodes visited from the root to the previous depth in depth limited search) + (all the nodes visited from the root until the new depth in depth limited search). Iterative deepening is "almost free" given the exponential nature of the problem. We ensure that we always have an answer in case we run out of time.

  

*Depth-Limited Search nodes visited at each node*: n = b ^ d + previous levels. If branching factor b, *n = (b^(d+1) - 1)/(b-1)*

  

*Iterative Deepening nodes visited*: < b * n

  

*STRATEGY*

Towards end game, you want to search more deeply because you want to see what would happen. Towards the beginning, branching factor might be quite large. Later on, the branching factor will be reduced in Isolation. Iterative Deepening and Quiescent Search will help us figure out what to do with the limited time we have available.

  
  

## Alpha-Beta Pruning

Alpha-Beta doesn't change the answer of minimax, but it is often much more efficient because it has us prune branches.

  

Our goal is to play the game! Not to keep a list of all the equally good moves on the same level. Assuming we evaluate the branches "from left to right," we can just choose the "leftmost branch." Often, the value of the minimax decision is *independent* of the values of these prunable branches.

  

Alpha–beta pruning gets its name from the two extra parameters in MAX-VALUE(state,α,β) that describe bounds on the backed-up values that appear anywhere along the path:

  

α = the value of the best (i.e., highest-value) choice we have found so far at any choice point along the path for MAX. Think: α = “at least.”

β = the value of the best (i.e., lowest-value) choice we have found so far at any choice point along the path for MIN. Think: β = “at most.”

  

This process keeps track of the best choice for MAX (alpha --> "at least this much utility") and the best choice for MIN (beta --> "at most this much utility").

  

Move ordering = ordering the successors that are likely to be the best, first, so that they can be pruned out. Alpha–Beta with perfect move ordering can solve a tree roughly twice as deep as minimax in the same amount of time.

  

## Asides

AI could be the study of clever hacks to exponential problems. AI is also the collection of NP hard problems that have not yet been solved.