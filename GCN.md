# GCN

![[Pasted image 20230407204804.png]]

- New vector representation of a node: Average of its neighbors passed through non-linear function.
![[Pasted image 20230407205117.png]]
![[Pasted image 20230407205200.png]]

- Can train to output to dimensionality 1, for binary cross entropy with backpropagation to train all the parameters.

 - $x$ layer GCN = $x$ hop node
