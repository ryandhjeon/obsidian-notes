# Iterative rule-guided reasoning over sparse knowledge graphs with deep reinforcement learning
#### (2022) - Yi Xia, Mingjing Lan, Junyong Luo, Xiaohui Chen, Gang Zhou
**Link**: https://linkinghub.elsevier.com/retrieve/pii/S0306457322001492
**DOI**: 10.1016/j.ipm.2022.103040
**Code/Link**:
**Tags**: #paper
**Rating**:

### Abstract

```
In recent years, reasoning over knowledge graphs (KGs) has been widely adapted to empower retrieval systems, recommender systems, and question answering systems, generating a surge in research interest. Recently developed reasoning methods usually suffer from poor performance when applied to incomplete or sparse KGs, due to the lack of evidential paths that can reach target entities. To solve this problem, we propose a hybrid multi-hop reasoning model with reinforcement learning (RL) called SparKGR, which implements dynamic path completion and iterative rule guidance strategies to increase reasoning performance over sparse KGs. Firstly, the model dynamically completes the missing paths using rule guidance to augment the action space for the RL agent; this strategy effectively reduces the sparsity of KGs, thus increasing path search efficiency. Secondly, an iterative optimization of rule induction and fact inference is designed to incorporate global information from KGs to guide the RL agent exploration; this optimization iteratively improves overall training performance. We further evaluated the SparKGR model through different tasks on five real world datasets extracted from Freebase, Wikidata and NELL. The experimental results indicate that SparKGR outperforms state-of-the-art baseline models without losing interpretability.
```

### Proposed model

- Differ from embedding-based methods: Just obtain $e_o$, and give essential supporting paths over KG as evidences of the reasoning results

*RL*
- Applying RL as the <u>training algorithm</u> of a <u>sequential decision model</u>, the process of multi-hop sequential reasoning in the KG can be modeled as [[Markov decision process]] (MDP)

- RL sequentially selects an outgoing edge $l$: direction of maximum probability, and iterates until it reaches the target entity.

- MDP supplies a mathematical framework for modeling sequential decision process with the interaction between the RL agent and the KG environment. 

- States: We want to implement the state that encodes the observed information as much as possible. 