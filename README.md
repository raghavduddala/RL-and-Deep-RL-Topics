# RL-and-Deep-RL-Topics
This repository will have all the explanations and the intuition behind different RL and Deep RL Algorithms

#### DPG: Deterministic Policy Gradient
DPG 



#### DDPG: Deep Deterministic Policy Gradient
--> DDPG is essentially a deterministic policy gradient algorithm where the policy gradient is calculated using neural networks as the function approximators, hence the name Deep Deterministic Policy Gradient. 
--> The Critic in DDPG is essentially a DQN(Deep Q Network)
--> The actor(Policy Gradient)
--> Both DPG and DDPG can handle continuous State space and Continuous action space, but DPG is unstable and DDPG is stable(i.e the value (Q-value) converges)
--> 
--> Without HER, DDPG either requires an established reward function and cannot work with Sparse and Binary Rewards or the sample complexity is really very large. (low sample efficiency)

#### HER : HindSight Experience Replay.
--> Generally, even DDPG uses a replay buffer to sample out experiences from Episodes to remove out any correlations that are induced by a temporally related data produced in a Off-Policy Setting.(Since, generally the Deep Learning architecture deals with data that is IID Independent and Identically Distributed). 

--> The "HER" builds on using the Experience Replay along with an intuition such that the results/experiences from failed experiences are also used in the learning process. HER maps the end state achieved to a "achieved goal" instead of the end goal(in other words, hence providing some sort of feedback regarding the rewards in relation with the state transitions achieved and the specific actions taken. 
