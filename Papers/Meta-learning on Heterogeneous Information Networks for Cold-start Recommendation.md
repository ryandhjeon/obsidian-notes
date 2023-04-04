# Meta-learning on Heterogeneous Information Networks for Cold-start Recommendation
#### (2020) - Yuanfu Lu, Yuan Fang, Chuan Shi
**Link**: https://dl.acm.org/doi/10.1145/3394486.3403207
**DOI**: 10.1145/3394486.3403207
**Code/Link**:
**Tags**: #paper
**Rating**:

### Abstract

```
Cold-start recommendation has been a challenging problem due to sparse user-item interactions for new users or items. Existing efforts have alleviated the cold-start issue to some extent, most of which approach the problem at the data level. Earlier methods often incorporate auxiliary data as user or item features, while more recent methods leverage heterogeneous information networks (HIN) to capture richer semantics via higher-order graph structures. On the other hand, recent meta-learning paradigm sheds light on addressing cold-start recommendation at the model level, given its ability to rapidly adapt to new tasks with scarce labeled data, or in the context of cold-start recommendation, new users and items with very few interactions. Thus, we are inspired to develop a novel meta-learning approach named MetaHIN to address cold-start recommendation on HINs, to exploit the power of meta-learning at the model level and HINs at the data level simultaneously. The solution is non-trivial, for how to capture HIN-based semantics in the metalearning setting, and how to learn the general knowledge that can be easily adapted to multifaceted semantics, remain open questions. In MetaHIN, we propose a novel semantic-enhanced tasks constructor and a co-adaptation meta-learner to address the two questions. Extensive experiments demonstrate that MetaHIN significantly outperforms the state of the arts in various cold-start scenarios. (Code and dataset are available at https://github.com/rootlu/MetaHIN.)
```

---
### Problem Definition
1. Heterogeneous Informatio Network (HIN)
2. Meta-path
3. Cold-start Recommendation
---
### Meta-learning for Recommendation
- Inspired by optimization-based meta-learning. Optimizes globally shared parameters (prior knowledge) over several tasks, so as to rapidly adapt to a new task with just one or a few gradient steps
---
### Methodology
1. Semantic-enhanced Task Constructor
2. Co-adaptation Meta-learner
	1. Base Model $$f_θ = (g_{\phi} , h_ω )$$
		 - Context aggregation (User embeddings)
			 - Initialize User & Item embeddings based on their features
		 - Preference prediction (Estimate the rating score)
			 - User's embedding $\text x_u$ and item it's embedding $e_i$ 
			 - Estimate the rating of user $u$ on the item $i$ 
			 $$r_{ui} = h_{\omega}(\text x_u, e_i) = \text MLP(\text x_u \oplus e_i)$$
		- Minimize loss for user $u$ to learn the preferences
		- !! The base model $f_θ$ needs a large number of example ratings to achieve reasonable performance (Not good for cold-start scenario)
		- Using the meta-learning problem, abstract the base model $f_θ = (g_{\phi} , h_ω )$ as encoding the prior knowledge $θ = {\phi, ω}$  of how to learn user preferences from contexts on HINs.
	2. Co-adaptation
		 `PRIOR KNOWLEDGE` using meta-learning
		1. Semantic-wise Adaptation
		2. Task-wise Adaptation
		3. Optimization


### SUMMARY
- What was the author's goal?
- What is the most important element of this approach?
- Can I utilize this thesis?
- Is there any other reference I would like to review?
- How can I improve this thesis?
- Is Github repository available?