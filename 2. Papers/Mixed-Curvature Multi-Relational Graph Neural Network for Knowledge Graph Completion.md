# Mixed-Curvature Multi-Relational Graph Neural Network for Knowledge Graph Completion
#### (2021) - Shen Wang, Xiaokai Wei, Cicero Nogueira Nogueira dos Santos, Zhiguo Wang, Ramesh Nallapati, Andrew Arnold, Bing Xiang, Philip S. Yu, Isabel F. Cruz
**Link**: https://dl.acm.org/doi/10.1145/3442381.3450118
**DOI**: 10.1145/3442381.3450118
**Code/Link**:
**Tags**: #paper #KG/Mixed-Curvature
**Rating**: -

### Abstract

```
Knowledge graphs (KGs) have gradually become valuable assets for many AI applications. In a KG, a node denotes an entity, and an edge (or link) denotes a relationship between the entities represented by the nodes. Knowledge graph completion infers and predicts missing edges in a KG automatically. Knowledge graph embeddings have shed light on addressing this task. Recent research embeds KGs in hyperbolic (negatively curved) space instead of conventional Euclidean (zero curved) space and is effective in capturing hierarchical structures. However, as multi-relational graphs, KGs are not structured uniformly and display intrinsic heterogeneous structures. They usually contain rich types of structures, such as hierarchical and cyclic typed structures. Embedding KGs in singlecurvature space, such as Euclidean or hyperbolic space, overlooks the intrinsic heterogeneous structures of KGs, and therefore cannot accurately capture their structures. To address this issue, we propose Mixed-Curvature Multi-Relational Graph Neural Network (M2GNN), a generic approach that embeds multi-relational KGs in a mixed-curvature space for knowledge graph completion. Specifically, we define and construct a mixed-curvature space through a product manifold combining multiple single-curvature spaces (e.g., spherical, hyperbolic, or Euclidean) with the purpose of modeling a variety of structures. However, constructing a mixed-curvature space typically requires manually defining the fixed curvatures, which needs domain knowledge and additional data analysis. Improperly defined curvature space also cannot capture the structures of KGs accurately. To address this problem, we set mixed-curvatures as trainable parameters to better capture the underlying structures of the KGs. Furthermore, we propose a Graph Neural Updater by leveraging the heterogeneous relational context in mixed-curvature space to improve the quality of the embedding. Experiments on three KG datasets demonstrate that the proposed M2GNN can outperform its single geometry counterpart as well as state-of-the-art embedding methods on the KG completion task.
```

### Notes

The real-world KG is usually not structured uniformly and demonstrates intrinsic heterogeneous structures.

Mixed-curvature model 



#### Datasets
- WN18RR
- FB15k-237
- YAGO3-10



