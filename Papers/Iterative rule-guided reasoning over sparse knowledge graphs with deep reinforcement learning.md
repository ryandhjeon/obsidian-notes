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

- States: We want to implement the state that encodes the observed information as much as possible. Multi-hop reasoning process considers; corrent entity $e_t$, query relation $r_q$, previous historical reasoning process $h_t$.

- Actions: The set of possible actions. $A$ of step $t$ consists of the outgoing edges of $e_t$ in KGs. A 'self-loop' edge is appended to every $A_t$, as the search process is within a given step, acting as a 'stop' action.

- Transition: Set the maximum hop count to $T$, and if the agent cannot reach the target within the limit, the transition will terminate at the state $s_t$. 

- Rewards: If the agent reaches the correct target entity at the end of the search, a terminal reward of 1 or 0 otherwise. 

- For more effcient [agent path searching], design the specific [agent reward function] to achieve better performance.

*Policy network*
- Policy network is parameterized by state information, global context and the pathfinding history. 

- Action $a_t$ is represented as the concatenation of the relation embedding $r \in {R^d}$  and target entity embedding $e \in {R^d}$ where every entity and relation in the KG is assigned a dense vector embedding with the same dimension d. 

- $h_t$ covers the sequence of observations and actions. $h_t$ = LSTM($h_{t-1}, a_{t-1}$)

- Encode the action space by stacking the embeddings of all actions in $A_t: A_t \in {R^{|A_t|\times2d}}$

- To avoid the dying ReLU, LeakyReLU with negative input slope $\alpha = 0.01$ is used as nonlinearity

*Rule induction from the KG*
- A rule head is denoted by r(...), rule body is denoted by the conjunction of atoms $b_1$(...), ... , $b_n$(...)

- Quality of each rule is mesaured with its [confidence score]. #(x, y) denotes the number of facts corresponding to the condition.
![[Pasted image 20230328140909.png]]

- Example: For $$r_{target}(a,b) \Leftarrow r_1(a,e) \land r_2(b,e)$$, turn $r_2(b,e)$ into $r_{2}^{-1}(e,b)$, and as a result, $$r_{target} \Leftarrow (r_1, r_{2}^{-1})$$If $r_1 \to r_{2}^{-1}$, could be composed as $r_{target}$ if a path satisfies the sequence of relations

*Reward design*
- 2 parts for the reward mechanism of an agent

1. Rule guidance reward $R_r$
2. Hit target reward $R_h$

- If the path inferred by the RL agent matches any of the preceding logic rules retrieved from the rule miner, the corresponding score of the rule is added to the total reward as a rule guidance reward $R_r$

- Additionally, add a Laplace smoothing, $p_c = 5$ for the confidence score with the final [rule guidance reward] $R_r$

- $R_h$: [hit target reward], rewards 1 if the predicted triple $\epsilon = (e_s, r_q, e_T) \in KG$

- Otherwise, for [soft reward] whose correctness is unknown, the embedding function of $\epsilon$ is used to measure the reward as a hit target reward $R_h$
$$R_h = \mathbb{I}(\epsilon \in KG) + (1-\mathbb{I}(\epsilon \in KG))f(\epsilon)$$

- $\mathbb{I}$ is an indicator function, $f(\epsilon)$ is a composition function for reward shaping using embeddings

- Final reward function, $R_{total}$ combines the $R_r$ and $R_h$ using a constant factor $\lambda$
$$\lambda : R_{total} = \lambda R_r + (1-\lambda)R_h$$ 
![[Pasted image 20230328144918.png]]

*Dynamic Path Completion*
- Sparse KG, the performance of the model during reasoning reduces significantly.

- Strategy dynamically allocates additional space to augment the original action space of the RL agent. Uses the RL agent with the rule guidance during the reasoning process. 

- The candidate set of additional actions: $$C_t = {(r,e)|r \in R \land e \in \mathcal{E} \land (e_t, r, e) \notin \mathcal{T} }$$
- $C_t$ is too large, as it is obtained by means of actions in $C_t$, so we adopt an approximate [pruning strategy]. 
 ![[Pasted image 20230328151017.png]]

**Pruning strategy**
1. Filter out <u>relations with the highest probability</u> using $P(r|s_t)$
2. Then select <u>entities with the highest probability</u> for the filtered relations using $P(e|r, s_t)$
3. Now the model prefers the relation $r$ that are <u>frequently occurred rather</u> than considering the <u>joint probability of the action</u>. 
4. Use dropout technique. It masks some outgoing relations randomly for the RL agent in the sampling step of REINFORCE, which gives randomized search effect.

- [Global information extraction]: Activity of obtaining the rules and corresponding confident scores. 
	- This helps RL agent to make decisions with the guidance from an overview of the KG. 
	- Higher [rule guidance rewards] is given to the path sequence that follows the logic rules. This guides the selection of additional action space, so that the path of completion more consistent with [global information].

**Dynamic Completion Steps**
1. When query $(e_s, r_q, ?)$ is given, RL agent is applied to explore over the KG environment.
2. When RL agent encounters the missing path in entity $i$, the [mined rules] are retrieved. 
3. If there exists the rule that its head matching query $q$, the rule $R_t$ and its [corresponding confidence score] is obtained.
$$R_t : r_{q}^{rule}(X,Y) \Leftarrow b_1(X, A_2)\land...\land b_n(A_n,Y)$$
4. If more than one rule is satisfied simultaneously, both rules are activated, and assume that the single rule that has [higher confident score] is activated to compose the path.
5. To guide the [path search] dynamically with the rules, the matrix $\mathbb{C}^{|R|\times|R|}$ and identity matrix $\mathbb{I}^{|R|\times|R|}$ are constructed for the entity. They represent the additional guidance of the rules and the normal relations. If the rule atom $b$ match the relation sequence $r$ of the reasoning path, the [confidence score] of the corresponding rule to the value of $c_{ij} \in \mathbb{C}$ is assigned.

![[Pasted image 20230328154743.png]]

6. The [higher confidence score] of the rule that the path matches, the greater the corresponding [relation weight] obtained with the guidance of the rules. 
7. Now, we can measure the [liklihood] of the path complement candidate set over all relations in each state, and the attention vector of each relation in the candidate set $w$ can be defined and normalized
$$$$



