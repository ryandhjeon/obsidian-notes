# Artificial cognition: How experimental psychology can help generate explainable artificial intelligence
#### (2021) - J. Eric T. Taylor, Graham W. Taylor
**Link**: https://link.springer.com/10.3758/s13423-020-01825-5
**DOI**: 10.3758/s13423-020-01825-5
**Code/Link**:
**Tags**: #paper
**Rating**:

### Abstract

```
Artificial intelligence powered by deep neural networks has reached a level of complexity where it can be difficult or impossible to express how a model makes its decisions. This black-box problem is especially concerning when the model makes decisions with consequences for human well-being. In response, an emerging field called explainable artificial intelligence (XAI) aims to increase the interpretability, fairness, and transparency of machine learning. In this paper, we describe how cognitive psychologists can make contributions to XAI. The human mind is also a black box, and cognitive psychologists have over 150 years of experience modeling it through experimentation. We ought to translate the methods and rigor of cognitive psychology to the study of artificial black boxes in the service of explainability. We provide a review of XAI for psychologists, arguing that current methods possess a blind spot that can be complemented by the experimental cognitive tradition. We also provide a framework for research in XAI, highlight exemplary cases of experimentation within XAI inspired by psychological science, and provide a tutorial on experimenting with machines. We end by noting the advantages of an experimental approach and invite other psychologists to conduct research in this exciting new field.
```

### INTRODUCTION

- Black box problem: Impossible to explain the model's decision
- XAI: the promise of AI at scale + urgent lack of satisfying explanations for AI decision making.
- Advance an XAI known as Artificial Cognition (Ritter et al., 2017): tradition of experimentation developed within cognitive psychology. 
- Draw parallels between the black-box in XAI and epistemic challenge faced by cognitive psychologists.
- Contribution from Psychology is low on XAI

### The black-box problem in machine learning & psychology

- After the process of deep neural network, the model is so complex that no human could explain how processing in these networks truly works.
- We have access to input and output, and mass of hidden functions must infer the decision-making process.
- This issue is the same epistemic challenge championed by cognitive pssychologists for last 150 years
- In 1868, psychologists have used behavioral experiments to infer the properties of invisible mental processes, as when Donders recorded response times and used the subtractive method to identify stages of perceptual processing and response selection. cognitive psychology has yielded robust models of perception, attention, memory, language, and decisionmaking, all without ever observing these processes directly.
- Cognitive psychologists have developed a science of behavior that works without opening its black box. cognitive psychology employs carefully crafted stimuli (input) and measures the corresponding behavior (output) to make causal inferences about the structure and function of the human mind.
- Instead of altering AI architecture or generating post hoc explanations for how AI reaches its decisions, we can develop satisfying models of mind without interfering with the AI’s black box.

### Ethical and political need for XAI

- First, why should we care if it makes good decisions?
- the parameters represent truth in a training data set, rather than truth in the world
- 1. data sets that are biased against a particular group will yield predictions that are biased against that particular group
- 2. commercial models that are trained on biased data sets will treat underrepresented groups unfairly and inaccurately
- 3. vehicles that are trained in test circuits may not generalize adequately to real roads
- 4. machines that are vulnerable to adversarial attacks may backfire or behave dangerously
- we need to understand how and why things can go wrong.

LEGISLATIVE BODIES & LAW

- THe law give citienzens a right to understand how AI makes decisions when it makes decisions on their behalf.
- France: includes the communication of paramenters, weights, and operations

SATISFACTION

- We argue that explanations must be causal, rather than correlative
- As in human psychology, correlation is insufficient to explain behavior in machine psychology.
- It is not enough to say “we think your loan was denied by the bank’s AI because your profile is low on variables x, y,and z, but we can’t be sure.”

### Machine behavior as XAI

- A large sector of XAI research aims to generate explanations through more interpretable architectures, or by introducing a second AI that examines another AI's decision and learns to generate explanations for it. 
- Explainability in AI is more AI ?!
- As of 2017, XAI and the social sciences were largely disconnected, establishing a case for an interdisciplinary approach.
- Around the same time, popular press articles began to capture public attention in the need for human-centric XAI
- I think having explanations will be good. We need better approaches to that—it should be its own field of study.

### A review of XAI for psychologists

- XAI has a blind spot that artificial cognition could help fill
- Simple models are interpretable, in many realistic settings their performance does not compete with deep neural networks (DNNs).
- XAI currently lacks the practice of causal inference by the attempted falsification of a priori hypotheses.

### Proxy models

- As a general rule, these models sacrifice some predictive power in the service of explainability
- sacrifice some predictive power to incorporate an interpretable architecture
- Even without the ability to inspect a neuron’s receptive field, abstract rules can be extracted automatically and pruned into a more digestible representation of the larger network

### Introspective models

- Introspective: Researchers are training DNNs to interpret the decisions of other DNNs
- Train a second black box to explain the first one
- AI-for-XAI adds another black box = need more explanation
- this introspective network is optimized for generating explanations according to previously observed ground truth from human agents, which may not faithfully reproduce the artificial agent’s internal state

### Correlative techniques & saliency maps

- correlative techniques are susceptible to the threat of multicollinearity: there are often many possible causes for a given correlation.
- Partial Dependence Plots (PDPs)

### SUMMARY
- What was the author's goal?
- What is the most important element of this approach?
- Can I utilize this thesis?
- Is there any other reference I would like to review?
- How can I improve this thesis?
- Is Github repository available?