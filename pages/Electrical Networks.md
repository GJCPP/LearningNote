public:: true

- Definitions
	- An ``electrical network`` is a directed multigraph, where the direction of an edge is just its orientation.
	- Each edge $e_i$ is assigned a real number $r_i$, called `resistance`. Edges are also called 
	   `resistors`.
	- Subject to `Ohm's law`: $w_i=\frac{p_i}{r_i}$
	  which states that, if there is a `potential difference` $p_i$ between endvertices of $e_i$, say $a_i$ and $b_i$, then an `electrical current` $w_i$ will flow from $a_i$ to $b_i$.
	  Note that $r_i^{-1}$ is defined as the `conductance`.
	- Subject to `Kirchhoff's laws`
		- Kirchhoff's potential law
		  id:: 63ca5c0d-bbbe-4ca7-a50f-6e3aff136dea
		  collapsed:: true
			- The potential differences round any cycle $x_1x_2\cdots x_k$ sum to zero:
			  $$p_{x_1x_2}+p_{x_2x_3}+\cdots +p_{x_{k-1}x_k}+p_{x_kx_1}=0$$
		- Kirchhoff's current law
		  id:: 63ca5c20-adf4-4c19-8475-0d212718ab1b
		  collapsed:: true
			- This law **postulates** that the total current outflow from any point is zero:
			  $$w_{ab}+w_{ac}+\cdots+w_{au}+w_{a\infty} = 0$$
			- where $w_{a\infty}$ denotes the current that leaves the network at $a$. (analogously, $w_{\infty a}$ the one entering the network at $a$)
		- Easy to see that ((63ca5c0d-bbbe-4ca7-a50f-6e3aff136dea)) is equivalent to state that we can assigned absolute potentials $V_a$ to each vertex, and the potential between vertices $a$, $b$ would be $p_{ab} = V_a - V_b$.
		- Note also that ((63ca5c20-adf4-4c19-8475-0d212718ab1b)) is an assumption, and cannot be deduced from other definitions.
	- In the most fundamental problems, current is allowed to enter the graph only at a single vertex $s$, the `source`, and leave only at another vertex $t$, the `sink`.
	- If the size of current entering the graph is $w$, and the potential difference between $s$ and $t$ is $p$, then by Ohm's law, $r = p/w$ is the *total resistance* of the network between $s$ and $t$.
- Basic facts
  collapsed:: true
	- Principle of superposition
	  id:: 63ca71ef-8e00-4f61-8ac9-02520b57a8d1
	  collapsed:: true
		- Any combination of solutions is again a solution.
		- Note that `solution` is a concept in linear system, instead of simply meaning "a way of assigning current/potential".
	- Solution for multiple sources/sinks can be obtained by superposing flows belonging to one source and sink
		- Can be deduced from ((63ca71ef-8e00-4f61-8ac9-02520b57a8d1))
	- There is exactly one solution for a given electrical network
		- The uniqueness can be deduced from ((63ca71ef-8e00-4f61-8ac9-02520b57a8d1)).
		  It suffices to only prove the uniqueness of the solution in a basic $s$-$t$ electrical network, which is easy.
		- The proof of the existence of a solution is much more complex, and is constructive. See ((63cb9126-d516-4e19-9aab-1e6293c0ed07)) for details.
		- Some insights that might help understanding this proof
			- In a spanning tree, there is exactly one path from $s$ to $t$, with each edge given a size of current $1$.
			- On each spanning tree, there is but one explicit solution. Adding them together makes one explicit solution on original network.
			- Why spanning tree, not path: a solution on a path does not contain potential of vertices outside of the path.
	- Star-triangle transformation
	  collapsed:: true
		- ((63cb91e7-d010-44b1-a624-d9955cfe2889))
		- Assuming that no current is allowed to enter/leaving at $v$.
		- See ((63cb8ef7-b37e-4514-a8bf-3237d806e105))
	- If the conductances of edges are rational and a current of size $1$ goes through the network, then the current in each edge has rational value.
		- A corollary from the constructive proof of the existence of solution.
		- See ((63cb9126-d516-4e19-9aab-1e6293c0ed07))
	- If some wires are cut, the total resistance does not decrease; if shorted, the total resistance does not increase.
