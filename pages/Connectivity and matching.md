public:: true

- ((63d33f00-ac9a-43e3-b6ca-7b628fdbb585))
- ### Definitions on connectivity
	- connectivity $\kappa(G)$
	  collapsed:: true
		- $k$-connected
			- $G$ is $k$-connected either
			  1. $G$ is $K_{k+1}$
			  2. To disconnect $G$, you need to remove **at least** $k$ vertices.
			- Note that to be $k$-connected, you need to have **more than** $k$ vertices.
		- The maximal value of $k$ for which $G$ is $k$-connected is denoted by $\kappa(G)$
	- edge-connectivity $\lambda(G)$
	  collapsed:: true
		- $k$-edge-connected
			- $G$ has at least two vertices
			- To disconnect $G$, you need to remove **at least** $k$ edges.
		- The maximal value of $k$ for which $G$ is $k$-edge-connected is denoted by $\lambda(G)$
	- block
	  collapsed:: true
		- ((63d3ab23-252a-4dc8-9690-f7db115d3de9))
	- $bc(G)$: block-cutvertex graph of $G$
	  collapsed:: true
		- Decompose $G$ into blocks $B_1, ..., B_p$
		  collapsed:: true
			- 1. $E(G) = \cup_1^p E(B_i)$
			- 2. for $i\neq j$, $E(B_i)\cap E(B_j)=\emptyset$
		- Let $bc(G)$ be the bipartite graph
		  collapsed:: true
			- vertices are $B_i$ and all the cutvertex of $G$.
			- each cutvertex of $G$ is joined to the blocks containing it.
		- Facts:
		  collapsed:: true
			- $bc(G)$ is a tree.
			- Each endvertex of $bc(G)$ is a block of $G$, called `endblock` of $G$.
			- A block is  an endblock iff it contains exactly one cutvertex.
			- Unless $G$ is $K_2$ or is $2$-connected, it has at least two endblocks.
		-
- ### Definitions on matching
	- matching
	  collapsed:: true
		- set of independent edges
	- stable matching
		- each vertex in $V_1$ has a preference over its neighbors in $V_2$, and so does vertex in $V_2$
		- $a\in V_1$ and $b\in V_2$ are not matched, only if at least one of them is matched to its "more preferred" one.
		-
- ### Basic facts
	- $\kappa(G)\leq \lambda(G)\leq \delta(G)$
	  collapsed:: true
		- Given that $G$ is nontrivial.
		- The right side is trivial.
		- The left side can be checked by:
		  collapsed:: true
			- If $G$ is a complete graph, they are equal.
			- Otherwise, given an edge cut $\{x_1y_1, ..., x_ky_k\}$
				- If $\{x_1, ..., x_k\}$ is a vertex cut, we are done.
				- Otherwise each vertex $x_i$ has degree at most $k$, and thus exactly $k$.
				  collapsed:: true
					- This is not obvious, but be checked by calculating the upper bound of their total degree.
					- In case of multigraph, this can be replaced by "has at most $k$ neighbours"
				- Thus removing neighbours of $x_1$, we are done.
	- Any two blocks have at most one vertex in common.
	- ((63e2744d-eb1e-4c4f-a019-039dc7816936))
	  collapsed:: true
		- Proved by constructing one.
		- Each $v\in V_1$ tries to match with its most preferred one.
		- Each $u\in V_2$ accept its most preferred one's request once it receives (if it is currently matched, tell that one to re-match).
		- This algorithm will stop: each $v\in V_1$ would either stopped being matched, or it will be denied by every vertex in $V_2$.
		- The result is stable. Trivially,
		- An interesting fact: no matter the order of proposing, this algorithm stops at a same stable matching.
	- ((63e2777a-70a9-4633-ad62-7094ba094a73)) Let $M$ and $M^\prime$ be two stable matchings in a bipartite graph, and let $C$ be a component of the subgraph $H$ formed by the edges of $M\cup M^\prime$. If $C$ has at least three vertices, then it is a preference-oriented cycle. In particular, if $aA, bB \in M$ and $aB \in M^\prime$, then $a$ prefers $A$ to $B$ iff $B$ prefers $a$ to $b$.
		- e.g. in circle $abcdefa$
			- if $a$ prefers $b$ to $f$, then $b$ prefers $c$ to $a$, $c$ prefers $d$ to $b$, etc.
		- The proof is done by
			- 1. prove that it is circle (augmenting path)
			- 2. check it is preference-oriented (easy)
	- Various stable matchings select exactly the same set of vertices to be matched.
	  collapsed:: true
		- corollary by ((63e2777a-70a9-4633-ad62-7094ba094a73))
		-
	- All stable matchings have a same cardinality.
- Theorems
	- [[Menger's theorem]]
	- [[Hall's theorem]]
	  id:: 63d690a0-0f20-4df5-ae71-c5553d0ab96e
	- If every antichain in a (finite) partially ordered set $P$ has at most $m$ elements, then $P$ is the union of $m$ chains.
	  collapsed:: true
		- See ((63dbd00a-d1ec-4506-8258-f66c0a8f692b))
		- Insights
			- Given $m$ much larger than any possible antichain could be, we can still find $m$ chains that combine into $P$ by taking empty sets into account.
			- Given now a $P$ with its maximal antichain of size $m$.
			- Remove a longest chain $C$ from $P$, and in $P-C$ must one find an antichain of size $m$, and is maximal in also $P$.
			- The essence is then to use $S$ to literally construct $m$ chains for $P$. Which, here, is achieved by combining the upper and lower shadows.
			-
	- [[Tutte's theorem]]
	-