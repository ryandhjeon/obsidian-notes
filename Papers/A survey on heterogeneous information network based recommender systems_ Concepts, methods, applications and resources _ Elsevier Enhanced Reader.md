# A survey on heterogeneous information network based recommender systems: Concepts, methods, applications and resources | Elsevier Enhanced Reader
#### () - 
**Link**: https://reader.elsevier.com/reader/sd/pii/S2666651022000092?token=19B5714C0B701C3590C0E3919CF4FCF6CB54CBCD4386EF591A1492F4ECD7F6FE3367D802D7BCCC3FCAC65982EDB3F24E&originRegion=us-east-1&originCreation=20230403203749
**DOI**: 10.1016/j.aiopen.2022.03.002
**Code/Link**:
**Tags**: #paper
**Rating**:

### Abstract

```
As an important way to alleviate information overload, a recommender system aims to filter out irrelevant information for users and providesthem items that they may be interestedin. In recent years, an increasing amount of works have been proposed to introduce auxiliary information in recommender systems to alleviate data sparsity and cold-start problems. Among them, heterogeneous information networks (HIN)-based recommender systems provide a unified approach to fuse various auxiliary information, which can be combined with mainstream recommendation algorithms to effectively enhance the performance and interpretability of models, and thus have been applied in many kinds of recommendation tasks. This paper provides a comprehensive and systematic survey of HIN-based recommender systems, including four aspects: concepts, methods, applications, and resources. Specifically, we firstly introduce the concepts related to recommender systems, heterogeneous information networks and HIN-based recommendation. Secondly, we present more than 70 methods categorized according to models or application scenarios, and describe representative methods symbolically. Thirdly, we summarize the benchmark datasets and open source code. Finally, we discuss several potential research directions and conclude our survey.
```

### INTRODUCTION

- Recommender systems often rely on historical user behavior data
- However, in many scenarios where users or items are updated frequently, historical behavior data is very sparse
- Cold-start in extreme case
- [[Auxiliary information]] to alleviate the data sparsity and cold-start problem
- [[Heterogeneous information networks]] (HINs) naturally preserves the entities and relationshis in the recommender system, and incorporates various auxiliary information.
- Effectively alleviates the data sparsity and cold start problems, and imrpoves the interpretability of recsys.

### CONCEPTS

1. Meta-path
2. Meta-structure (Meta-graph)
3. HIN-based recommender systems
	1. Link prediction task on the information network
	2. Traditional recsys are based on bipartite graph modeling, difficult to use various auxiliary information.
	3. HIN-based recommender systems have successfully solved the problem of modeling heterogeneous auxiliary information and user interaction behaviors in a unifiedmanner, which can not only effectively alleviate the data sparseness and cold start problems in the recom mender systems, but also significantly improve the interpretability of the recommender systems, so have received extensive attention and applications.
	4. Two steps
		1. Construct a heterogeneous information network based on the user-item interaction data and all auxiliary information.
		2. Design a recommendation model suitable for the specific heterogeneous information network.

![[Pasted image 20230403205915.png]]
![[Pasted image 20230403205927.png]]

### TAXONOMY BASED ON MODELS
(Designing a recommendation algorithm suitable for heterogeneous information networks)

1. Similarity Measurement
	1. Relation-based
	2. Meta-path based
2. Matrix Factorization
	1. Regularization-based
	2. Neural matrix factorization-based
3. Graph Representation Learning
	1. Two-state training-based
	2. End-to-end training based: Relation based
	3. End-to-end training based: Meta-path based
--- 
**1. Similarity Measurement**
- Collaborative filtering calculates the [similarity based on the interaction history] between the [user] and the [item]. 
	**Algorithms for Homogeneous Information network** (BAD)	
	- SimRank: Homogeneous. Evaluates the similarity of objects by the [similarity of the neighbors] of two objects
	- P-PageRank: Homogeneous. Evaluates the probability from the source object to the target object by restarting random walks
	- !! Homogeneous Information Networks [ignore the different types of objects and connections]. Not suitable for recsys as Hteterogeneous Information networks.

	**Algorithms for Heterogeneous Information network**
	1. Relation-based similarity measurement method
		- Assumes that the relevance of an item to a user can be obtained from the random walk probability of the user to the item. (High Probability = High relevance of them)
		- Always use randomwalk algorithm
	2. Meta-path based
		- Relation-based similarity measurement methods aim to learn relation-level transition probability.
		- Strong interpretability
		- !! Lacks on the explicit use of higher-level semantic information.
		- Similarity measurement based on meta-path introduces additional prior knowledge by introducing meaningful meta-paths manually
		- Good for capturing long-range semantic information
		- Classic Three kinds
			- Path Count (PathSim)
			- Path-based random walk (PCRW)
			- Path-based pairwise random walk (HeteSim)
- Summary: 
	- Earliest works using heterogeneous similarity measurement for CF-based recommender systems
	- Require a large amount of interactive information
	- It’s hard to provide recommendations to users and items that lack connectivity

**2. Matrix Factorization**
- Many advantages
- Output of matrix factorization is the hidden vectors of users and items, any user-item pair can predict the score, which improves the generalization ability and reduces space complexity
- !! Difficulty in modeling high-order interactions between users and items

**3. Graph representation learning (GRL)**
- Recsys based on NN has achieved better recommendation results
- Has strong cross capability and flexibility of model architecture design
- GRL learn the rich structural and semantic information in graph data

	**3.1 Two-stage training-based**
	- Unsupervised GRL aims to learn low-dimensional vector representations of graph structure to conveniently store and apply to various downstream tasks.
	- Pre-training + Fine-tuning
	- Inspired by [[DeepWalk]], and [[node2vec]], and other methods, many unsupervised heterogeneous graph embedding methods based on randomwalks were designed. 
		- [[metapath2vec]], [[HIN2Vec]]
		- Applied to the structural feature generation of recsys.
		- [[HERec]] uses meta-path based random walks to generate object sequences and uses [[node2vec]] to learn the embeddings of objects. Then, computes the similarity of embeddings for recommendation.
		- Some methods are based on relational modeling and do not need to manually specify the meta-path.
	**3.2 End-to-end training-based**
	- Two-stage training methods don't use the supervised information in the graph embedding stage, which is difficult for various recommendation tasks.
	- End-to-end embedding method uses supervision information while learning the graph embedding. 
		**3.2.1 Relation based**
		- Relation-aware GNN ([[RGCN]]) is used for recommender systems
		**3.2.2 Meta-path based**
		- Introduces prior knowledge and capture high-level semantic information in heterogeneous graphs ([[HAN]])
		- Aggregates heterogeneous neighbors of each order along the meta-path, and then aggregates different meta-paths to obtain user embedding and query embedding. 
		- [[NIRec]] introduces an interactive information extraction layer before the dual-level aggregation layer. 
		- [[MetaHIN]] aggregates both direct neighbors and meta-path-based neighbors as the base model of a co-adaptation meta-learner for cold-start recommendation.

### FUTURE DIRECTIONS
- Most HIN recommendation models represented by the heterogeneous GNN face many challenges.
	- Message passing: Poor robustness, and difficult to train with some missing or wrong links (Contrastive learning, multi-task learning, graph denoising framework only suitable for homogeneous or bipartite graphs)
	- Needs better meta-paths or meta-structures



### SUMMARY
- What was the author's goal?
- What is the most important element of this approach?
- Can I utilize this thesis?
- Is there any other reference I would like to review?
- How can I improve this thesis?
- Is Github repository available?