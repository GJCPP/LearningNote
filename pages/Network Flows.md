public:: true

- Notations
	- ((63d32d20-710e-4dfe-aabc-142bd9054939))
	- $\Gamma^+(x)=\{y\in V:\vec{xy}\in \vec{E}\}$
	  collapsed:: true
		- All edges coming out of vertex $x$.
		- Similarly, $\Gamma^-(x)=\{y\in V:\vec{yx}\in \vec{E}\}$
	- $v(f)$ is call the value of flow $f$
	- $\vec{E}(X,Y)=\{\vec{xy}\in \vec{E}:x\in X, y\in Y\}$
	- For any $g:\vec{E}\to \mathbb{R}$, define $g(X,Y)=\sum g(x,y)$
	  collapsed:: true
		- The sum over $\vec{E}(X,Y)$
	- An edge-cut separating $s$ and $t$
	  collapsed:: true
		- For some subset $S$ of $V$, if it contains $s$ but not $t$.
		- Then $\vec{E}(S,\bar{S})$ is called a cut separating $s$ and $t$.
	- Capacity restrictions on vertices
	  collapsed:: true
		- a function $c : V-\{s,t\}\to \mathbb{R}^+$
		- $\sum_{y\in \Gamma^+(x)} f(x,y) \leq c(x)$
		- That is, the amount of flow passing through $x$ cannot exceed $c(x)$.
	- A vertex-cut separating $s$ and $t$ (c.f. [here](((63d33bd9-c97e-4911-b0df-77e7884e5e5a))))
		- A vertex-cut is a subset $S$ of $V-\{s,t\}$
		- No positive flow from $s$ to $t$ can be define on $G-S$
- Basic facts
  id:: f328e41a-6f00-4f06-97ad-40421d98bb97
	- The existence of a maximal flow
	  id:: 63d330ae-be6b-4e7e-8537-6b5be1cd0b58
	  collapsed:: true
		- The value of flow is upper bounded.
		- The flow $f$ can be viewed as a vector in a subset of space $\mathbb{R}^{\vec{E}}$.
		- The value of $f$ is a continuous function of $f$.
		- Thus the value of $f$ must be convergent and there exists a $f$ that achieves this value.
	- [[Max-Flow Min-Cut Theorem]]
	- For network with integral edge capacity, there exists integral maximal flow
	  collapsed:: true
		- Use BFS to search augmenting path
	-
- Theorems
	-
	-