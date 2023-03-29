# Transductive Few-shot learning for Rule based Multi-hop graph reasoning

Challenges:

Sparse graph with disconnected nodes


Goal:
Find instance paths where the corresponding metapath match the rule body 

Effectiv e logical rules via a novel reward function. This can help to denoise the reward signal and guide the agent on long paths with high-degree nodes.


Starting at a query enetity, an agent performs a walk on the graph by sequentially transitioning to a neighboring node. The decision of which transition to make is determined by a stochastic policy. The stochastic walk process iterates until a finite number of transitions has been made. 



Method:

1. Extract Subgraphs
2. Transductive Few-shot learning for expolating the data. The output information will guide multi-hop reasoning models for the model learning. The probability vector of all entities being the tail entity. The ht from LSTM is added to the state representation.
3. We sample an entity based on probability distribution $\text p$ and denote its vector as $e_p$.



###### Reference