- On solving the electrical network
	- Firstly we show how to express the problem in matrices and vectors.
	  collapsed:: true
		- Assume that our electrical network is $G^\prime$ with $V(G^\prime)=\{v_1,v_2,...,v_{n-1}\}$ and $E(G^\prime)=\{e_1,e_2,...,e_{m^\prime}\}$.
		- Assume that the graph is connected and there is a voltage generator ensuring that the potential difference between $v_i$ and $v_j$ is $g_i-g_j$ volts for $1\leq i\leq j\leq k$.
		- Let's construct a new graph $G$ from $G^\prime$ by adding a vertex $v_n$ that joins $v_1, ..., v_k$ by edges $e_{m^\prime+1}, ..., e_{m^\prime+k}$, each new edges of resistance $0$.
		  collapsed:: true
			- This vertex is used to control the potential of the $k$ vertices.
			- The resistance $0$ will make any current passing through that edge unrelated to the potential on two ends. So we can set the potential difference across that edge freely, and thus control the desired potential differences between the first $k$ vertices.
		- Let $n=n^\prime + 1$ and $m = m^\prime + k$, i.e. the new number of vertices and edges in the graph. And of course $V(G) = \{v_1,v_2,...,v_n\}$ and $E(G) = \{e_1,e_2,...,e_m\}$.
		- The following three equations describe the electrical network
			- **1**. $B\vec{w}=\vec{0}$ states the Kirchhoff's current law.
			  collapsed:: true
				- The vector $\vec{w}=(w_1,w_2,...,w_m)^T$ is the current vector.
			- **2**. $C^T\vec{p}=\vec{0}$ states the Kirchhoff's potential law.
			  collapsed:: true
				- The vector $\vec{p}=(p_1,p_2,...,p_m)^T$ is the potential vector.
				- $C$ is a $n\times m$ matrix whose column vectors form a basis of cycle space of $G$.
				- The basis of cycle space of $G$ could be taken as the [fundamental cycle vectors](((63d12b86-0777-4c7f-b560-c2ceecae4eeb))) of any spanning tree of $G$.
			- **3**. $\vec{p}=R\vec{w}+\vec{g}$ states the potential relationship.
			  collapsed:: true
				- $r_i$ is the resistance of $e_i$.
				- $R=(R_{ij})$ is the $m\times m$ diagonal matrix with $R_{ii} = r_i$.
				- $\vec{g}$ is the extra requirement of potential, with last $k$ entries being $g_1, g_2, ..., g_k$ and others zero.
	- Then we provide method to solve it.
	  collapsed:: true
		- Select any spanning tree $T$ of $G$ and split $C_1(G)$ as $E_T+E_N$.
		  collapsed:: true
			- $E_T$ is the subspace spanned by tree edges, and $E_N$ by chords.
		- Take the columns of $C$ as the fundamental cycles.
		- Let $\vec{w}=({\vec{w_T}\atop \vec{w_N}}) \text{ and } \vec{p}=({\vec{p_T}\atop \vec{p_N}})$.
		- Let $\tilde{B}$ be the matrix obtained from $B$ by omitting the last row, and
		  collapsed:: true
		  $$C=({C_T\atop C_N})\text{ and }\tilde{B}=(B_TB_N)$$
			- Since the columns of $C$ are fundamental cycles, we can asume wlog that $C_N$ is $I_{m-n+1}$, i.e. one chord on a fundamental cycle at one time.
		- $B_T$ is invertible, and
		  collapsed:: true
		  $$C_T=-B_T^{-1}B_N$$
			- Proof of $B_T$ being invertible.
			  collapsed:: true
				- Since $v_n$ is omitted, there is one column with only one nonzero element, say the one corresponding to $e_1$.
				- Using that column, we play Gauss elimination on other columns. Some columns remaining to have two nonzero elements while some not.
				- We remark that the columns with exactly non-zero elements are the ones adjacent to $e_1$.
				- Any all-zero column appears in this elimination would mean a cycle. And if the elimination terminates with some columns having more than one non-zero elements, it means $T$ is not connected.
			- Observation of the equation.
			  collapsed:: true
				- A fascinating fact.
				- Essentially we are recovering information of $B_N$ from $C_T$ and $B_T$.
				  collapsed:: true
					- $B_N(v, e)$ asks that whether a given edge $e\in E_N$ has an endpoint $v$ on tree.
					- $C_T(e, e_T)$ tells that whether the tree edge $e_T$ is oriented as the chord $e$.
					- $B_T(v, e_T)$ tells that whether $e_T$ is adjacent to $v$.
		- Then $\vec{w}=-C(C^TRC)^{-1}C^T\vec{g}$
			- This and its proof are given by ((63d1dde4-8996-494b-bc71-26a376a357a9))
		-
- Theorems
	- [[Kirchhoff's matrix tree theorem]]