# Reinforcement Learning Note

## [Deep Q Networks on Cartpole](https://pytorch.org/tutorials/intermediate/reinforcement_q_learning.html)
- state, action, next state, reward
  - These are materials for training
- For each iteration or one move of the cart
  - save the quad into a pool
- The deep learning network
  - Input: state
  - Output: each output-layer neuron output represents 
    the estimated reward under one possible action  
  - We maintain two networks:
    - policy_net: what is trained all the time
    - target_net: to get the ideal Q, it is updated after each epoch
- For each training step
  - Randomly get a batch of quads from the pool
  - Q_real is the sum of policy_net outputs corresponding to the actions
  - Q_ideal is got from next state and reward by means of the Bellman Equation:
    - Q = reward + gamma * max(target_net(next state))
  - Optimization is to minimize the difference between Q_real and Q_ideal
- One training epoch is from the beginning to the end of this game
- Finally:
  - Given one state, we give out one suggested action (the one with higher value).