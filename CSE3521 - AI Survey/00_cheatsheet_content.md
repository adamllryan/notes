>[!INFO] Stuff on test
> - Covers up to adversarial search
> - No coding or pseudocoding problems, but maybe reading code problems
> - Will cover cost/benefits of graph tree
> - This sheet must fit on one page 8.5x11 single-sided. 
# Intro Content
AI has 4 goals:

|  | Humanlike | Rationality |  
| -------- | -------- | -------- |  
| Think | Think like people | Think rationally |  
| Act | Act like people | Act rationally |

> [!INFO] Rational means the following:
> - maximize achieving pre-defined goals
> - only consider decisions, not the thought process behind them
> - goals expressed in terms of utility of outcomes
> - maximizing your expected utility

*Turing Test*: Outdated test to determine if AI is successful. A human judge converses with unknown entity (person or an AI) for 5 minutes and if it can fool the judge into thinking it's a human, it passes.  
*Agent Metrics*:
Performance (agent success), Environment (environment variables), Actuators (agent abilities), Sensors (agent perception)
`Rational` means to behave in a very specific way:
*AI Types*: Processing/NLP, Speech recognition, TTS, dialog, computer vision, recognition, scene segmentation, image classification
*Agent Types*: Reflex, planning, goal-based, learning, utility, logical agents
#### Reflex Agent
Choose action based on current percept/memory. No consideration of future consequences. 
#### Planning Agent
Plans ahead and considers future states. 
#### Goal
## Environment Types
*Fully Observable*: Agent can see everything. 
*Partially Observable*: Agent deals with noise, inaccuracy, or incomplete sensors. 
*Single Agent*: Agent plays itself. 
*Multi Agent*: Involves multiple agents. 
*Static*: The world does not change while the agent is thinking. Decision time does not matter!
*Dynamic*: The world is changing while the agent is thinking. Decision time matters!
*Discrete*: Possible states are distinct and/or the world changes discretely. Think integers. 
*Continuous*: Possible states take continuous values. Think floats. 
*Deterministic*: The next state is fully determined by current state and agent action. If sent back to the same state, you can repeat this 100% of the time. 
*Stochastic*: The next state has some element of randomness. There is some uncertainty. 
*Episodic*: Past states are independent of previous ones. 
*Sequential*: States affect later ones
# Uninformed Search
## Search Problem
*Search Problem*: Contains the following. 
*State Space*: A list of every possible state. 
*Successor Function*: Returns all successor states, along with actions and costs. 
*Start State, Goal Test*: The first state the agent starts with, and a function that checks if state is goal state. 
*Solution*: Sequence of actions which transforms the start state to a goal state. 
## State Space Graphs
*State Space Graph*: Tree or graph representation of a search problem
*Nodes*: These are states
*Arcs*: These point to successor states. 
*Goal Test*: Is a set of node(s). 
> [!INFO]
> Each unique state occurs only once! Also we can rarely build a full graph in memory (too big)

A search tree corresponds to a plan to achieve states. We can't revisit previously visited notes. And every node in a search tree is a *path* in the state space graph. Both are constructed on demand. 

# Uninformed search
## DFS
Finds leftmost solution, regardless of cost. Expands left side until end is reached. $O(b^m)$ time complexity, $O(bm)$ space complexity. Complete if we prevent cycles. 
## BFS
Expands shallowest layers first. Complete, optimal if costs are all 1. $O(b^s)$ time, $O(b^s)$ space. 
## Iterative Deepening
DFS but only at one level at a time. Preferred method with large search space and solution depth not known. 
## Uniform cost search
Expand the cheapest nodes first. Create a stack and then while size > 0 remove cheapest and expand. Add successors to stack. $O(b^{C*/\epsilon})$ time and space. Complete and optimal. 
# Informed Search
## Search Heuristic
Heuristic is function that estimates distance to goal. Manhattan is absolute value distance
## Greedy Search
Expand node that is closest to goal. 
## A* Search
Combine UCS and greedy by summing forwards and backwards cost. 
*Admissible Heuristics*: underestimate actual costs
# Adversarial Search
Zero sum games: agents have opposite utilities (pure competition)
General Games: agents have independent utilities ( coop, indifference, competition)
Value of state is not utility of state!
## Minimax
We use minimax in games with alternating turns so we can maximize ours but minimize our opponent's. They have negative or smaller scores. 
## Adversarial Search
Deterministic and zero-sum games are best and our best outcome is if opponent acts rationally. 
Both functions are implemented with v=+/-inf and for each successsor return min/max of opposite function and v. $O(b^m)$ time and $O(bm)$space. We normally need depth limited search, bring in iterative deepening!
We use evaluation functions to replace goal tests when the game does not end. 
## Alpha-Beta Pruning
Starting from beginning, we pass in alpha and beta var. a=-inf and b=inf. min updates b=min(b,v) max updates a=max(a,v) both return +/-inf if a>=b. This cuts down on searches because we know those will never be searched. If left min=3 then we get 2 on next sibling successor, skip rest of sibling because it will never be chosen. 

# Quiz Utility
We want to abstract away details unnecessary to the problem. 
Successor function should: list successor states from actions and list valid actions an agent can perform on current state. 
Search state should include information needed to detect goals and include any information needed for or affected by performing actions. 
Best solution: optimality, solution found: completeness. 
admissible heuristic never overestimates cost remaining, consistent never overestimates the step cost. 
f: eval func, g: current path cost, h: heuristic, f=h greedy, f=g+h A* search
A* allow revisits and use consistent heuristic with closed set. 
AB Pruning does not replace minimax
Terminal test is game end
Agent is max, opponent is min, utility func is current eval