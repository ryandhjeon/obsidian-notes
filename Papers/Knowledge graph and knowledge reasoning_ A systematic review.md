# Knowledge graph and knowledge reasoning: A systematic review
#### (2022) - Ling Tian, Xue Zhou, Yan-Ping Wu, Wang-Tao Zhou, Jin-Hao Zhang, Tian-Shu Zhang
**Link**: https://linkinghub.elsevier.com/retrieve/pii/S1674862X2200012X
**DOI**: 10.1016/j.jnlest.2022.100159
**Code/Link**:
**Tags**: #paper #KG/Survey
**Rating**:

### Abstract

```
The knowledge graph (KG) that represents structural relations among entities has become an increasingly important research field for knowledge-driven artificial intelligence. In this survey, a comprehensive review of KG and KG reasoning is provided. It introduces an overview of KGs, including representation, storage, and essential technologies. Specifically, it summarizes several types of knowledge reasoning approaches, including logic rules-based, representation-based, and neural network-based methods. Moreover, this paper analyzes the representation methods of knowledge hypergraphs. To effectively model hyper-relational data and improve the performance of knowledge reasoning, a three-layer knowledge hypergraph model is proposed. Finally, it analyzes the advantages of three-layer knowledge hypergraphs through reasoning and update algorithms which could facilitate future research.
```

### Notes

[[KG reasoning]]: Improves the completeness of KG by inferring new knowledge.

![[Pasted image 20230129162152.png]]

#### Summarize of the representation, storage, and essential technologies of KG
KR Learning (KRL)
Knowledge Storage (KS)
KG Construction (KGC)
Knowledge Updating (KU)
Knowledge Reasoning

KGC = Knowledge extraction (KE), Knowledge fusion (KF), and Knowledge processing (KP).

WWW Consortium (W3C)
	- Resource Description Framework (RDF)
	- RDF schema (RDFS)
	- Web Ontology Language (OWL) description languages
	**Unable to represent a large amount of the real-world data**
	**Difficult to mine and analyze the semantic relationships between knowledge entities**

Knowledge Storage (KS)
	- RDF databases: Jena [8]、RDF4J [9], and gStore [10]
	- Relational databases (RDBs): PostgreSQL [11] and MySQL [12]
	- Graph databases (GDBs): Neo4j [13], JanusGraph [14], and HugeGraph [15]


#### Fine-grained classification of KG reasoning

![[Pasted image 20230129163504.png]]

