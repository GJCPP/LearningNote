- A method for solving linear integer programming.
- Basic idea
	- Consider now we are given
	  \begin{aligned}
	  \max_{\vec{x}\in \mathbb{Z}^n}\ &\vec{c}^T\vec{x}\\
	  \text{subject to}\ &A\vec{x}\leq \vec{b}\\
	  &\vec{x}\geq 0
	  \end{aligned}
	- Solve this problem under linear relaxation, and get an optimal $\vec{x}^*$
	- Find a plane $\vec{\alpha}^T\vec{x}\leq \beta$ such that
		- 1. It's valid for **integer programming**. That is, for any $\vec{x}\in \mathbb{Z}^n$ satisfying $A\vec{x}\leq \vec{b}$ and $\vec{x} \geq 0$, $\vec{\alpha}^T\vec{x}\leq \beta$ holds.
		- 2. It cuts off $\vec{x}^*$, i.e. $\vec{\alpha}^T\vec{x}^*>\beta$
		- Note that if these two conditions can not both hold, either we can round $\vec{x}^*$ by rounding each of its entry to get an optimal solution, or there is no solution at all.
	- Add this cutting plane to the constraint, and do it again till you find a solution.
- How to find that plane?
	- Gomory cuts
		- One would probably find the [concrete example here](https://faculty.math.illinois.edu/~mlavrov/docs/482-fall-2019/lecture35.pdf) more understandable... Since below is simply an express of that example in general notations.
		- Assume that $A$ is full-rank, and is $n\times n$. (if not, the problem can be solved in smaller dimension)
		- Add a relaxation variable for each line $i$:
		  $$s_i + \sum_{j}A_{i,j}x_j = b_i$$
		- Express $x_i$ in terms of $s_j$
		  $$x_i + \sum_{j=1}^n c_{i,j} s_j = k_i$$
		  , where $c_{i,j}$ and $k_i$ are constants. This holds for all feasible point (in the new problem with variable $s_j$)
		- There must be some $i$ such that $k_i$ is fraction. Let's pick out any.
		- Lift the integer to one side, for example
		  $$I = x_i + \sum_j \lfloor c_{i,j}\rfloor s_j - \lfloor k_i\rfloor$$
		  $$R = k_i-\lfloor k_i\rfloor - \sum_j (c_{i,j}-\lfloor c_{i,j}\rfloor)s_j$$
		  $$I=R$$
		-
		- For any feasible integer point, the right side is less than $1$, so
		  $$R = k_i-\lfloor k_i\rfloor - \sum_j (c_{i,j}-\lfloor c_{i,j}\rfloor)s_j\leq 0$$
		  for all feasible integer point.
		- This is Gomory cut we seeks, with variables being $s_j$.
		- We can again replace $s_j$ with linear combination of all $x_i$, so we are back to original problem.
		- It's easy to see that all feasible integer point satisfies this inequality.
		- **Why can this thing cut off the feasible solution?**
			- Fundamental theorem of LP: for standard form LP, there exists basic solution.
				- Basic solution for LP: where all inequalities that constrain the polytope are active.
			- That is, there exists a solution $\vec{x}^*$ such that $s_j=0$ for all $j$.
			- Then for this solution $\vec{x}^*$, $R=k_i-\lfloor k_i\rfloor>0$, if it is not an integer one.
			- So this plane actually cuts off some feasible solutions for the original problem.
		-
- Reference
	- https://faculty.math.illinois.edu/~mlavrov/docs/482-fall-2019/lecture35.pdf
	- https://en.wikipedia.org/wiki/Cutting-plane_method
	- https://www.ou.edu/class/che-design/che5480-11/Gomory%20Cuts-The%20How%20and%20the%20Why.pdf