public:: true

- This theorem states the relation between all spanning trees and combinatorial Laplacian of the graph.
- Theorem
	- Consider an undirected graph $G$.
		- Each edge $v_iv_j$ is given a positive weight $C_{ij}$.
		- For any spanning tree $T$ of $G$, let $w(T)$ be the product of its edges weights.
		- Let $N^*(G)=\sum_T w(T)$.
		- Denote by $K^*(G)$ any first cofactor of $L=D-C$, where $D$ is a diagonal matrix with $D_{ii} = \sum_{j=1}^n C_{ij}$.
	- Then $N^*(G)=K^*(G)$.
- Proof
	- See ((63d29388-817b-47ee-a000-ae45c797a89d))
	- Firstly we shall see that the first cofactors of $L$ shares a common number.
	  collapsed:: true
		- Perhaps I should also learn linear system and those matrix-things again...
	- The proof plays induction on both $n$ and $m$.
	- By considering "removing one edge in $G$", we are done on induction on $m$.
- Corollary
	- If we let each edge be of weight $1$, then $K^*(G)$ would be the number of spanning trees in $G$.
	- In directed graph $G$
	  collapsed:: true
		- See ((63d29ced-b4b7-4566-82f5-716a1ea4f702))
		- Let $C_{ij}$ be the number of edges from $v_i$ to $v_j$.
		- The "spanning tree" here is the spanning trees oriented towards $v_i$.