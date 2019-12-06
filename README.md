## Gomoku: an AI human vs computer game 
This is an implementation of the AlphaZero algorithm for playing the simple board game Gomoku (also called Gobang or Five in a Row) from pure self-play training. The game Gomoku is smilar as Tic-Tac-Toe, which is a game where both players trying to put their “X” or “O” symbol inside a 3 by 3 board. The player wins by having their symbol forming a connection with the length of 3. The connection can be either horizontal, vertical or diagonal. Gomoku is to form a length of 5 inside a 8 by 8 board.

## Key Reinforcement Learning Concepts Used in this project: 
- Monte Carlo Tree Search (MCTS): works similar to Adversarial Search covered in the previous section. The main difference is MCTS randomly choose a branch to go down rather than trying to iterate through all the branches. The algorithm then establishes a profile from the outcome from that branch.
- Q-Learning: is the simplest form of Reinforcement Learning. The goal of Q-Learning is to learn a policy that optimizes the evaluated outcome of the agent.
- Markov decision process:  is a state diagram describing the states and actions of the agents and the environment. It also describes the probability of transition between each states and reward for each state.


### Example Games Between Trained Models
- Each move with 400 MCTS playouts:  
![playout400](https://raw.githubusercontent.com/junxiaosong/AlphaZero_Gomoku/master/playout400.gif)

### Technical Requirements
To play with the trained AI models, only need:
- Python >= 2.7
- Numpy >= 1.11

To train the AI model from scratch，you need: 
- PyTorch >= 0.2.0    
- TensorFlow

### Implementation Steps
To play with provided models, run the following script from the directory:  
```
python human_play.py  
```
You may modify human_play.py to try different provided models or the pure MCTS.

To train the AI model from scratch run:   
```
python train.py
```
To use GPU in PyTorch, set ``use_gpu=True`` and use ``return loss.item(), entropy.item()`` in function train_step in policy_value_net_pytorch.py if your pytorch version is greater than 0.5)

The models (best_policy.model and current_policy.model) will be saved every a few updates (default 50).  


**Trainin Process**
1. We started with a 6 * 6 board and 4 in a row, and obtained a reasonably good model within 500~1000 self-play games in about 2 hours. (Saved policies in the files: best policy 6_6_4 model)
2. Afterwards, we trained the case of 8 * 8 board and 5 in a row, and obtained 2000~3000 self-play games to get a good model. It takes 1-2 days. (Saved policies in the files: best policy 8_8_5 model)

