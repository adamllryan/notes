# Adversarial Search

Adversarial search (A\*) uses the sum of uninformed and informed search to find the best move in a game. It is a combination of minimax and alpha-beta pruning.

## Minimax

Minimax is a recursive algorithm that is used to choose an optimal move for a player assuming that the opponent is also playing optimally. It is used in two-player games such as tic-tac-toe, checkers, chess, go, and so on.

The algorithm searches the game tree starting from the current state and generates all possible moves for the player and the opponent. It then evaluates each of these moves using a heuristic function and chooses the move with the highest score for the player and the lowest score for the opponent.

Adversarial search is optimal when the game is deterministic, fully observable, two-player, zero-sum, and turn-taking.

It will take the sum of the heuristic function with the backwards cost of the path to the node. The heuristic function is the estimated cost of the path from the node to the goal. The backwards cost is the cost of the path from the node to the start.

1. Begin with a max function. 
2. Max function will pick the largest successor value. 
3. Each successor is calculated recursively with a min function. 
4. Min function finds the smallest successor value. 
5. This repeats, with the min function using a max function to find the largest.

## Alpha-Beta Pruning




Terms:

- g - backwards cost
- h - forward cost (heuristic function or greedy search)
- f - total cost (g + h)

## Admissible Heuristics

An admissible heuristic is a heuristic that never overestimates the cost of the path from the node to the goal. It is used in A\* search to find the optimal path from the start to the goal.

## Alpha-Beta Pruning

Alpha-beta pruning is an optimization technique for minimax that reduces the number of nodes that are evaluated by the minimax algorithm in its search tree. It is called alpha-beta pruning because it uses two values, alpha and beta, to determine when to prune branches in the search tree.
