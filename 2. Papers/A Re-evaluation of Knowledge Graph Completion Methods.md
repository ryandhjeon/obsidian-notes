# A Re-evaluation of Knowledge Graph Completion Methods
#### (2020) - Zhiqing Sun, Shikhar Vashishth, Soumya Sanyal, Partha Talukdar, Yiming Yang
**Link**: http://arxiv.org/abs/1911.03903
**DOI**: 
**Code/Link**:
**Tags**: #paper #KG/Evaluation 
**Rating**:

### Abstract

```
Knowledge Graph Completion (KGC) aims at automatically predicting missing links for large-scale knowledge graphs. A vast number of state-of-the-art KGC techniques have got published at top conferences in several research fields, including data mining, machine learning, and natural language processing. However, we notice that several recent papers report very high performance, which largely outperforms previous state-of-the-art methods. In this paper, we find that this can be attributed to the inappropriate evaluation protocol used by them and propose a simple evaluation protocol to address this problem. The proposed protocol is robust to handle bias in the model, which can substantially affect the final results. We conduct extensive experiments and report performance of several existing methods using our protocol. The reproducible code has been made publicly available.
```

### Notes

#### KGC Evaluation
- [[Filtered setting]]: All the known correct triplets (from train, valid, and test triplets) are removed from T′ except the one being evaluated (Bordes et al., 2013). The triplets in T′ − {t} are called [[negative samples]].

#### Evaluation Protocols
- Purpose: to decide how to break ties for triplets with the same score
	- If there are multiple triplets with the same score from the model, one should decide which triplet to pick

- <u>TOP</u>: In this setting, the correct triplet is inserted in the beginning of T'
	- Does not evaluate the model rigorously. It gives the models that have a bias to provide the same score for different triplets, an inappropriate advantage

- <u>BOTTOM</u>: Here, the correct triplet is inserted at the end of T′ 
	- Can be unfair to the model during inference time because it penalizes the model for giving the same score to multiple triplets, 
	- i.e., if many triplets have the same score as the correct triple, the correct triplet gets the least rank possible.

- **RANDOM**: In this, the correct triplet is placed randomly in T′
	- The **best** evaluation technique which is both rigorous and fair to the model. It is in line with the situation we meet in the real world: given several same scored candidates, the only option is to select one of them randomly.

#### KGC Methods
- Non-Affected: methods which give consistent performance under different evaluation protocols.
	- ConvE, RotatE, and TuckER

- Affected: This category consists of recently proposed neural-network based methods whose performance is affected by different evaluation protocols.
	- ConvKB, CapsE, TransGate2, and KBAT


- In original paper:
	- RANDOM: [[ConvE]], RotatE, and TuckER
	- TOP: [[ConvKB]], CapsE, and KBAT

#### Conclusion
- Non-Affected methods: the performance remains consistent across different evaluation protocols
- Affected methods: a considerable variation in performance.

**Strongly encourage the research community to follow the RANDOM evaluation protocol for all KGC evaluation purposes.**

