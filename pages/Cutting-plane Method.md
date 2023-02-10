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
		- Assume that $A$ is full-rank, and is $n\times n$. (if not, the problem can be down with smaller dimension)
		- Add a relaxation variable for each line $i$:
		  $$s_i + \sum_{j}A_{i,j}x_j = b_i$$
		- File optimal $\vec{x}^*$ under linear relaxation.
		- Express $x_i$ in terms of $s_j$
		  $$x_i^* + \sum_{j=1}^n c_j s_j = k_i$$
		  , where $c_j$ and $k_i$ are constants. This holds for all feasible point (in the new problem with variable $s_j$)
		- There must be some $i$ such that $k_i$ is fraction. Let's pick out any.
		- Split above equation into integer and non-negative part, for example
		  $$I = x_i^* - \sum_j \lceil |c_j|\rceil s_j$$
		  $$N = \sum_j (\lceil|c_j|\rceil + c_j) s_j$$
		- We can throw the non-negative part away, so
		  $$x_i^* - \sum_j \lceil |c_j|\rceil s_j \leq \lfloor k_i \rfloor$$
		  , which holds for every feasible integer point. We can again replace $s_j$ with linear combination of all $x_i$, so we are back to original problem.
		- This gives a Gomory cut, which cuts exactly the $\vec{x}^*$ out, while all feasible integer points are reserved.
		-
- Reference
	- https://faculty.math.illinois.edu/~mlavrov/docs/482-fall-2019/lecture35.pdf
	- https://en.wikipedia.org/wiki/Cutting-plane_method