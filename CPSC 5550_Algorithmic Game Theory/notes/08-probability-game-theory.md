# Probability-Based Game Theory

## Mixed Strategies
- For some games, it is advantageous for a player to use a random mix of strategies. (Example: Rock Paper Scissors)
- A **mixed strategy** is a probability distribution over a set of strategies. For example, for Rock Paper Scissors, player 1's ideal distribution is $$p_1 = (\frac{1}{2}, \frac{1}{2}, \frac{1}{2})$$

## Expected Value
- The reward for player $i$ for a mixed strategy profile $\vec{p}$ is simply the expected value for the player: $$r_i(\vec p) = \sum_{\vec{s}} r_{i}(\vec{s})\prod_{j=1}^{n}p_{j}(s_{j})$$
    - $\vec{p}$ describes the mixed strategy profile of the game, i.e. the mixed stratgies every player chooses
    - $r_i$ describes the reward for player $i$
    - Sum over all possible pure strategy profiles $\vec s$
    - The product term represents the chance that $\vec s$ is the pure strategy profile that all players end up choosing. i.e. we multiply player A's chance of picking $\vec s$ with player B's chance ... etc.

### Zero-Sum Games
- For every 2-player szero-sum game, and every mixed strategy profile $\vec p$, it holds that $$r_1(\vec p) + r_2(\vec p) = 0$$
    - This is easy to prove given the definition of a zero-sum game for pure strategies: $$r_1(\vec s) + r_2(\vec s) = \sum_{\vec s} r_i(\vec s) = 0$$
        - The summation term is a product term of the EV equation for mixed strategies, and it equals zero

