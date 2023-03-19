# Explaining Deep Learning Models Through Rule-Based Approximation and Visualization
#### (2021) - Eduardo Soares, Plamen P. Angelov, Bruno Costa, Marcos P. Gerardo Castro, Subramanya Nageshrao, Dimitar Filev
**Link**: https://ieeexplore.ieee.org/document/9107404/
**DOI**: 10.1109/TFUZZ.2020.2999776
**Code/Link**:
**Tags**: #paper #XAI
**Rating**:

### Abstract

```
This paper describes a novel approach to the problem of developing explainable machine learning models. We consider a Deep Reinforcement Learning (DRL) model representing a highway path planning policy for autonomous highway driving [1]. The model constitutes a mapping from the continuous multidimensional state space characterizing vehicle positions and velocities to a discrete set of actions in longitudinal and lateral direction. It is obtained by applying a customized version of the Double Deep Q-Network (DDQN) learning algorithm [2]. The main idea is to approximate the DRL model with a set of IF...THEN rules that provide an alternative interpretable model, which is further enhanced by visualizing the rules. This concept is rationalized by the universal approximation properties of the rule-based models with fuzzy predicates. The proposed approach includes a learning engine composed of 0-order fuzzy rules, which generalize locally around the prototypes by using multivariate function models. The adjacent (in the data space) prototypes, which correspond to the same action are further grouped and merged into so-called "MegaClouds" reducing significantly the number of fuzzy rules. The input selection method is based on ranking the density of the individual inputs. Experimental results show that the specific DRL agent can be interpreted by approximating with families of rules of different granularity. The method is computationally efficient and can be potentially extended to addressing the explainability of the broader set of fully connected deep neural network models.
```

### Notes

**Q. Is it Model specific? or Model Agnostic?**

#### Introduction

The transparency of the trained machine learning models which is needed for validation, verification, and certification [3]–[8].

The demand of understandable models involves interpretability and explainability of a trained agent in order to fully understand the knowledge encoded in them.

Black box models are not transparent even with a impressive classification and approximation accuracy.

#### GOAL 
This paper proposes a new explainable self-organizing approach to transform a trained deep neural network model into a set of IF . . . THEN rules. We use a DRL model of the path planning policy for highway self-driving to simulate data corresponding to driving scenarios. 

The model maps the set of continuous state variables characterizing the position and velocities of the ego vehicle (EV) and the surrounding vehicles on a divided highway into a set of discrete actions in longitudinal and lateral direction.


#### Method

R^n: n is number of inputs
R^A: A is number of actions
i: i is the specific data sample/point k
N: N is the number of training data samples

1. Analyze mutual proximity of the data
2. 