# Draughts-AI

## Introduction

The game of checkers is considered a complicated game with $10^{20}$ possible legal positions in the English draughts version (8\*8 board) alone (much more on higher dimensions). In this attempt to create a game agent, a tree traversal approach has been used. This approach is not only fast but also efficient given that better heuristics are used. We have created an agent which is capable of playing the game of draughts or checkers with a remarkable win rate against average players. Draughts is a 1vs1 zero-sum game. Minimax or Minimax algorithm is best suited for such types of games. Following is the development procedure we practised during the development of the project.

1. Implemented a basic Minimax Agent with limited depth.
2. Applied ⍺-β pruning.
3. Improved the evaluation functions.

Initially, we considered many approaches to the implementation of this agent. Here is a report of them:
Reinforcement Learning agent. This would have been impractical and very complex to construct as there are $10^{20}$ different states possible of the 8×8 board.
Since this is a zero-sum game with 2 players playing 1 on 1, the minimax algorithm was the best suited for this purpose. We then designed the evaluation function.

<table>
    <tr>
        <td><img src="imgs/checker_gif_1.gif" alt="AI vs Player I"></td>
        <td><img src="imgs/checker_gif_4.gif" alt="AI vs Player II"></td>
    </tr>
    <tr>
        <td><img src="imgs/checker_gif_7.gif" alt="AI vs Player I"></td>
        <td><img src="imgs/checker_gif_8.gif" alt="AI vs AI II"></td>
    </tr>
</table>

## Evaluation Functions

We have used 2 types of evaluation functions depending upon the state of the game. These are mid evaluation and end game evaluation function. Following is the report for the same.
Here we list all the evaluation functions:

### Mid Evaluation

#### Piece to Value

$∑(Pi) + 2×∑(Ki) - ∑(OPi) - 2×∑(OKi)$

Where $P_i$ and $OPi$ are the player’s and Opponent’s Pawns and $Ki$ and $OKi$ are the player’s and Opponent’s Kings respectively.

#### Piece and Board part to value

${5∑(PHPi) + 7∑(EHPi) + 10×∑(Ki)} - {5∑(PHOPi) + 7∑(EHOPi) + 10×∑(OKi)}$

Where $PHPi$ and $PHOPi$ are the player’s and Opponent’s Pawns in their own respective halves and $EHPi$ and $EHOPi$ are their Pawns in their respective enemies’ halves.
$Ki$ and $OKi$ are the player’s and Opponent’s Kings respectively.

#### Piece and Row to value

${ ∑[5(Pi) +ri ]+ ∑[ 7(Ki) + ri ] } - { (∑[5(OPi) + rj] + ∑[7(OKi) + rj]}$

Where $Pi$ and $OPi$ is the player’s and Opponent’s Pawns and $Ki$ and $OKi$ are the player’s and Opponent’s Kings respectively. $rj$, $ri$ are the row number of the respective piece.

#### Piece and Board part to value (modified)

${5∑(PHPi) + 7∑(EHPi) + 10×∑(Ki)} - {5∑(PHOPi) + 7∑(EHOPi) + 10×∑(OKi)}/n$

Where $PHPi$ and $PHOPi$ is the player’s and Opponent’s Pawns in their own respective halves and $EHPi$ and $EHOPi$ are their Pawns in their respective enemies’ halves. $Ki$ and $OKi$ are the player’s and Opponent’s Kings respectively.
$n$ is the number of pieces on the board.

### End Evaluation:

#### Sum of Distances

$Dij$ = Distance of ith King of player from jth King of the enemy.
$S = ∑ni = 1 ∑nj = 1 Dij$

Minimise S if more number of pieces than opponent else maximise .

### Farthest Piece

$Dij$ = Distance of ith King of player from jth King of the enemy.

$Dmax = max(∑nj = 1 Dij)$

Minimise Dmax if more number of pieces than opponent else maximise.

## Conclusion

1. Heuristics can be drastically improved by adding specific features.
2. The depth of the game tree has a significant influence on the quality of the computer player.
3. There's a tradeoff between calculation time and quality of the game.
4. It is not efficient to use Minimax without optimizations while with them it can be a good solution.
5. Alpha-Beta pruning is exponentially improving in comparison to Minimax as the depth grows.
6. Certain heuristics are clearly better than others but some of the “bad” ones still work well in some cases.

## Contributing

Found a bug? Create an **[issue](https://github.com/Hsankesara/Draughts-AI/issues/new)**.
