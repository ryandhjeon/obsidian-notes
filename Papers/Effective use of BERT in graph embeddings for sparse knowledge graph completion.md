# Effective use of BERT in graph embeddings for sparse knowledge graph completion
#### (2022) - Xinglan Liu, Hussain Hussain, Houssam Razouk, Roman Kern
**Link**: https://dl.acm.org/doi/10.1145/3477314.3507031
**DOI**: 10.1145/3477314.3507031
**Code/Link**:
**Tags**: #paper #KG/Sparse
**Rating**:

### Abstract

```
Graph embedding methods have emerged as effective solutions for knowledge graph completion. However, such methods are typically tested on benchmark datasets such as Freebase, but show limited performance when applied on sparse knowledge graphs with orders of magnitude lower density. To compensate for the lack of structure in a sparse graph, low dimensional representations of textual information such as word2vec or BERT embeddings have been used. This paper proposes a BERT-based method (BERT-ConvE), to exploit transfer learning of BERT in combination with a convolutional network model ConvE. Comparing to existing text-aware approaches, we effectively make use of the context dependency of BERT embeddings through optimizing the features extraction strategies. Experiments on ConceptNet show that the proposed method outperforms strong baselines by 50% on knowledge graph completion tasks. The proposed method is suitable for sparse graphs as also demonstrated by empirical studies on ATOMIC and sparsified-FB15k-237 datasets. Its effectiveness and simplicity make it appealing for industrial applications.
```

### Notes

#### Dataset
ATOMIC
Sparsified-FB15k-237
ConceptNet100k

