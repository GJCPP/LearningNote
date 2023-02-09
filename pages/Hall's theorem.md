public:: true

- Theorem
	- Consider a bipartite graph $G$ with vertex sets $V_1$ and $V_2$.
	- It has a complete matching from $V_1$ to $V_2$ iff
	  $$|\Gamma(S)| \geq |S| \text{ for every } S \subseteq V_1$$
- Proof
	- Insights on [the third proof](((63d7e64a-3c44-4af4-98c8-a23ca4612dc4)))
		- For any $G$ satisfying the condition, we could find a minimal subgraph spans it such that it still satisfy the condition.
		- If we remove edge $a_1x$, $|\Gamma(A_1\backslash \{a_1\})| < |A_1\backslash \{a_1\}|$. This is guaranteed by how we choose $A_1$.
		- Same holds for $a_2$.
		- Consider what happens for $A_1\cup A_2$. Adding two edges joining the same vertex could not save it.
- Collary
	- A regular bipartite graph has a complete matching.
		- Which suggests that, for any group $G$ and its subgroup $H$, we can find $g_1, g_2, ..., g_m$ such that:
			- $\bigcup_i g_iH = \bigcup_i Hg_i = G$
	- ((63d7ea7d-582c-402f-97be-826955299ca6)) For bipartite graph $G = G_2(m,n)$
		- If for every $S_1 \subseteq V_1$, $|\Gamma(S)|\geq |S|-d$.
		- Then $G$ contains $m-d$ independent edges.
		- (and vise versa)
	- ((63d7ebf1-5c94-4155-a6f1-51a69ae2439d)) For bipartite graph $G=G_2(m,n)$
		- Let $h$ be the maximal number of independent edges.
		- Let $i$ be the maximal number of independent vertices.
		- Let $j$ be the minimal number of edges and vertices covering all the vertices.
		- Then $i = j = m+n-h$. Note that here $m+n$ is the number of vertices.
		- Proof
		  collapsed:: true
			- See ((63d7ebf1-5c94-4155-a6f1-51a69ae2439d))
			  collapsed:: true
				- First paragraph means $h+(n+m-2h) = j$.
				- In third paragraph, if such a $S$ is not exist, this mean we have $h+1$ independent edges.
	- ((63da6dd5-390e-4a9d-b464-1c222103f684)) For bipartite graph $G$
		- Let $V_1=\{x_1, ..., x_m\}$ and $V_2=\{y_1,...,y_n\}$.
		- Given demands $d_1, ..., d_m$ on $V_1$.
		- $G$ contains subgraph $H$ such that $d_H(x_i)=d_i$ and $0\leq d_H(y_i)\leq 1$ iff
		  $$|\Gamma(S)| \geq \sum_{x_i\in S}d_i$$
		- Insights
			- The corollary tries to "marry" $x_i$ to $d_i$ $y_j$s.
			- By repeat $x_i$ for $d_i$ times, this equals Hall's Theorem.
- General form of Hall's theorem
	- ((63da7017-ddf7-4788-9c6f-3ec985206bcf))
	- This describes a general matching with defect. Each $x_i$ can have at most $d_i$ $y_j$, while $y_j$ can belong to at most $e_j$ $x_i$ at the same time.
	- $d$ is the number of defect that tolerates. Letting $d$ equals $0$ would make $d_H(x_i)=d_i$ as well as $y_j$.
	- The proof constructs a network, and by enumerating its cut, it verifies the condition by "capacity of cut must be greater than value of flow".
	-