# Online Learning

In online learning, a single agent gets to pick different strategies after playing the same game multiple times, learning in the process to maximize reward given by the scenario.

- A set of actions $S = [m]$
- For multiple "rounds", time $t = 1, 2, \dots, T$:
    1. Agent picks probability distribution $p^t$ over $S$
    2. Adversary picks rewards $r^t(s) \in [0, 1] \quad \forall s \in S$
    3. The agent collects the reward $r^t(p^t) = \underset{x^t \sim p^t}{\mathbb{E}} \left[ r^t(x^t) \right]$
        - $\mathbb{E}$: expected value

## Goal

The agent's goal is to find a sequence $p^1, \dots, p^T$ that maximizes $\overset{T}{\underset{t=1}{\sum}} r^t(p^t)$

Note that this game is totally unfair, since the adversary picks the rewards _after_ seeing the agent's strategy!

Even when playing perfectly, the agent can only get a maximum guaranteed reward of $T/2$ for a smart adversary. We can change this if we use randomness (i.e. a mixed strategy).



## Regret
Regret is similar to loss; it's the difference between the maximum possible reward and the true reward, after all rounds have been played out.

$$
R_p(T) = \underset{a \in S}{\max} \underset{t=1}{\overset{T}{\sum}} r^t(a) - \underset{t=1}{\overset{T}{\sum}} r^t(p^t)
$$

- $a^\star = \underset{a \in S}{\argmax} \underset{t=1}{\overset{T}{\sum}} r^t(a)$ is the best **_single pure strategy_** in hindsight.

## No-Regret Algorithm
An algorithm $A$ is a **no-regret algirithm** if for any $r^1, \dots, r^T$, it achieves
$$
\frac{1}{T} R_A(T) = \underset{a \in S}{\max}\frac{1}{T}\sum{r^t(a)} - \underset{t=1}{\overset{T}{\sum}} r^t(p^t) \underset{\text{as } T \to \infty}{\to} 0
$$

That is, average regret converges to zero as the number of rounds played ($T$) goes to infinity.

> Remember, regret is compared with the best single pure strategy evaluated in hindsight!

### Be The Leader
"Be The Leader" algorithm simply says to do whatever action minimizes total regret.

- Cumulative reward of action $s$: $$u^t(s) = \underset{j=1}{\overset{t}{\sum}} r^j(s)$$
- Action chosen: $\bar x^t=\underset{a \in S}{\argmax}\ u^t(a)$

This algorithm is sort of nonsense, because it uses knowledge of $r^t$ to pick $\bar x^t$ (but we cannot know the rewards of the $t$'th round before we pick the actions for the $t$'th round). We only define it as an intermediate step.

### Randomness
Any no-regret algorithm has to use randomness, since a deterministic algorithm can be exploited by an adversary.

This poses a problem; classic operators like $\max$ lead to deterministic choices of actions. We need to use a smooth/soft version of $\max$. Recall: softmax!

## Softmax
This is the same softmax as in machine learning; it outputs a vector of numbers, where the $i$'th entry is of greater magnitude if the $i$'th input is larger.

Any softmax-capable function needs to (1) approximate $\max$ and (2) be smooth.

![Softmax function](./resources/softmax.png)

## Be The Regularized Leader
> For round $t$, take the cumulative reward of each strategy from rounds $1, \dots, t$, and apply softmax. Your probability distribution for round $t$ is the output of softmax.

Note that this algorithm is only hypothetical because, again, it uses information of the rewards in round $t$ to pick the action for round $t$. But we define as a benchmark.

## Follow The Regularized Leader (FTRL)
> For round $t$, take the cumulative rewards of each strategy from rounds $1, \dots, t-1$, and apply softmax. Your probability distribution for round $t$ is the output of softmax.

This algorithm's regret will be at most $u \cdot T$ larger than the regret of "Be The Regularized Leader".
- $u$ is a parameter of the softmax function

If we choose the exponential mechanism as the softmax function with parameter $\epsilon = \sqrt{\frac{\log m}{T}}$, we have regret at most $O( \sqrt{\frac{\log m}{T}})$.

$O( \sqrt{\frac{\log m}{T}})$ approaches 0 as $T \to \infty$, so FTRL is a no-regret algorithm.

## Usage and Relevance

You can use online learning to find coarse-correlated equilibria, which will be described in [the next section](./13-correlated-equilibria.md).