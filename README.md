# Chess AI

This project focuses on computer science concepts such as data structures and algorithms. Chessnut is the chess engine I am using for all the moves and chess logic. I am utilizing a tree to generate the possible chessboards 3 levels deep and depth first search, minimax, and alpha-beta pruning to find the best move based on the following heuristics:

* material (total piece count for each player)
* number of possible legal moves with emphasis on center squares
* check/checkmate status
* pawn structure

Currently trying to implement multiprocessing as our recursive function uses a lot of computing power so calculating heuristics on board states more than 4 levels deep takes a lot of time. With a depth of 3 leves, our AI makes pretty good moves but also makes a lot of ill-advised ones as well. The AI's chess intelligence is estimated to be at a level 3 out of 9.

![Chess AI Terminal Screenshot](https://github.com/rohankrgupta/AI-Chess/blob/main/Screenshot%20from%202021-02-20%2014-47-46.png)


## Minimax Algorithm

Borrowing from Wikipedia's concise definition, the [minimax algorithm](https://en.wikipedia.org/wiki/Minimax) is "a decision rule used ... for minimizing the possible loss for a worst case (maximum loss) scenario." With respect to chess, the player to act is the maximizer, whose move would be met with an adversarial response from the opponent (minimizer). The minimax algorithm assumes that the opponent is competent and would respond by minimizing the value (determined by some heuristic) of the maximizer.

## Alpha-Beta Pruning

Because of the number of board states possible in chess (estimated to be [10^120](https://en.wikipedia.org/wiki/Shannon_number)), minimax can be improved with a layer of [alpha-beta pruning](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning). By keeping track of alpha (the highest value guaranteed to the maximizer) and beta (the lowest value guaranteed to the minimizer), it is possible to avoid calculating the heuristics of certain board states that cannot improve the situation for the current player.


## Acknowledgments

* cgearheart's [Chessnut](https://github.com/cgearhart/Chessnut)
* Aleks Kamko's [Alpha-Beta Pruning Practice](http://inst.eecs.berkeley.edu/~cs61b/fa14/ta-materials/apps/ab_tree_practice/)
