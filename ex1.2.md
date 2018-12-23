## Reference implementation of the Tic-Tac-Toe Value Function Learning Agent
### "Reinforcement Learning: An Introduction" Chapter One: Sutton and Barto, 2018

#### Symmetries Many tic-tac-toe positions appear different but are really the same because of symmetries. 
- How might we amend the learning process described above to take advantage of this? 
- In what ways would this change improve the learning process? 
    - The time taken to learn the values reduces and space required to store the values reduces. This is because for each value, the experience generated from all corresponding symmetric states are being used to update that value, and hence we can expect faster convergence (when compared to the case where symmetries are being ignored).

- Now think again. Suppose the opponent did not take advantage of symmetries. In that case, should we? 
- Is it true, then, that symmetrically equivalent positions should necessarily have the same value.