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
2. [relation-aware GNNs]: Considers mluti-relational graphs with labels and directions on the edges.
	- Natural language understanding
	- Modeling protein structure
	- Drug-drug interaction prediction
	- Retrosynthesis planning

