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
    - The semi greedy player is loosing up around 2000 iterations then steadily improves and eventually plays better than purely greedy player. That should be because purely greedy one memorises bad moves. This could cause it to prioritise the wrong things and optimise getting small rewards in the short term missing out on bigger long term ones.

#### Learning from Exploration: Suppose learning updates occurred after all moves, including exploratory moves. If the step-size parameter is appropriately reduced over time (but not the tendency to explore), then the state values would converge to a set of probabilities. What are the two sets of probabilities computed when we do, and when we do not, learn from exploratory moves? Assuming that we do continue to make exploratory moves, which set of probabilities might be better to learn? Which would result in more wins?

If we perform learning updates even when performing explanatory moves, we will underestimate the actual value of the states we update after exploratory moves. This is because, unless the previous estimates were wrong, the action we pick is actually sub-optimal, and will lead to a worse state than the one we would have reached by exploiting our policy.

Therefore:

- When we perform the updates also for exploration, our probabilities (value function values) will be lower bounds on the optimal ones
- Otherwise, we will have unbiased values

Assuming that we continue to make explanatory moves, it’s better to learn the unbiased ones. If a action that we choose during exploration is actually better than the greedy action, one we explore the state and update it’s value, it could overtake the current best action for state.

Given that the estimates for the values for the first case are biased, they would perform at least as bad as the unbiased estimates. I’m not totally sure if the bound would be strict or not.

    