# Knowledge Graph Reasoning


Knowledge graph completion is the most widely used field of knowledge reasoning: TransR, CapsE, RGHAT, etc

*3.1 Embedding-based Reasoning (Neural Methods)* 

Determination of mapping function that maps a symbolic representation to a vector space for numerical representation

Reduces the dimension disaster and captures the implicit association between entities and relations.

Key point: Can be calculated directly and quickly.

Extended from [[Word2vec]], embedding knowledge graphs into low-dimensional geometric spaces (Euclidean space, or hyperbolic space, etc...) through translation or rotation.

Translation: Vector addition

Rotation: Hadamard product

ex: TransE, TransH, TransR, TransD, ComplEx, RotatE,  QuatE, RESCAL, DisMult, etc...

Neural Methods
ex: RGCN, GraIL, 

*3.2 Symbolic-Based Reasoning*

Reasoning new entity relations using rules through first-order predicate logic and description logic.

CON: Efficiency of logical reasoning on large-scale knowledge graph is limited by its discreteness.

PRO: The rules are usually similar to the reasoning processes that humans use to think about problems, and its reasoning conclusions can be explained.

ex: Inductive logic programming([[ILP]]), Association rule mining under incomplete evidence ([[AMIE]]), [[TensorLog]], [[ProPPR]]

*Symbolic Logic Methods*
Logic Programming, Inference Algorithms

*3.3 Neural-Symbolic Methods*

1. Use a collection of logic rules and forward chaining to build a Markov logic network (MLN)
2. Use Neural Methods to improve inference and learning of MLN



PRO: 
	- Strong expression ability and achieve good results in relation (link) prediction and other tasks
	- Symbolic: Ability of using domain Knowledge, interpretability
	- Neural: Efficiency, Capacity

ex: Reasoning With Neural Tensor Networks for Knowledge Base Completion ([[NTN]]), [[R-GCN]]


**MLN**: Combines first-order logic and probabilistic graphical models

Pro:
- Effectively leverage domain knowledge with logic rules
- Handle the uncertainty

Limitation: 
- Inference is difficult due to complicated graph structures
- Recall is low since many facts are not covered by any logic rules

**Knowledge Graph Embeddings**: Learn the entity and relation embeddings for predicting the missing facts

Pro:
- Can be effectively and efficiently trained by SGD
- High recall of missing link prediction with entity and relation embeddings

Limitation:
- Hard to leverage domain knowledge (logic rules)

**Probabilistic Logic Neural Networks for Reasoning**: 
<sub>Meng Qu and Jian Tang. Probabilistic logic neural networks for reasoning. NeurIPS 2019.</sub>

1. Towards combining Markov Logic Networks and knowledge graph embedding
	- Leverage logic rules and handle their uncertainty
	- Effective and efficient inference
2. Define the joint distribution of facts with Markov Logic Network
3. Optimization with variational EM
	- Parametrize the variational distribution with knowledge graph embedding methods



