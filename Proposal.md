# Transductive Few-shot learning for Rule based Multi-hop graph reasoning

Challenges:

Sparse graph with disconnected nodes


Goal:
Find instance paths where the corresponding metapath match the rule body 

Effectiv e logical rules via a novel reward function. This can help to denoise the reward signal and guide the agent on long paths with high-degree nodes.


Starting at a query enetity, an agent performs a walk on the graph by sequentially transitioning to a neighboring node. The decision of which transition to make is determined by a stochastic policy. The stochastic walk process iterates until a finite number of transitions has been made. 



Extract Subgraphs
