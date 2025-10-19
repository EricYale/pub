# Two-Player Zero-Sum Games

## Definitions
- Player 1 has strategies $\{1, 2, \dots, n\}$
- Player 2 has strategies $\{1, 2, \dots, n\}$
- Since this is a zero-sum game, the reward of player 1 is the negative of reward of player 2: $$r_1(i, j) = a_{ij} = -r_2(i, j)$$
- The set of all rewards is $A = [a_{ij}]$ $$r_1(i, j)=e_i^TAe_j=a_{ij}$$
    - $e_i = \begin{bmatrix} 0 \\ 0 \\ 1 \\ 0 \end{bmatrix} \subset \real^n$
- n-dimensional simplex $\Delta_n \subseteq \real^n$: $$\Delta_n = \{x \in \real^n, x_i \ge 0 \space\forall i \in [n], \space \sum_{i=1}^n x_i=1\}$$
    - In other words, $\Delta_n$ is the space of all unit vectors of dimension $n$ with non-negative entries
- $\vec x \in \Delta_n$ is a mixed strategy of player 1
- $\vec y \in \Delta_n$ is a mixed strategy of player 2

> Example: Rock Paper Scissors
> $$
> A = \begin{bmatrix}
>   0& -1& 1\\
>   1& 0& -1\\
>   -1& 1& 0
> \end{bmatrix}
> $$

## Min-Max

Imagine a turn-based game where each player goes once.

A strategy $\bar{\vec{x}}$ is a **max-min equilibrium** (Stackelberg equilibrium) if the following holds:

$$
\bar{\vec{x}} \in \underset{\vec{x} \in \Delta_{n}}\argmax \ u_{1}(\vec{x}) = \underset{\vec{x} \in \Delta_{n}}\argmax\  \min_{j} \{ \vec{x}^{T} A e_{j} \}
$$

> #### Explanation of equations
> 
> - $e_j$ is a standard basis vector, i.e. all elements 0 except one, which is 1
> - $\min_{j} \{ \vec{x}^{T} A e_{j}\}$: player 1's minimum guaranteed payoff if he plays strategy $\vec x$
> - $\bar x$: the mixed strategy of Player 1 that _maximizes_ his _minimum payoff_
> - (since we assume Player 2 will force Player 1 into his minimum payoff scenario; similar to minimax trees)

...and $\bar{\vec{y}}$ a **min-max equilibrium** if the following holds:

$$
\bar{\vec{y}} \in \underset{\vec{y} \in \Delta_{m}} \argmin \ U_{2}(\vec{x}) = \underset{\vec{y} \in \Delta_{m}}\argmin\  \max_{i} \{ e_{i}^{T} A \vec{y} \}
$$


### Perfect Min-Max Play

- If player 1 plays first:
    1. Player 1 picks $\vec{x} = \underset{\vec{x} \in \Delta_n}{\argmax} \{ \underset{\vec{y}}{\min} \space \vec{x}^TA\vec{y} \}$
    2. Player 2 picks $\vec{y} = \underset{\vec{y} \in \Delta_n}{\argmin}\{\vec{x}^TA\vec{y}\}$
- If player 2 plays first
    1. Player 2 picks $\vec{y} = \underset{\vec{y} \in \Delta_n}{\argmin} \{ \underset{\vec{x}}{\max} \space \vec{x}^TA\vec{y} \}$
    2. Player 1 picks $\vec{x} = \underset{\vec{x} \in \Delta_n}{\argmax}\{\vec{x}^TA\vec{y}\}$

Player 1 chooses a mixed strategy; player 2 chooses the best strategy in response.

**There's no reason for player 2 to choose a mixed strategy** since they know what player 1 chooses, and they are the last to act.

## Linear Programming
We can find an optimal strategy using a linear program.

$$\max \min \{ \vec{x}^TAe_j\}$$

can be written as

$$
\begin{align*}
\text{maximize:} \quad & z \\
\text{constraints:} \quad & z = \min\{\vec{x}^TAe_j\} \\
& \sum x_i = 1 \\
& \vec{x} \ge 0
\end{align*}
$$

which is equivalent to

$$
\begin{align*}
\text{maximize:} \quad & z \\
\text{constraints:} \quad & z = \min\{\vec{x}^TAe_j\} \\
& (\vec{x}^T)(\vec{1}) = 1 \\
& \vec{x} \ge 0
\end{align*}
$$

which can be written as

$$
\begin{align*}
\text{maximize:} \quad & z \\
\text{constraints:} \quad & z \lt \vec{x}^TAe_j \quad \forall_j \in [m] \\
& (\vec{x}^T)(\vec{1}) = 1 \\
& \vec{x} \ge 0
\end{align*}
$$

...

$$
\begin{align*}
\text{maximize:} \quad & z \\
\text{constraints:} \quad & -A^T\vec{x} + \vec{1}z \le 0\\
& \vec{1}^T\vec{x} = 1 \\
& \vec{x} \ge 0
\end{align*}
$$

This is now a linear program; this linear program efficiently computes the **max-min** equilibrium.

Similarly, we can construct a linear program that computes the **min-max** equilibrium:

$$
\begin{align*}
\text{maximize:} \quad & w \\
\text{constraints:} \quad & -A\vec{y} + \vec{1}w \le 0\\
& \vec{1}^T\vec{y} = 1 \\
& \vec{y} \ge 0
\end{align*}
$$

Now, observe that the linear program for the max-min equilibrium is the dual of the linear program for the min-max equilibrium!

## Nash Equilibrium
Using this observation, we can say that the strategy profile $(\bar{\vec{x}}, \bar{\vec{y}})$ is a Nash equilibrium, where $\bar{\vec{x}}$ is a max-min equilibrium and $\bar{\vec{y}}$ is a min-max equilbrium.

$(\bar{\vec{x}}, \bar{z})$ is an optimal solution of the primal program, and $(\bar{\vec{y}}, \bar{w})$ is an optimal solution of the dual program.

From strong duality, we know that $\bar{z} = \bar{w}$. Thus, we know that

$$
\underset{j}{\min} \{\bar{\vec{x}}^TAe_j\} = \underset{i}{\max} \{e_i^TA\bar{\vec{y}}\}
$$

We can reduce this to
$$
\bar{\vec{x}}^TA\bar{\vec{y}} \ge \vec{x}^T A\bar{\vec{y}} \quad \forall \vec{x} \in \Delta n \\
\bar{\vec{x}}^TA\bar{\vec{y}} \ge \bar{\vec{x}}^T A\vec{y} \quad \forall \vec{y} \in \Delta n
$$

which means that this is a Nash equilibrium, because neither player 1 or player 2 can change their strategy to a different one to gain an advantage.

## Von Neumann's Min-Max Theorem

Based on the equality from the dual programs, we also know that

$$
\underset{y \in \Delta m}{\min} \ \underset{x \in \Delta n}{\max} \ x^TAy = \underset{x \in \Delta n}{\max} \ \underset{y \in \Delta m}{\min} \ x^TAy
$$

This means that no matter who plays first, the reward of both players is the same at any sequential equilibria whether it is a min-max or max-min equilibrium.

This equilibrium value is called the **value** of the game.
