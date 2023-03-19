# A Novel Embedding Model for Knowledge Base Completion Based on Convolutional Neural Network
#### (2018) - Dai Quoc Nguyen, Tu Dinh Nguyen, Dat Quoc Nguyen, Dinh Phung
**Link**: http://arxiv.org/abs/1712.02121
**DOI**: 10.18653/v1/N18-2053
**Code/Link**:
**Tags**: #paper #KG/ConvKB
**Rating**:

### Abstract

```
In this paper, we propose a novel embedding model, named ConvKB, for knowledge base completion. Our model ConvKB advances state-of-the-art models by employing a convolutional neural network, so that it can capture global relationships and transitional characteristics between entities and relations in knowledge bases. In ConvKB, each triple (head entity, relation, tail entity) is represented as a 3column matrix where each column vector represents a triple element. This 3-column matrix is then fed to a convolution layer where multiple filters are operated on the matrix to generate different feature maps. These feature maps are then concatenated into a single feature vector representing the input triple. The feature vector is multiplied with a weight vector via a dot product to return a score. This score is then used to predict whether the triple is valid or not. Experiments show that ConvKB achieves better link prediction performance than previous state-of-the-art embedding models on two benchmark datasets WN18RR and FB15k-237.
```

### Notes

- KBs are missing a lot of valid triples (Socher et al., 2013; West et al., 2014)
	- Valid triples obtain lower implausibility scores than invalid triples

- Example of [[TransE]]: Entities and relations are represented by k- dimensional vector embeddings

- Using relation paths between entities in the KBs could help to get contextual information for improving KB completion performance

- [[ConvE]]—the first model applying CNN for the KB completion task (Dettmers et al. 2018)
	- ConvE focuses on the local relationships among different dimensional entries in each of vh or vr, i.e., ConvE does not observe the global relationships among same dimensional entries of an embedding triple (vh, vr, vt), so that ConvE ignores the transitional characteristic in transition-based models, which is one of the most useful intuitions for the task.

- [[ConvKB]]


### Datasets
- [[WN18RR]]
- [[FB15k-237]]

- WN18RR and FB15k-237 are created to not suffer from this reversible relation problem in WN18 and FB15k, for which the knowledge base completion task is more realistic.

- [[Filtered setting]] protocol: Bordes et al. (2013)

### Evaluation metrics for corrupted triplets
- Mean rank (MR): Lower MR, the better performance
- Mean reciprocal rank (MRR): Higher MRR, the better performance
- Hits@10: Higher Hits@10 the better performance.
	- i.e., the proportion of the valid test triples ranking in top 10 predictions