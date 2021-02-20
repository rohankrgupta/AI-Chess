# Chess AI

This project focuses on computer science concepts such as data structures and algorithms. Chessnut is the chess engine we are using for all the moves and chess logic. We are utilizing a tree to generate the possible chessboards 3 levels deep and depth first search, minimax, and alpha-beta pruning to find the best move based on the following heuristics:

* material (total piece count for each player)
* number of possible legal moves with emphasis on center squares
* check/checkmate status
* pawn structure

Currently trying to implement multiprocessing as our recursive function uses a lot of computing power so calculating heuristics on board states more than 4 levels deep takes a lot of time. With a depth of 3 leves, our AI makes pretty good moves but also makes a lot of ill-advised ones as well. The AI's chess intelligence is estimated to be at a level 3 out of 9.

![Chess AI Terminal Screenshot](https://github.com/jameslim1021/Chess-AI/blob/master/screenshots/chessai.png)


## Minimax Algorithm

Borrowing from Wikipedia's concise definition, the [minimax algorithm](https://en.wikipedia.org/wiki/Minimax) is "a decision rule used ... for minimizing the possible loss for a worst case (maximum loss) scenario." With respect to chess, the player to act is the maximizer, whose move would be met with an adversarial response from the opponent (minimizer). The minimax algorithm assumes that the opponent is competent and would respond by minimizing the value (determined by some heuristic) of the maximizer.

## Alpha-Beta Pruning

Because of the number of board states possible in chess (estimated to be [10^120](https://en.wikipedia.org/wiki/Shannon_number)), minimax can be improved with a layer of [alpha-beta pruning](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning). By keeping track of alpha (the highest value guaranteed to the maximizer) and beta (the lowest value guaranteed to the minimizer), it is possible to avoid calculating the heuristics of certain board states that cannot improve the situation for the current player.

## Heuristics

There are many factors when calculating the heuristics of a chessboard. As we developed our heuristic formula to consider more factors, the computations required to calculate the best move increased exponentially. At the moment, the AI considers the following 4 aspects of a board in its heuristic function.

### Material
The material heuristic compares the value of one's pieces with the opponent's pieces. It encourages the AI to capture pieces and make favorable trades. We used the standard values for each piece:
* Pawn: 1
* Bishop/Knight: 3
* Rook: 5
* Queen: 9

### Number of Moves
This heuristic calculates the number of legal moves a player can make. It encourages the AI to develop its pieces to exert more control over the board. It prioritizes controlling the center where pieces will have more options to influence the game. For example, a queen near the center of the board can move in 8 directions and thus control more squares, whereas a queen on a corner square can only move in 3 directions.

### Pawn Structure
The pawn structure heuristic gives a score based on the number of pawns supported by other pawns. It encourages the AI to develop its pawns in a way that allows pawns moving forward to be defended by other pawns from behind.

### Check Status
This heuristic checks if a player is in check or checkmate status. It encourages the AI to make moves that would put the opponent in check while avoiding moves that would put itself in check. It also detects if a move would put opponent in checkmate, which would be prioritized over all other heuristics.


## Acknowledgments

* cgearheart's [Chessnut](https://github.com/cgearhart/Chessnut)
* Aleks Kamko's [Alpha-Beta Pruning Practice](http://inst.eecs.berkeley.edu/~cs61b/fa14/ta-materials/apps/ab_tree_practice/)
