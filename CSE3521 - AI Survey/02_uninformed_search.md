# Search

## Agents that plan ahead

Planning agents need to answer what if questions. They make decisions based on hypothesized consequences and need a `model` of how the world evolves in response to actions. Must also formulate a `goal test`.

There is a difference between [optimal] and [complete] planning.

These agents need to formulate a solution to an offline version of the problem in a simulated or imaginary environment. This offline problem has a goal test/desired state to achieve that is not necessarily always the same as the real problem. The goal is to find a sequence of actions that can achieve the goal with a better optimal cost/performance measure/utility. They then execute the action sequence in the real environment. May also need to replan action after analyzing the state change.

## Search Problems

A [search problem] consists of a state space, successor function (a new state based on actions and costs), and a start state with goal test. A [solution] is a sequence of actions (a plan) which transforms the start state to the goal state.

## State Space

A [state space] contains a `world state` that includes every detail of the environment and a `search state`.
A `search state` keeps only the details needed for planning the next move, aka abstraction.

Slide 7 contains two examples of pathing and eat-all-dots problems state spaces.

# Uninformed Search

There are a few ways to conduct an uninformed search:

- depth-first search
- breadth-first search
- uniform-cost search

These are just search trees lol

## State space graphs

A state space graph is a mathematical representation of a search problem. Nodes are states, arcs represent successors, and the goal test is a set of goal nodes (could be just one too).

In a state space graph, each unique state can only occur once! Additionally, it is rare we can build the full graph in memory because of its size.

## Search Trees

A search tree is a what if tree of plans with the outcomes of actions. The start state is the root node and children are successors. Each [node] shows a state but correspond to `plans` that achieve those states. For most problems, we can never actually build the whole tree. But it is good for concepts!

Nodes are not states but partial plans! They are paths that the agent can take.

A state space graph is a [node] of a search tree. Each tree contains a state space graph in every node. A unique sttate can show up at multiple nodes in a search tree, however each node in the tree is a unique plan. Both are constructed on demand, in order to save resources. Lots of repeats in the structure of a search tree.

## Tree search

We need a plan to systematically search a tree and find solutions.

A [search] expands out to find potential plans (nodes) and maintains a fringe of partial plans under consideration. The goal should be to expand as few tree nodes as possible.

## General tree search

A tree search function will return a solution or failure.

Function Loop:

1. If there are no candidates for expansion, return false.
2. Choose a [leaf node] for expansion according to strategy.
3. If the [node] contains a goal state, return the corresponding solution, otherwise expand the node and add the resulting nodes to the search tree.
4. Continue.

## Uninformed vs. Informed search

Uninformed search does not have any information about the problem other than its definition. It can only find solutions by systematically visiting new states and testing for the goal.

An informed search is given some ideas of where to look for solutions. It uses problem specific knowledge to solve the problem!

### Depth-first search

A search strategy that always wants to examine the newest stuff first. Find the deepest node first. Implemented as a [LIFO stack].

Issues: always finds the left-most solution regardless of depth or cost. Also can infinitely loop if cycles are not prevented.

### Breadth-first search

A search strategy that will always check the nodes on the same level before checking the deeper levels. Implemented as a

Issues: expensive

### Uniform cost search
