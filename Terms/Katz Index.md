# Katz Index

Counts all possible paths between two specific nodes

![[Pasted image 20230420150819.png]]

There is an interesting property of the adjacency matrix A where ith power of that matrix indicates if there is a path of length i between two nodes u and v. The β term is a kind of normalization constant where we can choose what path lengths should matter the most (i.e. short or long).

The Katz index is **biased** and will generate higher similarity scores for nodes with higher node degrees. To overcome this problem, **LHN similarity metric** was proposed that takes this bias into account:




REFERENCE
https://towardsdatascience.com/feature-extraction-for-graphs-625f4c5fb8cd

