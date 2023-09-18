# Informed Search

## Heuristic Search

We use Heuristics to guide the search process. Heuristics are problem-specific knowledge that provide hints about where a solution is likely to be found. Heuristics are used to evaluate nodes in the search tree and decide which node to expand next.
Heuristics are forward-looking, i.e., they estimate the cost of reaching the goal from the current state. A common heuristic always overestimates the cost, should never underestimate the forward-looking cost.

# Uninformed Search Recap

algorithm is given some ideas of where to look for solutions. given problem-specific knowledge.

## Graph Search

Graph search is a general algorithm for finding a path in a graph between two nodes. It is the basis of many search algorithms for many problems, including problems in artificial intelligence, and operations research.

NOTE: We ban repeated states in graph search. This is because repeated states can cause infinite loops. We also want to never expand a state twice.

## Iterative Deepening and Graph Search

Iterative deepening is a state space search strategy in which a depth-limited search is run repeatedly with increasing depth limits until the goal is found. It is equivalent to breadth-first search but uses much less memory; on each iteration, it visits the nodes in the search tree in the same order as depth-first search, but the cumulative order in which nodes are first visited is effectively breadth-first.

It is not optimal with graph search!

# General Tree search

General tree search is a general algorithm for finding a path in a tree between two nodes. It is the basis of many search algorithms for many problems, including problems in artificial intelligence, and operations research.

**The search stops when you dequeue/expand a goal state, not when you queue it.**

## Search Heuristics

**A heuristic is a function that estimates the cost of reaching the goal from the current state.**
A common heuristic in determining path is just returning the distance between the current node and the goal node. Often called greedy search.

## Greedy Search

We expand a node that we think is closest to the goal state. Worst case is just depth-first search, best case is more common where you are taken to the goal.

## A\* Search

A\* search is a general algorithm for finding a path in a graph between two nodes. It is the basis of many search algorithms for many problems, including problems in artificial intelligence, and operations research.

It sums uniform-cost search and greedy-search and moves to the node with the lowest sum cost out of all the nodes in the queue.

A\* is optimal! Best case it takes you straight to the goal, but worst case is it just becomes uniform-cost search.

## Admissible (optimistic) Heuristics

An admissible heuristic is a heuristic that never overestimates the cost of reaching the goal, i.e., the cost it estimates to reach the goal is not higher than the lowest possible cost from the current point in the path.
A heuristic is **admissible** if `0 <= h(n) <= h*(n) for all n`, where h*(n) is the true cost to reach the goal state from n.
${h(n) \leq h^*(n)}$

## Consistent (monotonic) Heuristics

A heuristic is **consistent** if `h(n) <= c(n, a, n') + h(n') for all n, n'`, where c(n, a, n') is the cost of taking action a in state n to reach state n'.
