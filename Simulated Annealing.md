
*A probabilistic technique for approximating the global optimum.*

  

Comes from the concept of annealing in metallurgy, which heats and cools a material to alter physical properties.

  

## Context

  

Hill Climbing Search is a greedy local search. These algorithms often perform quite well because they can make rapid progress towards solutions. However, hill climbing gets stuck at:

1. Local Maxima

2. Ridges

3. Plateau

  

Sometimes you can do *random-restart hill climbing*, which is complete (if a goal exists, it will be found eventually). It conducts a series of hill-climbing searches from randomly generated initial states until a goal is found.