- Uses Heterogeneous Graph, where Nodes and Edges are different types
- Knowledge Graph: KG = Source node, Relation type, Destination node 
![[Pasted image 20230407211030.png]]

- GCN: Cannot handle this, as we don't want to treat all nodes as the same, and all relations as the same.

![[Pasted image 20230407211151.png]]
- Aggregating B and C for node A doesn't make sense.
- RGCN handles this by having different projection matrices for each unique type of triple
- W matrix #1: Person - block - person
- W matrix #2: Person - follow - person
- Specific to the type of triple. (Not specific nodes)
- ![[Pasted image 20230407211521.png]]
- $\sum_{r\in{R}}$ : $r$ represents the relation type.
- $\sum_{j\in{N^r_i}}$ : $r$ is on $N$ the neighborhood, it's because during the nextsum, you only consider the neighbors of a particular type $r$.
- $W_r^{(l)}$ has $r$ in it. Each relationtype has its own projection matrix. In RGCN, each layer has $r$ (number of relation types) of $W$, while regular GCN layer had one $W$
- $W_0^{(l)}$ : Self connection. When updating itself, giving special own type and special its own projection matrix. 

So, we still gather neighbors, aggregate them, and project them, and pass them to non-linearity. However, the aggregating and projection based on the relation type first. The idea is projection matrices put them in the same project space, so when you sum them together, you can make some semantic sense of what's going on. 

The relations can be canceled out if they are in the same projection space. That's why we want diffent relation types in different project space. 

RGCN has more parameters than GCN as each relation type have their own $W$. It can be a problem if there are many relation types, and also especially they are rare.

2 ways to regularizing the issue.
1. Basis decomposition: 
   ![[Pasted image 20230407230631.png]]
   - $B$: You specify the [numer of unique] $W$s you want to have for the layer. 
   - Then, each of the $W_r$ is calculated by combining those components $V_b^{(l)}$ linearly, so they learn the coefficient for each of the components.
   - With no regularization, each relation type has its own projection matrix. But with the maximal regularization you can specify the number of shared weight matrix. 
	   - Ex1: 1 shared $W$ for each layer, but each of the relation types within learn some coefficient to scale it
	   - Ex2: We have 100 relation types, but only want 2 basis. Then each of the 100 relation types will learn 2 coefficients. 1 to scale the first, 1 to scale the second. Which is a linear combination of number of components. (Weight sharing scheme)

2. Block diagonal decomposition
	![[Pasted image 20230407231717.png]]
	- Takes small matrices and stacks them diagonally in a bigger matrix. 
	- The idea is many of the values of the matrix will be zero.
	- There are variables that are strongly interconnected within the group, but don't have much interaction outside of the group. 
		- Ex. The height and weight vs. Political interaction might be interacting within one another, but not each other. Which codify the interaction of two groups as 0.
	- At the end of the day, we just want to reduce the number of the parameters in the matrices, so they dont overfit.