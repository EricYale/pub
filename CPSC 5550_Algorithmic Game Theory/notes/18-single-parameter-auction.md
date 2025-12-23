# Single Parameter Auctions

Maximizing revenue from an auction is much more difficult than maximizing social welfare. We have to define a slight generalization of the single-item auction called a _single-parameter setting_.

## Single-Parameter Setting
- $n$ agents
- Each ag ent $i \in [n]$ has a private valuation $v_i \in R_{\ge 0}$
- The auctioneer announces an allocation rule $a: \real_{\ge 0}^n \to \real_{\ge 0}^n$ and a payment rule $p: \real_{\ge 0}^n \to \real$
    - In a single-item auction, the output of $a$ is a probability distribution over who gets the item, while in a single-parameter setting, the output of $a$ is a vector of "amounts" that each agent gets
- The agents (publicly) choose a bid $b_i \in \real_{\ge 0}$
- Agent $i$ receives utility $$u_i(b_i, b_{-i}) = v_i \cdot a_i(b_i, b_{-i}) - p_i(b_i, b_{-i})$$
- The pair of allocation rule and payment rule $(a, p)$ is called a mechanism

## DSIC for Single-Parameter Settings
An allocation rule $a$ is **implementable** if there exists a payment rule $P$ such that $(a, p)$ is DSIC.

Myerson's Lemma shows that a mechanism $(a, p)$ is DSIC iff
1. $a_i(b_i, \dots, b_n)$ is a monotone non-decreasing function of $b_i$ for all $\vec b_{-i}$
2. The payment rule has the following form: $$p_i(b_i, \vec b_{-i}) = b_i a_i(b_i, \vec b_{-i}) - \int_0^{b_i} a_i(z, \vec b_{-i}) dz + c_i(\vec b_{-i})$$
    - where $c_i$ is a constant that does not depend on $b_i$

## Example: Sponsored Search Auctions
Take a search engine that wants to sell the first $k$ ad slots on a search results page. Each position has a different click-through rate $r_j$ for position $j \in [k]$.

Each ag ent has a private valuation $v_i$ per click. That is, if an agent $i$ gets position $j$, their utility is $u_i = r_j v_i - p_i$.

The auctioneer decides $a_i(\vec b)$, which is the click-through rate that every bidder gets, along with their price to pay.

The welfare-maximizing allocation rule is to assign slot $j$ to the $j$'th highest bidder. (Note that this allocation rule is monotone since higher bids result in higher CTRs.) Thus, this allocation rule is implementable.
