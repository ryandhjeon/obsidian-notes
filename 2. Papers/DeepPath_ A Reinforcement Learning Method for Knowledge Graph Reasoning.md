# DeepPath: A Reinforcement Learning Method for Knowledge Graph Reasoning
#### (2017) - Wenhan Xiong, Thien Hoang, William Yang Wang
#### University of California, Santa Barbara
**Link**: http://aclweb.org/anthology/D17-1060
**DOI**: 10.18653/v1/D17-1060
**Code/Link**:
**Tags**: #paper #KG/Reasoning
**Rating**:

### Abstract

```
We study the problem of learning to reason in large scale knowledge graphs (KGs). More specifically, we describe a novel reinforcement learning framework for learning multi-hop relational paths: we use a policy-based agent with continuous states based on knowledge graph embeddings, which reasons in a KG vector space by sampling the most promising relation to extend its path. In contrast to prior work, our approach includes a reward function that takes the accuracy, diversity, and efficiency into consideration. Experimentally, we show that our proposed method outperforms a path-ranking based algorithm and knowledge graph embedding methods on Freebase and Never-Ending Language Learning datasets.
```

### Notes

- To handle complex queries where there are no obvious answers, intelligent machines must be able to reason with existing resources, and learn to infer an unknown answer.

- [[Path-Ranking Algorithm]] ([[PRA]]) emerges as a promising method for learning inference paths in large KGs.
	- Uses a random-walk with restarts based inference mechanism to perform multiple bounded depth-first search processes to find relational paths. Coupled with elastic-net based learning, PRA then picks more plausible paths using supervised learning.

- We propose a novel approach for **controllable multi-hop reasoning**: we frame the path learning process as reinforcement learning (RL).
	- In contrast to PRA, we use translationbased knowledge based embedding method to encode the continuous state of our RL agent, which reasons in the vector space environment of the knowledge graph.

- [[Neural symbolic machine]] ([[NSM]]): KG reasoning using RL. It learns to compose programs that can find answers to natural language questions. 

- **GOAL of multi-hop relation reasoning**: To find reliable predictive paths between entity pairs.


#### Reinforcement Learning for Relation Reasoning

**PART 1**: 
- The external environment E which specifies the dynamics of the interaction between the agent and the KG.
- Markov Decision Process (MDP)
- Tuple <S, A, P, R> is defined.
	- S: Continuous state space
	- A: A = {a1, a2, ..., an} is the set of all available actions
	- P: P(St+1 = s′|St = s, At = a) is the transition probability matrix
	- R: R(s, a) is the reward function of every (s, a) pairs.

**PART 2**:
- The RL agent, is represented as a policy network which maps the state vector to a stochastic policy.
$$π_θ(s, a) = p(a|s; θ)$$

- The neural network parameters $θ$ are updated using stochastic gradient descent.

- **Policy-based RL methods is more appropriate**: The action space can be very large due to complexity of the relation graph.
	- Deep Q Network (DQN): Not good.
		- Can lead to poor convergence properties. 
		- Learning a greedy policy which is common in value-based methods


#### RL Environment

**Actions**
- Given the entity pairs $(e_s, e_t)$ with relation $r$, we want the agent to find the most informative paths linking these entity pairs.

- Beginning with the source entity $e_s$, the agent use the policy network to pick the most promising relation to extend its path at each step until it reaches the target entity $e_t$.

- The action space is defined as all the relations in the KG: keep the output dimension of the policy network consistent.

**States**
- To capture the semantic information of these symbols, we use translation-based embeddings such as TransE and TransH to represent the entities and relations.

 - Each state captures the agent’s position in the KG. After taking an action, the agent will move from one entity to another. These two are linked by the action (relation) just taken by the agent.

- State vector at step $t$:
$$s_t = (e_t, e_{target} − e_t)$$
- $e_t$ : Embeddings of the current entity node
- $e_{target}$ : Embeddings of the target entity node

**Rewards**: Encourage the agent to find predictive paths
- *Global accuracy*
	- The number of actions that can be taken by the agent can be very large.
	- There are much <u>more incorrect sequential decisions</u> than the correct ones.
	- $r_{global}$
		- +1, if the path reaches $e_{target}$
		- -1, otherwise

- *Path efficiency*
	- Train the agent to find paths using <u>positive samples for each relation</u>.
	- Often contains redundant information since some of them may be correlated.
	- Diversity reward function: Cosine similarity between the current path and the existing ones
 $$r_{DIVERSITY} = -\frac{1}{|F|} \sum_{i=1}^{|F|}cos(p, p_i)$$
	- Path embeddings for the relation $p = \sum_{i=1}^{n}r_i$
	- $r_1$ -> $r_2$ -> $r_3$ -> ... -> $r_n$

- *Policy Network*
	- Fully-connected neural network
		- To parameterize the policy function $π(s; θ)$ that maps the state vector $s$ to a probability distribution over all possible actions.
		- 2 hidden layers, with ReLU.
		- Output layer: Normalized with Softmax function


#### Training pipeline
