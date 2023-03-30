# Proposal: Transductive Few-shot learning for  Multi-hop graph reasoning

We propose to develop a deep learning-based KG completion model for two tasks:
1) KG reasoning by KG completion for ADs potential treatment prediction
2) Efficient KG update

Additionally, KG completion aims to infer missing triplets by reasoning the information already present in the KG. KG update aims to incorporate new entities or relations to an existing graph.

Generally, most KGs tend to be incomplete and outdated. For the incompleteness, large KGs naturally contain a lot of missing relations due to distant and implicit relationships between entities. Moreover, most KGs quickly become outdated after the initial construction due to the high cost of synchronizing new knowledge. In this project, we propose a deep learning-based algorithm for KG reasoning and efficient KG update for large KGs.

Primarily, we propose a multi-hop with auto-connection algorithm to capture distant and implicit missing relations in a large KG.

Traditionally, Path Ranking Algorithm (PRA)-based models are effective but often experience two challenges with large KGs.
1) Search space explosion (path explode due to the large size of entities and relations)
2) Poor representation of semantic information in a discrete space

Therefore, the proposed algorithm adopts Meta-learning and Reinforcement Learning (RL) to ease the pain of traditional methods. 

Link prediction task, which automatically completes knowledge graph is successfully tackled by learning embeddings of entities and relations from existing triplets. However, the embedding based methods usually assume that a sufficient number of associative triplets exist for training and cannot embed unseen entities. Thus, they are highly suboptimal for learning and inference on evolving real-world graph. When new subgraphs emerges, we can meta-learn the small number of seen entities to extrapolate the knowledge and transfer knowledge from known entities to incoming entities. Given embeddings of the seen entities for a multi-relational graph, we can meta-train GNN to predict the links between seen-to-unseen, and unseen-to-unseen entities. Then, we can meta-test on the unseen entities and generate embeddings without re-training the entire model from scratch. After construction of the representation of each unseen entity, we can perform the link prediction. With this method, sparsity in large KGs is not an issue anymore

However, even though we might have inferred the new triplets to the original knowledge graph, we cannot explain what relationships the entities have with each other. To do that, we run the multi-hop reasoning process with RL.

Here, we follow the strategy that the path-based reasoning model, DacKGR used. During the Dynamic Anticipation, we use the prediction information from the meta-learned model to get the probability vector of all entities being the tail entity. 

In sparse KGs, there are insufficient evidential paths between head and tail entities. During the Dynamic Completion step, the action space of each entity is dynamically augemented during reasoning process. We use path based method to get the essential supporting paths over KG as evidences of the reasoning results. The multi-hop sequential reasoning in the KG can be modeled as a Markov decision process(MDP). The framework consists of states $S$, actions $\mathcal A$, transition $\sigma$, rewards $\mathcal R$, and a policy network p.

- States: We want to implement the state that encodes the observed information as much as possible. Multi-hop reasoning process considers; current entity $e_t$, query relation $r_q$, previous historical reasoning process $h_t$.

- Actions: The set of possible actions. $A$ of step $t$ consists of the outgoing edges of $e_t$ in KGs. A 'self-loop' edge is appended to every $A_t$, as the search process is within a given step, acting as a 'stop' action.

- Transition: Set the maximum hop count to $T$, and if the agent cannot reach the target within the limit, the transition will terminate at the state $s_t$.

- Rewards: If the agent reaches the correct target entity at the end of the search, a terminal reward of 1 or 0 otherwise.

*Policy network*
- Policy network is parameterized by state information, global context and the pathfinding history. 

- Action $a_t$ is represented as the concatenation of the relation embedding $r \in {R^d}$  and target entity embedding $e \in {R^d}$ where every entity and relation in the KG is assigned a dense vector embedding with the same dimension d. 

- $h_t$ covers the sequence of observations and actions. $h_t$ = LSTM($h_{t-1}, a_{t-1}$)

- Encode the action space by stacking the embeddings of all actions in $A_t: A_t \in {R^{|A_t|\times2d}}$

