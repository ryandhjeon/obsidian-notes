# An Overview of Knowledge Graph Reasoning: Key Technologies and Applications
#### (2022) - Yonghong Chen, Hao Li, Han Li, Wenhao Liu, Yirui Wu, Qian Huang, Shaohua Wan
**Link**: https://www.mdpi.com/2224-2708/11/4/78
**DOI**: 10.3390/jsan11040078
**Code/Link**:
**Tags**: #paper #KG/Survey
**Rating**:

### Abstract

```
In recent years, with the rapid development of Internet technology and applications, the scale of Internet data has exploded, which contains a significant amount of valuable knowledge. The best methods for the organization, expression, calculation, and deep analysis of this knowledge have attracted a great deal of attention. The knowledge graph has emerged as a rich and intuitive way to express knowledge. Knowledge reasoning based on knowledge graphs is one of the current research hot spots in knowledge graphs and has played an important role in wireless communication networks, intelligent question answering, and other applications. Knowledge graph-oriented knowledge reasoning aims to deduce new knowledge or identify wrong knowledge from existing knowledge. Different from traditional knowledge reasoning, knowledge reasoning methods oriented to knowledge graphs are more diversified due to the concise, intuitive, flexible, and rich knowledge expression forms in knowledge graphs. Based on the basic concepts of knowledge graphs and knowledge graph reasoning, this paper introduces the latest research progress in knowledge graph-oriented knowledge reasoning methods in recent years. Specifically, according to different reasoning methods, knowledge graph reasoning includes rule-based reasoning, distributed representation-based reasoning, neural network-based reasoning, and mixed reasoning. These methods are summarized in detail, and the future research directions and prospects of knowledge reasoning based on knowledge graphs are discussed and prospected.
```

### Notes

#### 3. Knowledge Graph Reasoning

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



ex: Reasoning With Neural Tensor Networks for Knowledge Base Completion ([[NTN]]), [[R-GCN]],