# Learning to Extrapolate Knowledge: Transductive Few-shot Out-of-Graph Link Prediction
#### (2020) - Jinheon Baek, Dong Bok Lee, Sung Ju Hwang
**Link**: https://proceedings.neurips.cc/paper/2020/hash/0663a4ddceacb40b095eda264a85f15c-Abstract.html
**DOI**: 
**Code/Link**:
**Tags**: #paper
**Rating**:

### Abstract

```
Many practical graph problems, such as knowledge graph construction and drug-drug interaction prediction, require to handle multi-relational graphs. However, handling real-world multi-relational graphs with Graph Neural Networks (GNNs) is often challenging due to their evolving nature, as new entities (nodes) can emerge over time. Moreover, newly emerged entities often have few links, which makes the learning even more difficult. Motivated by this challenge, we introduce a realistic problem of few-shot out-of-graph link prediction, where we not only predict the links between the seen and unseen nodes as in a conventional out-of-knowledge link prediction task but also between the unseen nodes, with only few edges per node. We tackle this problem with a novel transductive meta-learning framework which we refer to as Graph Extrapolation Networks (GEN). GEN meta-learns both the node embedding network for inductive inference (seen-to-unseen) and the link prediction network for transductive inference (unseen-to-unseen). For transductive link prediction, we further propose a stochastic embedding layer to model uncertainty in the link prediction between unseen entities. We validate our model on multiple benchmark datasets for knowledge graph completion and drug-drug interaction prediction. The results show that our model significantly outperforms relevant baselines for out-of-graph link prediction tasks.
```

### Introduction

1. [GNN]: Exploit the graph-structured data which works on a non-Euclidean domain. Mostly deals with simple graphs with unlabeled edges.
2. [Relation-aware GNNs]: Considers mluti-relational graphs with labels and directions on the edges.
	- Natural language understanding
	- Modeling protein structure
	- Drug-drug interaction prediction
	- Retrosynthesis planning

*Challenges of link prediction for KGs*
1. KGs dynamically evolve over time. Around 200 new entities emerge every day. Predicting links on the emerging (Unseen) entities pose a new challenge.
2. Real-world KGs exhibit [long-tail distributions], where large portion of the entities have only few triplets. [Embedding-based methods] cannot embed unseen entities.

*Propose Graph Extrapolation Networks (GENs)*
- Few-shot Out-of-Graph(OOG) link prediction for emerging entities
- Seen - Unseen && Unseen - Unseen
- GENs are meta-learned to extrapolate the knowledge from seen to uness entities
- Transfers knowledge from entities with many to few links. 
- Meta-trains two GNNs to predict the links between entities
	1. [Inductive GEN]: 1st GNN; learns to embed the unseen entities that are not observed, and predicts the links between seen and unseen entities.
	2. [Transductive GEN]: 2nd GNN; learns to predict the links not only between seen and unseen entities, but also between unseen entities themselves.
- Link prediction for unseen entities is unreliable, which gets worse when few triplets are available for each entitiy. 
- [Stochastic embedding] is used to learn the distribution of unseen representations for stochastic embeeding to account for the [uncertainty]
- [Transfer learning strategy] to model the long-tail distribution. Leads GEN to represent the unseen entities that are well aligned with the seen entities

*Link prediction goal*
- Entitiy prediction
- Relation prediction

*Learning to Extrapolate Knowledge with Graph Extrapolation Networks*
- Training for 'seen-to-seen' work well on 'seen-to-unseen' cases?
	- No. Use [meta learning] framdework to handle the OOG link prediction problem. Train a model over a <u>distribution of tasks</u> such that the model generalizes well on unseen tasks.

**Learning Objective**
- Maximize the score of a true triplet $s(e_h, r, e_t)$ that contains any unseen entities $e'$ to rank it higher than all the other false triplets, with embedding and score function parameters $\theta$ denoted as follows:
![[Pasted image 20230328215106.png]]
- Generalization to real unseen entities can be tackled with [meta-learning] by simulating unseen entities during training

**Meta-Learning Framework**
- We can formulate a set of tasks such that the model learns to generalize over unseen entities, which are simulated using seen entities.
1. <u>Randomly split</u> the entities in a given graph into the [meta-training set] for simulated unseen entities, and the [meta-test set] for real unseen entities
2. Generate a task by <u>sampling the set of simulated unseen entities</u> during meta-training, for the learned model to generalize over actual unseen entities.
3. Each task $\mathcal{T}$ over a distribution $p(\mathcal{T})$ corresponds to a set of unseen entities $\mathcal{E_T} \subset \mathcal{E'}$ with a predefined number of instances $|\mathcal{E_T}| = N$ 
4. Divide the triplets associative with each entity $\mathcal{e_{i}' \in \mathcal{E_T}}$ into the support set $S_i$ and the query set ![[Pasted image 20230328220410.png]]

- Meta-objective: Learning to represent the unseen entities as $\phi$ using a suppor set $S$ with a meta-function $f$, to maximize the triplet score on a query set $\mathcal{Q}$ with a score function $s$ as follows:
![[Pasted image 20230328220849.png]]
- Once the model is trained with the [meta-training tasks] $\mathcal{T_train}$, we can apply it to [unseen meta-test tasks] $\mathcal{T_test}$. The set of entities is disjoint from $\mathcal{T_train}$. 
- 