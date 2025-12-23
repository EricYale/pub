# Nash's Theorem
Nash's Theorem states that every finite game has a Nash Equilibrium.

## Proof
Take a function $F(\vec p)$ which outputs $\vec p'$, the best response to $\vec p$.

Let's define an intermediate function $$f_i(\vec p) = \underset{p \in \Delta m_i}{\argmax}\ \vec{r}(p, \vec p_{-i})$$

And then define
$$
F(\vec p) =
\begin{bmatrix}
f_1(p) \\
\vdots \\
f_n(p)
\end{bmatrix}
$$

If we were naïve, we would make the following incorrect assertion:

> !! By Brower's fixed point theorem, there exists $p^\star$ such that $F(\^\star) = p^\star$
> 
> !! Therefore $p^\star_i$ is a best response to $p^\star_{-i}, \quad \forall i \in [n]$
>
> !! Therefore $\vec p^\star$ is a Nash Equilibrium

However, $\argmax$ is not continuous so therefore $F$ is not continuous, so we cannot use the fixed point theorem.

Like we did in [Online Learning](./12-online-learning.md), we can apply Softmax instead of $\argmax$ to get this continuity property we need.

We don't care how large $\mu$ is in our softmax function, we can use the properties of the exponential mechanism to conclude that for all $\delta \gt 0$ there exists a continuous function $g: \Delta_m \to \Delta_m$ such that $$u(p) \ge \max_{s \in S} u(s) - \delta$$ where $p = g(u)$ for some continuous function $g$.

Thus we bypass the error with our naïve proof, and we prove Nash's theorem.

## Computational Complexity

Although we previously showed that [computing NE in two-player zero-sum games is efficient](./11-two-player-zero-sum.md), and that [computing coarse-correlated equilibria is efficient](./13-correlated-equilibria.md), we know that **finding Nash equilibria for general games is hard**.

Reason: _finding Nash equilibria is as difficult as finding the fixed point in **any** continuous function_. (Papadimitriou '06).
