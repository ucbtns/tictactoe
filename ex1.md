## Reference implementation of the Tic-Tac-Toe Value Function Learning Agent
### "Reinforcement Learning: An Introduction" Chapter One: Sutton and Barto, 2018


#### Symmetries: Many tic-tac-toe positions appear different but are really the same because of symmetries. 
- How might we amend the learning process described above to take advantage of this? 
    - Instead of updating just the given board state update all symmetries, ie. rotation reflection combinations. 

- In what ways would this change improve the learning process? 
    - The time taken to learn the values reduces and space required to store the values reduces. This is because for each value, the experience generated from all corresponding symmetric states are being used to update that value, and hence we can expect faster convergence (when compared to the case where symmetries are being ignored).

- Now think again. Suppose the opponent did not take advantage of symmetries. In that case, should we? 
    - Although the symmetrically equivalent positions should have the same value ideally, in case the opponent did not take advantage of symmetries we should also not since there might be better ways of exploiting this, ie adapt to play of opponent for more wins.

- Is it true, then, that symmetrically equivalent positions should necessarily have the same value.
    - No. Consider the case where the opponent does not make use of symmetries. Assuming an imperfect
opponent, we can consider two states a and b which are symmetrically equivalent. Now, assume
that the actions taken by the opponent when in these two states is not symmetrically equivalent.
For example, in state a, the opponent may play a sound move, but in state b, the opponent
may make a mistake that can be exploited by us. Thus, to be able to best respond to the
opponents imperfection as in the above case, it would be beneficial for us to maintain separate
values for the states a and b even though they are symmetric.

#### Greedy Play: Suppose the reinforcement learning player was greedy, that is, it always played the move that brought it to the position that it rated the best. 

- Might it learn to play better, or worse, than a nongreedy player? What problems might occur?
    - The semi greedy player is loosing up around 2000 iterations then steadily improves and eventually plays better than purely greedy player. That should be because purely greedy one memorises bad moves.
    