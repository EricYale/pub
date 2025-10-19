# Linear Programming

## Example
In a factory, Widget A requires 2 blue inputs and 1 red input. Widget B requires 1 blue input and 4 red inputs.

Widget A produces $5 of profit per unit, and widget B produces $6 of profit per unit.

We can use up to 3 blue inputs per minute, and we can use up to 5 red inputs per minute.

We can optimize how many Widget A and how many Widget B to make per minute by setting up the reward function to maximize, and the constraint functions.

$$
\begin{align}
\text{maximize:} \quad & 5x_1 + 6x_2 \\
\text{constraints:} \quad & 2x_1 + x_2 \le 3 \\
                        & x_1 + 4x_2 \le 5 \\
                        & x_1 \ge 0 \\
                        & x_2 \ge 0
\end{align}
$$

In this example, the optimal solution happens to be $(1, 1)$. But how can we prove that this is true, i.e. _given an optimal solution, how to prove that it's optimal_?

### Proving Optimality

We know that the optimal solution has to satisfy
$$
2x_1 + x_2 \le 3\\
x_1 + 4x_2 \le 5
$$

We can multiply the first inequality by 2 on both sides:
$$
4x_1 + 2x_2 \le 6\\
x_1 + 4x_2 \le 5
$$

Adding these inequalities, we get
$$
5x_1 + 6x_2 \le 11
$$

By doing this, we arrived at the expression we need to maximize: $5x_1 + 6x_2$! So we know that our reward can never be greater than 11.

If we plug in our postulated solution of $(1, 1)$, we get 11, and we just proved it can never be larger than 11, so we have proven we found an optimal solution.

But this seemed very ad-hoc; how can we generalize?

### Generalizing
We'll multiply equation 1 by $y_1$ on both sides, and equation 2 by $y_2$ on both sides.


$$
2y_1x_1 + y_1x_2 \le 3y_1\\
y_2x_1 + 4y_2x_2 \le 5y_2
$$

Adding them together;
$$
(2y_1 + y_2)x_1 + (y_1 + 4y_2)x_2 \le 3y_1 + 5y_2
$$

We can set the coefficients on $x_1$ and $x_2$ to be greater than those in our maximized expression. So

$$
(5x_1 + 6x_2) \le (2y_1 + y_2)x_1 + (y_1 + 4y_2)x_2 \le 3y_1 + 5y_2
$$

Thus, $3y_1 + 5y_2$ is an upper bound on $5x_1 + 6x_2$. Equating coefficients, we can then write the inequalities

$$
2y_1 + y_2 \ge 5\\
y_1 + 4y_2 \ge 6
$$

We want to find the $(y_1, y_2)$ that provides the best upper bound, i.e. achieve the minimum value of $3y_1 + 5y_2$.

$$
\begin{align}
\text{minimize:} \quad & 3y_1 + 5y_2 \\
\text{constraints:} \quad & 2y_1 + y_2 \ge 5 \\
                        & y_1 + 4y_2 \ge 6 \\
                        & y_1 \ge 0 \\
                        & y_2 \ge 0
\end{align}
$$

This optimization is problem is called the **dual** of our original linear programming problem.

Importantly, we know that if we are given (1) a solution $(x_1, x_2)$, and (2) a solution $(y_1, y_2)$, we _know_ that $(x_1, x_2)$ and $(y_1, y_2)$ are both optimal.

## Definitions
- **Linear program**: an optimization program with variables $x \in \real^n$, with an objective function $c^Tx$ where $c \in \real^n$, and constraints $Ax \le b$ where $A \in R^{n \times m}, b \in R^m$.
- **Feasible solution**: a vector $x$ that satisfies $Ax \le b, x \ge 0$
- **Optimal solution**: a feasible solution that maximizes $c^Tx$.
- **Dual linear program**: the problem derived from the **primal** program, as described above. An optimization program with variables $y \in R^m$ (one for every one of the constants $Ax \le b$), objective function $-b^Ty$, and constraints $A^Ty \ge c$.
- **Infeasible**: a linear program is infeasible if there is no $x \in R^n$ such that $x$ is feasible.
- **Unbounded**: a linear program is unbounded if its value is $+\infty$, i.e. for any $k \ge 0$ there is a feasible $x$ s.t. $c^Tx \gt k$.

## Weak Duality Lemma
> Let $x$ be any feasible solution of the primal program, and $y$ be any feasible solution of the dual program. $c^Tx \le b^Ty$.

## Strong Duality Theorem
> For a primal linear program, and its dual, we always fall into one of these cases:
> 1. Both the primal and dual are infeasible
> 2. Primal is unbounded and dual is infeasible
> 3. Primal is infeasible and dual is unbounded
> 4. Both primal and dual are feasible and bounded, in which case $C^Tx^\ast = b^Ty^\ast$ where $x^\ast$ is an optimal solution of primal, and $y^\ast$ is an optimal solution of dual.

## Supplemental Material
- [Stanford CS261](https://theory.stanford.edu/~trevisan/cs261/lecture06.pdf)