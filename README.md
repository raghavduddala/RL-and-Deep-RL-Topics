# RL-and-Deep-RL-Topics
This repository will have all the explanations and the intuition behind different RL and Deep RL Algorithms

##### Replay Buffer:
replay buffer to sample out experiences from Episodes to remove out any correlations that are induced by a temporally related data and to make the data for the Neural networks to be IID.

#### DQN: Deep Q-Network
--> This is essentially Q-Learning with Deep Learning, also uses a Replay Buffer

#### DPG: Deterministic Policy Gradient
DPG can be used for Continuous action and state space but the problem is that it is very unstable and may not always converge which is really not useful for practical robotic applications



#### DDPG: Deep Deterministic Policy Gradient
--> DDPG is essentially a deterministic policy gradient algorithm where the policy gradient is calculated using neural networks as the function approximators, hence the name Deep Deterministic Policy Gradient. 
--> The Critic in DDPG is essentially a DQN(Deep Q Network) which pre-processes 
--> The actor(Policy Gradient) 
--> Both DPG and DDPG can handle continuous State space and Continuous action space, but DPG is unstable and DDPG is stable(i.e the value (Q-value) converges)
--> Target networks are used to avoid divergence in the "Q -value" since the same network will be used both for updating the Q- value and also to preprocess for action(a), hence the problem is avoided using a different network with same initial weights and then slowly updating them using soft updates(averaging method) such that stability is ensured. The weights update for the target networks is constrained to be very slower than the actual critic and actor networks.
--> Without HER, DDPG either requires an established reward function and cannot work with Sparse and Binary Rewards or the sample complexity is really very large. (low sample efficiency)

#### HER : HindSight Experience Replay.
--> Generally, even DDPG uses a replay buffer to sample out experiences from Episodes to remove out any correlations that are induced by a temporally related data produced in a Off-Policy Setting.(Since, generally the Deep Learning architecture deals with data that is IID Independent and Identically Distributed). 

--> The "HER" builds on using the Experience Replay along with an intuition such that the results/experiences from failed experiences are also used in the learning process. HER maps the end state achieved to a "achieved goal" instead of the end goal(in other words, hence providing some sort of feedback regarding the rewards in relation with the state transitions achieved and the specific actions taken.

-->  In a multi-goal setting RL control problem, the policy is a mapping from both the state and the goal to an action. This implies that the goal is also written in a state transition tuple such as (s_t, r, s_t+1, a_t, G) where G is the original desired goal, but in a HER setting the state transition tuples are stored such as (s_t, r, s_t+1, a_t, G') where G'(achieved goal) is the last state in the episode and the reward is then computed with respect to the achieved goal (i.e the last state achieved at the end of the episode). All these new state transition tuples are stored in the experience replay buffer and are used in the learning process. 

--> Because of the above changes and additional data from HER  it has the following effect: 
"At first, the agent will be able to reach states in a relatively small area around the initial state, but gradually it expands this reachable area of the state space until finally it learns to reach those goal states we are actually interested in."
Words in Quote from the article: https://towardsdatascience.com/reinforcement-learning-with-hindsight-experience-replay-1fee5704f2f8