- To avoid the dying ReLU, LeakyReLU with negative input slope $\alpha = 0.01$ is used as nonlinearity

*Reward design*
- Hit target reward $R_h$ 
- $R_h$: [hit target reward], rewards 1 if the predicted triple $\epsilon = (e_s, r_q, e_T) \in KG$

*KG Completion*
FB15K-237-10%
FB15K-237-20%
FB15K-237-50%
WIN18RR

*Drug-Drug Interaction (Link prediction task)*
DeepDDI
BIOSNAP-sub

*Evaluation*: To validate the model efficiency, we plan to split the graph into train set, support set, and query set for testing purpose. In addition, for model performance evaluation, we propose to use the proportion of correct tail entity rankings in the top K, Hit Ratio of 1, 3, 10 (Hits@K) and Mean reciprocal rank of all correct tail entities.

--
Things I might add:
1. Rather than randomly splitting the data for training, find top K dense subgraphs
2. Adding rule miner for iterative rule guidance strategy (AnyBurl) for higher confidence score during RL. This can be added as the additional reward.
3. Decision transformer?

--
REFERENCE

[1]       J. Baek, D. B. Lee, and S. J. Hwang, “Learning to Extrapolate Knowledge: Transductive Few-shot Out-of-Graph Link Prediction,” in _Advances in Neural Information Processing Systems_, Curran Associates, Inc., 2020, pp. 546–560. Accessed: Mar. 21, 2023. [Online]. Available: https://proceedings.neurips.cc/paper/2020/hash/0663a4ddceacb40b095eda264a85f15c-Abstract.html

[2]       R. Das _et al._, “Go for a Walk and Arrive at the Answer: Reasoning Over Paths in Knowledge Bases using Reinforcement Learning.” arXiv, Dec. 30, 2018. Accessed: Jan. 29, 2023. [Online]. Available: http://arxiv.org/abs/1711.05851

[3]       W. Xiong, T. Hoang, and W. Y. Wang, “DeepPath: A Reinforcement Learning Method for Knowledge Graph Reasoning,” in _Proceedings of the 2017 Conference on Empirical Methods in Natural           Language Processing_, Copenhagen, Denmark: Association for Computational Linguistics, 2017, pp. 564–573. doi: 10.18653/v1/D17-1060.

[4]       X. V. Lin, R. Socher, and C. Xiong, “Multi-Hop Knowledge Graph Reasoning with Reward Shaping.” arXiv, Sep. 11, 2018. Accessed: Jan. 26, 2023. [Online]. Available: http://arxiv.org/abs/1808.10568

[5]       G. Marcus, “Deep Learning: A Critical Appraisal”.

[6]       “Lv et al. - 2020 - Dynamic Anticipation and Completion for Multi-Hop .pdf.”

[7]       L. A. Galárraga, C. Teflioudi, K. Hose, and F. Suchanek, “AMIE: association rule mining under incomplete evidence in ontological knowledge bases,” in _Proceedings of the 22nd international conference on World Wide Web_, Rio de Janeiro Brazil: ACM, May 2013, pp. 413–422. doi: 10.1145/2488388.2488425.

[8]       C. Meilicke, M. W. Chekol, D. Ruffinelli, and H. Stuckenschmidt, “Anytime Bottom-Up Rule Learning for Knowledge Graph Completion,” in _Proceedings of the Twenty-Eighth International Joint Conference on Artificial Intelligence_, Macao, China: International Joint Conferences on Artificial Intelligence Organization, Aug. 2019, pp. 3137–3143. doi: 10.24963/ijcai.2019/435.

[9]       Y. Xia, M. Lan, J. Luo, X. Chen, and G. Zhou, “Iterative rule-guided reasoning over sparse knowledge graphs with deep reinforcement learning,” _Inf. Process. Manag._, vol. 59, no. 5, p. 103040, Sep. 2022, doi: 10.1016/j.ipm.2022.103040.