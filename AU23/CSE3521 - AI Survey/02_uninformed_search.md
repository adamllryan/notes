Before a [[01_agent_design#Agent Types|planning agent]] makes a real action, it simulates its actions in an offline, fake environment. This fake scenario has a **goal test**, which is the measure of how well a sequence of actions would expectedly achieve a solution. It is not always the same as the problem. 

## Search Problem

Note the difference between **complete** (the solution) and **optimal** (complete and most efficient). 

A **search problem** encapsulates the following:
- **state space**, containing the world state, which holds every detail about the environment and a search state, which holds only details needed to plan the next move. 
- **successor function**, which stores a tree of possible actions associated with costs. 
- **start state**, or our initial state. 
- **goal test**, which is a state(s) or function that, once reached, lets us know that we have reached a solution.  
A **solution** is a sequence of actions or a plan that transforms the start state to a goal state. 

A state space is the set of all possible states that can be achieved. 

**State space graphs** are a mathematical representation of a search problem, where nodes are states and arcs are successors. Note that in a state space graph, every unique state may only occur once. Goal test is a node or set of goal nodes. Because of how many possible states there are, it is often difficult or impossible to build the whole graph in memory. 

**Search trees** are a way to represent state space graphs in a way that lets us solve the problem. The root node is our start state and we want to travel down until we reach a/all goal nodes. Similarly, we can almost never build the whole search tree. Each node in a search tree is made up of a whole path in the state space graph. This means that we can see duplicate states, but never the same plan!

For both state space graphs and search trees, we construct them *on demand* and as little of them as possible. 

## Tree Search

How do we systematically build and explore a search tree? We can start by defining a few goals and requirements:
- Must start at the root.
- Expand as few nodes as possible.
- Store partial plans that are under consideration.
- Know when to stop searching. 

There are a few ways to conduct an uninformed search:

- depth-first search
- breadth-first search
- uniform-cost search

A tree search function will return a solution or failure. Here is the algorithm for a general tree search:

~~~
Function Loop:
1. If there are no candidates for expansion, return FALSE.
2. Choose a LEAF NODE for expansion according to strategy.
3. If the NODE contains a goal state, return the corresponding solution, otherwise expand the NODE and add the resulting NODES to the search tree.
4. Continue.
~~~

## Uninformed Search

Uninformed search is the first area of focus. **Uninformed search** means that we search *without information* to the problem and are only able to find solutions by systematically visiting new states and testing for the goal. Alternatively, [[03_informed_search|informed search]] is the approach where we are given some ideas of where to look for solutions. It uses problem specific knowledge to solve the problem!

We have 3 main uninformed search algorithms: 
- Depth-first. 
- Breadth-first. 
- Uniform cost. 

**Depth-first search** is a search strategy that always wants to examine the newest stuff first. Find the deepest node first. Implemented as a last in, first out *stack*. It comes with the issues of always finding the left-most solution regardless of depth or cost. It also can infinitely loop if cycles are not prevented.

Analysis of DFS:
- $O(b^m)$ time complexity where b is the number of nodes and m is the number of levels iterated through. 
- $O(bm)$ space. 
- Complete if cycles are prevented. 
- Not optimal because it finds only the leftmost solution, regardless of cost. 

**Breadth-first search** is the search strategy that will always check the nodes on the same level before checking the deeper levels. Implemented as a first in, first out *queue*. It only comes with the issue of being expensive, because we have to visit every node. 

Analysis of BFS:
- $O(b^s)$ time complexity where b is the number of nodes and s is the shallowest solution level. 
- $O(b^s)$ space complexity. 
- It is complete, optimal if costs are all 1. 

What if we want to get the best of both worlds? We can use iterative deepening where we run DFS but cancel after we hit a certain depth, increasing that as we don't find solutions. It's wasteful, but most of the work is normally in the deepest level, so it's not so bad. This is preferred when we have a large search space and no known solution depth!

**Cost** refers to how expensive it is to travel between two nodes. So far, we have been pretending every link has the cost of 1. What if we need to handle state space graphs with different costs?

**Uniform Cost Search** handles cost by expanding the cheapest node! Note that UCS must expand the cost of the whole path from start, not just the cheapest traversal. In other words, it processes all nodes with a lower cost than the cheapest solution. 

Analysis of UCS:
- $O(b^{C^*/\epsilon})$ where $C^*$ is the cheapest solution and $\epsilon$ is the arc cost (space and time). 
- It is complete if there is a finite cost solution and minimum arc cost > 0. 
- It is also optimal. 

Note that the only difference between all of these is the way we add and remove nodes! We can implement the same search algorithm but use a queue, stack, and priority queue for breadth-first, depth-first, and uniform cost search respectively. 

## Graph Search

With tree search, we need to identify repeated states or else we could end up with lots of extra work (or even infinite loops). This is due to creating our tree from a graph that may contain recurrences. Here is a general set of rules to abide by so that we can avoid this:
- Never expand a state twice. 
- Before expanding a state, check a list of visited nodes and make sure that we have never been to this state. 
- Store this as a set, not a list. 

Graph search uses the same algorithm as [[02_uninformed_search#Tree Search|tree search]], but with a few changes:
~~~
NEW: create visited set
Function Loop:
1. If there are no candidates for expansion, return FALSE.
2. Choose a LEAF NODE for expansion according to strategy.
3. If the NODE contains a goal state, return the corresponding solution.
4. NEW: If NODE not in visited set, add to visited set then expand, and add children to search tree. 
5. Continue.
~~~
We can sometimes optimize this by not adding already visited nodes to the search tree *at all*. This doesn't work for some algorithms, though (like [[03_informed_search#A * Search|A* Search]]). 

Analysis:
- Smaller time complexity than before
- Exponential space but limited by state space size. Only bad with DFS.
- Same as before. 

With graph search, iterative deepening is not optimal. We don't care, though, because of the memory cost with graph search and DFS. 
