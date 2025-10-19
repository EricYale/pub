# Mixed Nash Equilibrium

## Definition
- Mixed strategy profile $\vec p$ is a mixed Nash equilibrium if $$r_i(p_i, \vec p_{-i}) \ge r_i(p'_i, \vec p_{-i})$$ for all players $i$ and for all mixed strategies $p'_i$.
- That is, any player $i$ should not be able to improve their reward by changing their own mixed strategy probability distribution.
- If player A's strategy is a mixed Nash equilibrium, player B will be **indifferent** between each of their pure strategies.
    - Indifference means that each pure strategy will have the same expected value.
    - If a player is indifferent between pure strategies, that means all mixed strategies that they play will also have the same expected value.
- At equilibrium, the pure strategies that a player mixes into his mixed strategy all have the same expected value.

## Finding Nash Equilibria for Two-Player Games

Say we have the game "Matching Pennies."

P1 ⬇︎ / P2 ➡︎ | H | T
--|--|--
H | +1 / -1 | -1 / +1
T | -1 / +1 | +1 / -1

Let's try to find a mixed Nash equilibrium.

Let $p$ and $q$ be mixed strategies for players 1 and 2 respectively. That is, player 1 will play H $p\%$ of the time, and play T $(1-p)\%$ of the time.

$$
\begin{align*}
r_1(p, q) & = (1)(p)(q) + (-1)(1-p)(q) + (-1)(p)(1-q) + (1)(1-p)(1-q) \\
& = p(4q-2) - 2q + 1
\end{align*}
$$

We can ignore the $-2q+1$ term because it is independent of the strategy $p$ of player 1, and therefore does not factor into player 1's mixed strategy.

Thus, we get $r_1(p,q)$ as a linear function of $p$. Thus, let's maximize $r_1(p,q)$ by adjusting $p$, for each possible $q$ value.

$$
p_{\text{best}} = \begin{cases} 0 & \text{if } q < 1/2 \\ 1 & \text{if } q > 1/2 \\ \text{anything} & \text{if } q = 1/2 \end{cases}
$$

We can do the same calculation for player 2, and get 

$$
q_{\text{best}} = \begin{cases} 0 & \text{if } p > 1/2 \\ 1 & \text{if } p < 1/2 \\ \text{anything} & \text{if } p = 1/2 \end{cases}
$$

If player 1 chooses $p^\star > \frac{1}{2}$, then $q^\star = 0$ according to the best response of player 2. But, if $q^\star = $ then $p^\star = 0$ according to the best response of player 1. This creates a contradiction.

On the other hand, if $p^\star \lt \frac{1}{2}$ then $q^\star = 1$ which should then imply $p^\star = 0$, another contradiction.

We can similarly rule out $q^\star \lt \frac{1}{2}$ and $q^\star \gt \frac{1}{2}$.

Thus, the only mixed Nash equilibrium is $(p^\star, q^\star)$ where $p^\star = \frac{1}{2}$ and $q^\star = \frac{1}{2}$.


## Von Neumann's Min-Max Theorem
"Every zero-sum two-player game (with any number of strategies per player) has at least one mixed Nash equilibrium. Furthermore, there exists an efficient algorithm that computes this equilibrium."
