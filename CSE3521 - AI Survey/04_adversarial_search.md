>[!NOTE]
> This is incomplete. It was decently written at first, so I have not done another pass at it yet. 
# Multiple Agent Games

When agents are placed together, they can either participate in zero-sum or general games. 
If agents have opposite utilities, they are playing by **zero-sum** rules. In this scenario, agents have opposite utilities and must compete to maximize theirs while minimizing their opponents'. 
Alternatively, **general games** are when agents have independent utilities. This can allow for cooperation, indifference, competition, and more. 

If utility cost is accumulated, our solution is the goal state. In this case, our solution should focus on having the *minimum cost*. We should use A* or UCS, and we want to aim for faster times than brute force. 
If it isn't, our solution is the terminal state. Now, we focus on finding the solution with the *max utility*. We should explore all paths to terminal states. 

Now, we will refer to the value of a state as the best achievable outcome or utility from that given state. It represents the best possible score we can get given that position. 

# Adversarial Search

Adversarial search (A\*) uses the sum of uninformed and informed search to find the best move in a game. It is a combination of minimax and alpha-beta pruning.

## Minimax

**Minimax** is a recursive algorithm that is used to choose an optimal move for a player assuming that the opponent is also playing optimally. It is used in two-player games such as tic-tac-toe, checkers, chess, go, and so on.

The algorithm searches the game tree starting from the current state and generates all possible moves for the player and the opponent. It then evaluates each of these moves using a heuristic function and chooses the move with the highest score for the player and the lowest score for the opponent.

Adversarial search is optimal when the game is deterministic, fully observable, two-player, zero-sum, and turn-taking.

It will take the sum of the heuristic function with the backwards cost of the path to the node. The heuristic function is the estimated cost of the path from the node to the goal. The backwards cost is the cost of the path from the node to the start.

1. Begin with a max function. 
2. Max function will pick the largest successor value. 
3. Each successor is calculated recursively with a min function. 
4. Min function finds the smallest successor value. 
5. This repeats, with the min function using a max function to find the largest.

## Alpha-Beta Pruning

**Alpha-beta pruning** is an optimization technique for minimax that reduces the number of nodes that are evaluated by the minimax algorithm in its search tree. It is called alpha-beta pruning because it uses two values, alpha and beta, to determine when to prune branches in the search tree.

Because minimax alternates min and max functions, we can actually prune off many sibling nodes in a function. Say we are conducting a min search and at a level, the first node searched yields a value 7. Now we check the second sibling. Of all the sibling's successors, if any have a min smaller than 7 (or equal to), we can immediately discard the whole sibling from the search because we know that it now has a min smaller than its left sibling, and the max function above will pick the left sibling anyways. Similarly, if we are conducting max search at a level, and that left node is 7 (for example), if we find a sibling with a larger successor node than 7 we can discard that sibling because the parent min level will want the smallest successor only. 

Terms:

- g - backwards cost
- h - forward cost (heuristic function or greedy search)
- f - total cost (g + h)

## Deterministic Games
State space is S, starts from $s_0$
Players: Agents

Terminal test: sometimes opponent wins and you fail. terminal test checks success whether or not you win or not. Indicates end of path, not just you have reached the end of a path, where it may be the goal state or not. If you can only end by winning, we use goal test, otherwise it is called terminal test. 