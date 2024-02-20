## Informed Search

**Informed search** differs from [[02_uninformed_search#Uninformed Search|uninformed search]] in the way that we now are given some ideas of where to look for solutions and we can use problem-specific knowledge. We use [[03_informed_search#Search Heuristic|search heuristics]] to help us get to our goal state faster.

## Search Heuristic

A **heuristic** is a function that is able to estimate the distance of a state to a goal. We are in charge of implementing it ourselves.

We use Heuristics to guide the search process. Heuristics are problem-specific knowledge that provide hints about where a solution is likely to be found. Heuristics are used to evaluate nodes in the search tree and decide which node to expand next.  
Heuristics are forward-looking, i.e., they estimate the cost of reaching the goal from the current state.

A heuristic should **NEVER OVERESTIMATE, ALWAYS UNDERESTIMATE** the forward-looking cost.

A common heuristic in determining path is just returning the distance between the current node and the goal node. Often called greedy search.

## Greedy Search

**Greedy search** is where we expand a node that we think is closest to the goal state. With greedy search, our worst case is just depth-first search and our best case is more common where you are taken to the goal.

## A\* Search

A\* search is a general algorithm for finding a path in a graph between two nodes. It is the basis of many search algorithms for many problems, including problems in artificial intelligence, and operations research.

It sums [[02_uninformed_search#Uninformed Search|uniform-cost search]] and [[03_informed_search#Greedy Search|greedy-search]] and moves to the node with the lowest sum cost out of all the nodes in the queue. In other words, it takes the sum of the travel cost and heuristic cost, and then performs UCS. It is the combination of forwards and backwards cost.

A\* is optimal! Best case it takes you straight to the goal, but worst case is it just becomes uniform-cost search.

## Admissible Heuristics

An **admissible heuristic** (optimistic heuristic) is a heuristic that never overestimates the cost of reaching the goal, i.e., the cost it estimates to reach the goal is not higher than the lowest possible cost from the current point in the path. A heuristic is *admissible* if $0\leq h(n) \leq h^*(n)$ for all n, where $h^*(n)$ is the true cost to reach the goal state from n.  
Admissible heuristics can slow down bad plans but not outweigh the true costs.

A heuristic is **consistent** (or monotonic) if $h(n) <= c(n, a, n') + h(n')$ for all $n$, $n'$, where $c(n, a, n')$ is the cost of taking action $a$ in state $n$ to reach state $n'$.

When dealing with A* search, we should allow revisits and use a consistent heuristic w/ a closed set to avoid revisits.
