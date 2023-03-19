# Reinforcement learning with dynamic completion for answering multi-hop questions over incomplete knowledge graph
#### (2023) - Hai Cui, Tao Peng, Ridong Han, Beibei Zhu, Haijia Bi, Lu Liu
**Link**: https://linkinghub.elsevier.com/retrieve/pii/S0306457323000201
**DOI**: 10.1016/j.ipm.2023.103283
**Code/Link**:
**Tags**: #paper
**Rating**:

### Abstract

```
Text-enhanced and implicit reasoning methods are proposed for answering questions over incomplete knowledge graph (KG), whereas prior studies either rely on external resources or lack necessary interpretability. This article desires to extend the line of reinforcement learning (RL) methods for better interpretability and dynamically augment original KG action space with additional actions. To this end, we propose a RL framework along with a dynamic completion mechanism, namely Dynamic Completion Reasoning Network (DCRN). DCRN consists of an action space completion module and a policy network. The action space completion module exploits three sub-modules (relation selector, relation pruner and tail entity predictor) to enrich options for decision making. The policy network calculates probability distribution over joint action space and selects promising next-step actions. Simultaneously, we employ the beam search-based action selection strategy to alleviate delayed and sparse rewards. Extensive experiments conducted on WebQSP, CWQ and MetaQA demonstrate the effectiveness of DCRN. Specifically, under 50% KG setting, the Hits@1 performance improvements of DCRN on MetaQA-1H and MetaQA-3H are 2.94% and 1.18% respectively. Moreover, under 30% and 10% KG settings, DCRN prevails over all baselines by 0.9% and 1.5% on WebQSP, indicating the robustness to sparse KGs.
```

### Notes



### Challenge
- Action space completion
	- How to efficiently supplement additional actions, which should be semantically consistent with the reasoning process
	- The exhaustive search occurs. 
	$$O(|E|x|R|)$$
- Solution: Reduce search space
	- Separate the procedure of action space completion into two sub-steps
		1. Select top-`M` high-confidence relations conditioned on the state information at timestep `t`
		2. Find top-`N` tail entities. Each pair of selected relation and entity forms a supplementary action to agument the original action space 
		$$O(|R|+M*|E|)$$
		
### Proposed model
- Relation selector
- Relation pruner
- RL-based policy network


### Differences from existing studies
- Difference from [[DacKGR]]
	- Task definition: KGC task vs. Alleviate the KG incompleteness for mulO
