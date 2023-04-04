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
**Similarity Measurement**
- Collaborative filtering calculates the [similarity based on the interaction history] between the [user] and the [item]. 
	
	- SimRank: Homogeneous. Evaluates the similarity of objects by the [similarity of the neighbors] of two objects
	- P-PageRank: Homogeneous. Evaluates the probability from the source object to the target object by restarting random walks
	- Homogeneous Information Networks [ignore the different types of objects and connections]. Not suitable for recsys as Hteterogeneous Information networks.

**Algorithms for Heterogeneous Information network**
1. Relation-based
	-  
2. Meta-path based



### SUMMARY
- What was the author's goal?
- What is the most important element of this approach?
- Can I utilize this thesis?
- Is there any other reference I would like to review?
- How can I improve this thesis?
- Is Github repository available?