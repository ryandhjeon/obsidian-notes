# Metapath2vec: Scalable Representation Learning for Heterogeneous Networks
#### (2017) - Yuxiao Dong, Nitesh V. Chawla, Ananthram Swami
**Link**: https://dl.acm.org/doi/10.1145/3097983.3098036
**DOI**: 10.1145/3097983.3098036
**Code/Link**:
**Tags**: #paper
**Rating**:

### Abstract

```
We study the problem of representation learning in heterogeneous networks. Its unique challenges come from the existence of mul- tiple types of nodes and links, which limit the feasibility of the conventional network embedding techniques. We develop two scalable representation learning models, namely metapath2vec and metapath2vec++. The metapath2vec model formalizes meta-path- based random walks to construct the heterogeneous neighborhood of a node and then leverages a heterogeneous skip-gram model to perform node embeddings. The metapath2vec++ model further enables the simultaneous modeling of structural and semantic cor- relations in heterogeneous networks. Extensive experiments show that metapath2vec and metapath2vec++ are able to not only outper- form state-of-the-art embedding models in various heterogeneous network mining tasks, such as node classification, clustering, and similarity search, but also discern the structural and semantic cor- relations between diverse network objects.
```

### 요약
https://www.youtube.com/watch?v=prX2p9S8C1U

**Embedding based Method**
- TransE
	- 이병헌과 류승룡과 영화 광해의 관계
- TransR
	- 이병헌은 액션, 류승룡은 코메디에 많이 나오기 때문에 Embedding이 달라져야 한다
	- 이병헌의 대표장르, 류승룡의 대표장르에 따라 학습 정보가 달라져야 한다
	- Entity Space에서 류승룡과 이병헌은 가깝지만, Relation Space에서는 멀어진다
	- 특정 Node는 특정 Relation에 대해서 다른 space에서 학습이 되어야 한다. (Graph Attention Network)
- Graph Attnention Network - Score

**Path based Method**
- DeepWalk
	- 이웃을 어떻게 정의 할 것인지
	- 그래프간의 연관성이 어떻게 되는지?
	- Diffusion: 연결된 노드에 따라 정보의 교환(Diffusion)을 할 수 있다.
	- $A$를 제곱해서 $A^2$ 로 2 Step의 연결 여부를 알수가 있다.
	- 평균을 하게 되면, [[High order proximity]] 를 정보를 알수가 있다. 
	- PPMI를 적용할수 있는데,
		- ex. Node 1번이 파워가 커졌을때, 그것이 어떻게 전파되는지. Negative value가 됬을때는 0으로 전처리를 하는 방법이 PPMI.
	- [[Window size]]: Neighborhood의 사이즈를 정해주는 것. 안에 있는것들은 Neighbor이다. 비슷한 정보들이 window안에 있기 때문에 비슷하게 Embedding 되어야 한다.
	- 보통은 One-hot encodding을 사용하지만, [[Skip-gram]]의 Hidden layer의 가중치를 사용하게 된다 (Negative sampling).
	- 한계: 
		- 노드가 같다는 것을 Assume 하고 시작한다.
		- 하지만 Node & Relation type이 다를때, Deepwalk 기반은 문제가 있다.




### SUMMARY
- What was the author's goal?
- What is the most important element of this approach?
- Can I utilize this thesis?
- Is there any other reference I would like to review?
- How can I improve this thesis?
- Is Github repository available?