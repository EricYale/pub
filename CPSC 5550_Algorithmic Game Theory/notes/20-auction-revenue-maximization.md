# Auction Revenue Maximization

## Constraints
Theoretically, the auctioneer could fix a payment rule such that each bidder must pay infinite money. This is obviously absurd, so we create the following limitation in the context of revenue maximization:

> A mechanism $(a, p)$ is **individually rational** (IR) if for every bidder $i \in [n]$ it holds that $$u_i(v_i, \vec b_{-i}) = v_ia_i(v_i, \vec b_{-i}) - p_i(v_i, \vec b_{-i}) \ge 0 \quad \forall \vec b_{-i} \in \real^{n-1}_{\ge 0}$$

That is, every bidder has nothing to lose by participating in the auction. They always have the option of bidding truthfully and making out with a positive utility when they do.

## Necessity of Aggregate Information

Imagine a **1-bidder** auction where the auctioneer chooses a deterministic allocation rule within an IR mechanism.

There must be a price at which the seller goes from not allocating any winner to giving the (only) bidder the item. Call this $\bar b$.

If $\bar b = 0$, then obviously the bidder gets no revenue since our mechanism is IR.

On the other hand, _without knowing the bidder's private valuation $v$_, we cannot make any determination of where to set $\bar b$; if the bidder bids anything lower than $\bar b$ we still make no revenue due to IR.

This is generalizable to multiple bidders. **It is not possible to design a mechanism that generates good revenue for any private valuation.**

> Put practically: an auctioneer with no knowledge of the true value of an item will not be able to extract maximum revenue. To maximize revenue, we need to use signals about the bidders' valuation of the item.

> Note that Vickrey auctions etc encourage bidders to bid their true valuation, but the mechanism design of *paying the second-highest bid* makes it so that the auctioneer does not collect maximum revenue (they could have collected the highest bid).

## Aggregate Information: Probability Distribution Function

We assume we know a PDF $f$ (and therefore a CDF $F$) such that the valuation of any one bidder is drawn from $f$.

We want to design a mechanism $M = (a, p)$ such that
$$
Rev_F(M) \overset{\Delta}{=} \underset{v \sim F}{\mathbb{E}} [p(v)]
$$

(the argument of $Rev_F$ is the mechanism itself.)

If each bidder has the same valuation PDF (i.e. $F_1 = F_2 = \dots = F_n$) then
$$
Ref_F(M) = \underset{v_i \sim F}{\mathbb{E}} [\sum_{i=1}^n R(\vec v)] = \underset{v_i \sim F}{\mathbb{E}} [\sum_{i=1}^n \Phi(v_i)a_i(\vec v)]
$$

where $\Phi(v)$ is the virtual value
$$
\Phi(v) = v - \frac{1 - F(v)}{f(v)}
$$

> Note: virtual value is essentially the expected value we can extract from one bidder with valuation $v$. Since a bidder won't pay more than their valuation, the chance that they actually want to pay goes down as the price goes up.
>
> Therefore, $Ref_F$ is simply the (expected value of) the sum of virtual values, but select only the ones who win the item and pay.

## Optimal Mechanism
The resulting optimal mechanism is a **reserve price mechanism** with price $p^\star$ such that $\Phi(p^\star) = 0$

> **Reserve price mechanism**: in a single-buyer single-item auction, a reserve price mechanism is simply one where the bidder gets the item if they bid above the reserve price, and they pay the reserve price.