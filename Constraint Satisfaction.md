*Unary Constraints*: One variable's value is constrained.

*Binary Constraints*: At most two variables are constrained.

## Backtracking Search

Backtracking Search uses recursion. A couple ways to improve efficiency and minimize backtracking:

1. The *Least Constraining Variable* chooses the value that rules out the fewest values among the other variables (have to consider what the other regions can take as values).

2. The *Minimum Remaining Values* chooses the variable with the fewest legal values left, subject to the constraints.

3. The *Degree Heuristic* chooses the variable first with the most constraints on the other remaining variables (e.g. a territory that bounds the most other territories, when you are trying to color the regions).

4. *Forward Checking* is like an early warning system that the search is going down the wrong branch. You need to keep track of remaining legal values for each unassigned variable, so that you can stop the search and back up if you notice that any variable has no more remaining legal values. But this isn't enough...

  

## Arc Consistency

A variable in a constraint satisfaction problem is *arc consistent* with respect to another second variable if there is a value still available to the second variable after assigning a value to the first variable.

  

If all variables in a graph satisfy this definition, then the network is *arc consistent*.

  

## Structured Constraint Satisfaction Problems

Can we decompose problems into several independent problems?

  

If there are no loops, we can pick any variable to be the root of the tree, and choose an ordering of the variables s.t. each variable appears after its parent in the tree. We start at the leaves, move up to the parent, and make each parent arc consistent (or report failure). Then we can assign values to the variables going back down (given that we know that it's arc consistent).

  

You can also "turn" graphs into trees by *conditioning*, e.g., assigning values to sub-variables and removing those values from the possibilities of its neighbors (e.g., assigning a value to South Australia and removing that possible value from its neighbors).