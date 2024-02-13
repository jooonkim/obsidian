  

**Breadth First Search** is guaranteed to find the shortest path in terms of *number of steps*, but not in terms of *total cost*. That is **Uniform Cost Search** (aka cheapest cost search).
  

**Depth First Search** is not *complete* like **BFS** and **UCS** are. The reason why is that assuming an infinite tree, **BFS** and **UCS** will eventually reach the goal state G, assuming it has a finite cost for UCS. However, for **DFS**, there is a risk that it will continue to go down an infinite path (all the way down the tree).

  

Similarly, **BFS** and **UCS** are *optimal* unlike *DFS* in that they are guaranteed to find a solution with the shortest path (for BFS) and with the lowest total cost (for UCS).

  

**A * search** could be called "best estimated total path first search." It's like starting with the straight line distance.

### Uniform Cost Search

  

Uniform Cost Search is really just a special case of A* search in some ways. However, UCS is an **uninformed search**, relying solely upon path costs (don't have any heuristics for a node's location).
### A* Search

  

Euclidean distance is an admissible + consistent heuristic.

*Admissible heuristic*: the estimated cost must be lower than or equal to the true cost. It is optimistic in that it never overestimates the cost.

h(a, b) <= g(a, b) where h is the heuristic and g is the true cost. A* is guaranteed to find the lowest cost if h(s) < true cost == h never overestimates == h is optimistic == h is admissible.

  

f(n) = g(n) + h(n) where g(n) is the path cost from the initial state to node n, and h(n) is the estimated cost of the shortest path from n to a goal state. So, f (n) = estimated cost of the best path that continues from n to a goal.

  

With an inadmissible heuristic, A* may or may not be cost-optimal.
### Bi-Directional UCS

  

There are 2 strategies.

#### Strategy 1:

You are alternating frontiers, doing one step with the forward frontier, and one step with the backwards frontier.

  

#### Strategy 2:

Lowest Cost / Highest-Priority First.

  

Everything about bi-directional and tri-directional is about knowing when to stop. Am I stopping too early?

  

Think about the stopping conditions for bi-ucs. Even when you find a path that connected the start to the goal, you can't stop until you can prove that no other path could possibly exist at a lower cost than the path you found.

  

To extend the idea from AIMA to weighted graphs, we can take the explored set into consideration. When an element is in the explored set, we have found the shortest path to the element (depending on the definition of shortest path for that particular algorithm). We can thus use this idea. When performing searches from either side, we can wait until the explored sets intersect. When they do, we would have found the shortest path to the intersecting point from both the start and the goal nodes. Therefore, combining the two should gives us the overall shortest path.

  
  

Stopping criterion: min(forward) + min(reverse) > shortest_path_in_graph

  

Any manner of expanding frontiers is OK

• Alternating both frontiers – good for parallel computing

• Taking the min – good in weighted graphs where hubs have high cost