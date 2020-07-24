# Tic-Tac-Toe
An implementation of Minimax AI Algorithm on Tic-Tac-Toe (or Noughts and Crosses) game. 

Try it: https://tictactoe0215.herokuapp.com

Features:

    o	Player can choose to play between 2 player (vs. human) and 1 player (vs. AI) mode.
    o	Player can choose which token they want to play with(X or O).
    o	Player can choose between 2 difficulty levels in single player mode, Easy and Hard(unbeatable).
    
 How To Play:
 
•	The objective of Tic Tac Toe is to get three in a row.Players alternate placing Xs and Os on the game board until either opponent has three tokens in a row or all nine squares  are filled.
           
Minimax Algorithm

Minimax is a type of adversarial search algorithm for generating and exploring game trees. It is mostly used to solve zero-sum games where one side’s gain is equivalent to other side’s loss, so adding all gains and subtracting all losses end up being zero.Minimax algorithm keeps playing the turns of both player and the opponent optimally to figure out the best possible move.
 
 
 JavaScript implementation of Minimax algorithm:
 

    function minmax(newGrid, depth, playTurn) {
    const gameState = checkGameState(newGrid);
    if (gameState == false) {
    const values = [];
    for (var i = 0; i < 3; i++) {if (window.CP.shouldStopExecution(1)) break;
      for (var j = 0; j < 3; j++) {if (window.CP.shouldStopExecution(2)) break;
        const gridCopy = _.cloneDeep(newGrid);
        if (gridCopy[i][j] !== '') continue;
        gridCopy[i][j] = playTurn;
        const value = minmax(gridCopy, depth + 1, playTurn === player ? comp : player);
        values.push({
          score: value,
          location: [i, j] 
          });
          
      }window.CP.exitedLoop(2);
    }window.CP.exitedLoop(1);
    if (playTurn === comp) {
      const max = _.maxBy(values, v => {
        return v.score;
      });
      if (depth === 0) {
        return max.location;
      } else {
        return max.score;
      }

    } else {
      const min = _.minBy(values, v => {
        return v.score;
      });
      // console.log(min);
      if (depth === 0) {
        return min.location;
      } else {
        return min.score;
      }
    }

      } else if (gameState === player) {
    return depth - 100;
     } else if (gameState === comp) {
    return 100 - depth;
     } else if (gameState === null) {
    return 0;
      }
    }


