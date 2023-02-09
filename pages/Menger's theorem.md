public:: true

- Theorem
	- ((63d54bbe-a2b1-4b9d-80e5-fb3950aa81de))
		- Part $1$ is called "vertex form"
		- Part $2$ is called "edge form"
	- It is an analogue of the max-flow min-cut theorem for undirected graph.
- Proof
	- An very easy one: use the max-flow min-cut theorem with vertex capacity / edge capacity.
	  collapsed:: true
		- See [[Max-Flow Min-Cut Theorem]] and its remark.
	- A direct [proof](((63d54a99-628b-4641-8c78-6ec9fd11ce7a))) of the vertex form
		- Consider the minimal $k$ that has counterexample.
		- Consider the $G$ with minimal edges that is a counterexample of $k$.
			- That is, there is a set of $k$ vertices separating $s$ and $t$, yet there are at most $k-1$ independent $s$-$t$ paths.
			- For obviously, if there are $k$ independent $s$-$t$ paths, $\kappa(G)\geq k$.
		- Then in $G$
			- No vertex is adjacent to both $s$ and $t$.
			- Any set $W$ of $k$ vertices separating $s$ and $t$, the vertices in it must either all adjacent to $s$, or all adjacent to $t$.
			  collapsed:: true
				- Otherwise let's contract $s$ side of the component in $G-W$ to $s^\prime$ and join it to every vertices in $W$, and name the new graph $G_s$.
				- $G_s$, with less edge than $G$, can be used to show that there are $k$ independent $s$-$t$ paths in $G$.
			- Take a shortest $s$-$t$ path $sx_1x_2\cdots x_lt$.
				- $l\geq 2$
				- Let $W_0$ be a cut in $G-x_1x_2$. It must be of size $k-1$.
				- $W_1=\{x_1\}\cup W_0$, this cut of $G$ suggests that $s$ is adjacent to all vertices in $W_0$.
				- $W_2=\{x_2\}\cup W_0$, this cut of $G$ suggests that $t$ is adjacent to all vertices in $W_0$.
				- Thus, $s$ and $t$ has at least one common neighbour.
				-