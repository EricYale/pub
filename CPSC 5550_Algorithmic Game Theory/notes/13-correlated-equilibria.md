# Correlated Equilibria

## Illustration by Example
**Chicken**
- Imagine the game of chicken, where two cars are approaching each other at a corner.
- Both want to be the one that goes first, but neither wants to crash.

P1/P2 | Go | Wait
--|--|--
Go | -100, -100 | 1, -1
Wait | -1, 1 | 0, 0

**Correlated Equilibria**
- The introduction of a **traffic light** creates a an agreement between both players that is mutually beneficial.
- This is called a **correlated equilibrium**.

## Correlated Equilibria
- A **correlated equilibrium** is a probability distribution over the set of all possible strategy profiles.
    - For "chicken", it would be a four-element vector with (Go, Wait), (Wait, Go), (Go, Go), and (Wait, Wait). Our traffic light would assign 50% probability to both (Go, Wait) and (Wait, Go).
- A **correlated equilibrium** means: $$\underset{\vec x \sim\ \sigma^\star}{\mathbb{E}}\left[r_i\left(\vec x\right)\right] \ge \underset{\vec x \sim\ \sigma^\star}{\mathbb{E}}\left[r_i\left(\delta(\vec x), \vec{x_{-i}}\right)\right]$$ where $\delta$ is a function mapping the mediator's proscribed pure strategy to the pure strategy the player will defect to.

- That is, no player should be able to increase their reward by not cooperating with the agreement, _after_ they have received their assignment from the mediator (traffic light), _assuming_ all other players follow orders.

## Coarse Correlated Equilibria
- We can relax this definition and introduce the notion of a **coarse correlated equilibrium**.
- $\sigma$ is a coarse-correlated equilibrium if all players are better off agreeing to the mediator rather than following a pure strategy. It assumes that players are committed to the mediator's CCE, and **they are not allowed to renege**. $$\underset{\vec x \sim\ \sigma^\star}{\mathbb{E}}\left[r_i\left(\vec x\right)\right] \ge
\underset{\vec x \sim\ \sigma^\star}{\mathbb{E}}\left[r_i\left(s_i, \vec{x_{-i}}\right)\right] - \epsilon \quad \forall s_i \in S_i, i \in [n]$$
    - $s_i$ is the pure strategy that player $i$ would be better off playing rather than agreeing to the mediator. (that is, if $\sigma$ were not a CCE)

### $\epsilon$-CCE
- We can introduce a fudge factor $\epsilon$ that allows for some wiggle room.
- If a probability distribution $\sigma$ is an $\epsilon$-coarse-correlated equilibrium, the following must hold:
$$
\underset{\vec x \sim\ \sigma^\star}{\mathbb{E}}\left[r_i\left(\vec x\right)\right] \ge
\underset{\vec x \sim\ \sigma^\star}{\mathbb{E}}\left[r_i\left(s_i, \vec{x_{-i}}\right)\right] - \epsilon \quad \forall s_i \in S_i, i \in [n]
$$
- In other words, $\sigma^\star$ is an $\epsilon$-coarse-correlated equilibrium if there is no player $i$ that gains more than $\epsilon$ by dropping out of the agreement and following a pure strategy $s_i$.

## Finding a Coarse-Correlated Equilibrium
**Algorithm to find an $\epsilon$-CCE**:

- for t = 1..T:
    1. Player $i$ runs a FTRL algorithm $$r_i^t(\cdot) = \mathbb{E}[r_i^t(\cdot, \vec{x_{-i}})], P_i^t$$
    2. Player $i$ realizes a reward $$r_i^t(P^t) = \underset{\vec x \sim\ P^t}{\mathbb{E}}[r_i^t(\vec x)]$$

**Value of epsilon**:
- This algorithm will find an $\epsilon$-CCE for $$\epsilon \le O \left( \sqrt{\frac{\log m}{T}} \right)$$
