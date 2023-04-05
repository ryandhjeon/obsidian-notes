#HeterogeneousGraph #Recommendation #LinkPrediction #Transductive

### Goal

- Improve the recommendation performance on Heterogeneous Informaiton Networks (HIN)

### Peliminary

- Meta-path
- Heterogeneous Information Network (HIN)
- HIN based recommendation
  ddd

### Introduction

However, most of the existing network embedding methods [3] mainly focus on homogeneous networks, which are not able to effectively model heterogeneous networks. 

1. Path based similarities [1] or latent factors [2], which cannot learn the complicated mapping mechanism of HIN information for recommendation

Learn effective heterogeneous network representations for summarizing important structural characteristics and properties of HINs. 

### Challenge

1. Meta-path based similarities rely on explicit path reachability, and may not be reliable to be used for recommendation when path connections are sparse or noisy.
2. Meta-path based similarities mainly characterize semantic relations defined over HINs, and may not be directly applicable to recommender systems

### Contribution

1. To alleviate challenge #1, we introduce 
2. To alleviate challenge #2, we introduce

### Proposed approach

1. **Heterogeneous Network Embedding**

	Inspired by the recent progress on network embedding [3], [4], we adopt the representation learning method to extract and represent useful information of HINs for recommendation. The goal is to learn a low-dimensional representation $e_v ∈ \mathbb{R}^d$ (embedding) for each node $v ∈ V$.

	1.1 Meta-path based Random Walk

	1.2 


### Dataset



### Evalutation method

- What to evaluate (WHY?)
- Comparison (SAME DATA?)

### Reference

[1] C. Shi, J. Liu, F. Zhuang, P. S. Yu, and B. Wu, “Integrating heterogeneous information via flexible regularization framework for recommendation,” Knowledge and Information System, vol. 49, no. 3, pp. 835–859, 2016.

[2] X. Yu, X. Ren, Q. Gu, Y. Sun, and J. Han, “Collaborative filtering with entity similarity regularization in heterogeneous information networks,” Proceedings of 1st International Joint Conference on Artificial Intelligence Workshop on Heterogeneous Information Network Analysis, 2013.

[3] B. Perozzi, R. Al-Rfou, and S. Skiena, “Deepwalk: Online learning of social representations,” in Proceedings of the 20th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 2014, pp. 701–710.

[4] A. Grover and J. Leskovec, “node2vec: scalable feature learning for networks,” in Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 2016, pp. 855864.


