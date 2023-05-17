# SmartContract-RockPaperScissior


This is a smart contract that allows two players to play a game of Rock-Paper-Scissors. The contract is deployed by a manager, who specifies the playing time, revealing time, address of the first player and the address of the second player, and assigns the reward of the game in the value field.

How to Play
-The first player inserts his move (rock, paper, scissors) and nonce (32-hex value) in the function prepareMove() and then calls the function.
-The player then assigns a deposit in the value field and copies the output of prepareMove() and inserts it in makeMove() and calls the function.
-The second player performs steps 2,3.
-If the playing time ended now the revealing time just started.
-The first player reveals his hashed move by inserting his move (rock, paper, scissors) and the nonce inserted in prepareMove() in the form of the following: [paper], [0x4554480000000000000000000000000000000000000000000000000000000000].
-The second player performs step 7.
-The 2 players receive their deposits after calling the reveal function if hash of the nonce and the move inserted is equal to the hashed move inserted in makeMove().
-The 2 players wait till the end of revealing time.
-The manager calls the function GameEnd() after the end of revealing time and transfer the reward to the players according to the result.
-Winner variable can be called to check the address of the winner of the game.
-If there is no winner and the 2 players inserted the same moves, then the address output of Winner will be 0.
-getContractBalance() is updated after each money transfers(when the manager assigns the reward in the beginning and when the players assign their deposits) and can be called at any time of the run to check the current contract balance.


Code Limitations
-The value of the reward must be even so that it can be divided when the players insert the same moves.
-The manager cannot insert 2 identical player addresses when deploying the contract.
-The players must insert a correct move. Correct moves include (Rock, rock, ROCK, …).
-The manager cannot deploy the contract without assigning a reward in the beginning in the value field.
-GameEnd must be called only once.
-If a player is dishonest, he will lose the deposit and the deposit will go to the manager.
-The output of the reveal function must be the same as the input of prepareMove().
-If one of the players is dishonest and inserted dishonest input in reveal() the other player will be the winner automatically if he is honest and the deposit of the dishonest player will go to the manager.
-The reward will be transferred back to the manager if the 2 players are dishonest.
-The reward will be transferred back to the manager if one of the players is dishonest and the other one didn’t show up.
-The reward will be transferred back to the manager if the 2 players didn’t show up.
-prepareMove(), makeMove(), reveal() are called by each player only once.
-The players must stick to the time limitations of the game. They are not allowed to call reveal() before the end of the playing time or call makeMove() after the end of the playing time.
-The manager only has to call GameEnd() only after the end of the revealing time.
-The 2 players must make a deposit in the beginning.
-Only the 2 players whom addresses specified by the manager in the beginning of the contract are eligible to play.
-When the reward is transferred back to the manager, the winner address is 0.


Conclusion
This is a simple smart contract that allows two players to play a game of Rock-Paper-Scissors. The contract is easy to use and can be deployed by anyone.
