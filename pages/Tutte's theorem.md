public:: true

- The variant of [[Hall's theorem]] on general graph.
- [Theorem](((63de8144-5b67-473b-b5f4-5a8971a4522a)))
	- Denote $q(G)$ by the number of odd components in $G$.
		- "Odd component" is a component of odd order.
	- Then $G$ has a $1$-factor iff for every $S\subseteq V(G)$
	  collapsed:: true
	  $$q(G-S)\leq |S|$$
		- c.f. ((63de02cd-f2a1-431a-a98d-fd2ebb25ea2e))
- Proof
	- Necessity is trivial, since each odd component must get aid from $S$ for at least one edge.
	- Play induction on $|G|$. If $|G|=0$, it holds.
	- Consider a $G$ with even order.
	- Consider a maximal $S$ s.t. $q(G-S)\leq |S|$.
	  collapsed:: true
		- Since any $S$ of size $1$ would satisfy, such a $S$ exists.
	- Prove that each even component satisfies the condition.
	- Prove that each odd component, if with any vertex removed, satisfies the condition.
	  collapsed:: true
		- Use the fact that $S$ is maximal.
	- Prove that $S$ can be perfectly matched to the odd components.
	  collapsed:: true
		- Use [[Hall's theorem]].
	- Thus, we constructed a $1$-factor of $G$.
- Collary
	- ((63de8450-e468-42ab-911d-8cfcc5b57b33))
	  collapsed:: true
		- Proved by adding a $K_d$ with every of its vertices connected to every vertices of $G$.
		-