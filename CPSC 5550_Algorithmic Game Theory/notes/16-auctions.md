# Auctions

## Definitions
- Each bidder $i$ has a **private valuation** $v_i$, which they are willing to pay
- The auctioneer does not know the private valuations, but wants to decide:
    1. Allocation: which bidder gets the item
    2. Payment: how much each bidder should pay
- A bidder's **utility** from the auction if they pay $p_i$ is $u_i = v_i - p_i$ (see: consumer surplus)

## Ascending Price Auctions: Mechanics

An auction starts with a price $b = 0$, and all bidders raise their hands.

We continuously increase the price $b$.

At every instance of the price $b$, only the bidders that are interested in paying the price keep their hand raised.

The instance $b$ that only one hand is raised is the winning price, and that bidder wins.

## Descending Price Auctions: Mechanics

We start with a price $b = MAX$ and no bidders raise their hands.

We continously decrease the price $b$.

The instance that a bidder raises their hand is the winning price, and that bidder wins.

> See: Dutch auctions (like flower auctions in the Netherlands with the big clock)

## Sealed Bid Auctions
- All bidders simultaneously write down a bid. Bidder $i$ writes down $b_i$
- The auctioneer collects all bids and opens them. They decide an **allocation rule** that maps $\vec b = (b_1, \dots, b_n)$ to a probability distribution
    - $a_i(\vec b)$ is the probability that bidder $i$ will get the item, given a bid profile $\vec b$
    - If $a_i$ only has values in $\{0,1\}$, then the allocation is deterministic; otherwise it is randomized
- Each bidder pays a price according to the payment rule $p_i(\vec b)$, which is the amount bidder $i$ has to pay given the bid profile $\vec b$
- Bidder $i$'s expected utility (quasi-linear) is $$u_i(\vec b) = a_i(\vec b) \cdot v_i - p_i$$

### Examples of Sealed Bid Auctions
- First-price auctions: the highest bidder wins and pays their bid
    - Allocation rule: $a_i(\vec b) = \mathbb{1} \{ b_i = \underset{j \in [n]}{\max} \ b_j \}$
    - Payment rule: $p_i(\vec b) = a_i(\vec b) \cdot b_i$
- Second-price auctions (Vickrey auctions, Google Ads): the highest bidder wins and pays the second-highest bid
    - Allocation rule: $a_i(\vec b) = \mathbb{1} \{ b_i = \underset{j \in [n]}{\max} \ b_j \}$
    - Payment rule: $p_i(\vec b) = a_i(\vec b) \cdot (\underset{j \neq i}{\max} \ b_j)$
- Random lottery:
    - Allocation rule: $a_i(\vec b) = \frac{1}{n}$
    - Payment rule: $p_i(\vec b) = b$
- All-pay auction: highest bidder wins, but all bidders pay their bid no matter if they win or not
    - Allocation rule: $a_i(\vec b) = \mathbb{1} \{ b_i = \underset{j \in [n]}{\max} \ b_j \}$
    - Payment rule: $p_i(\vec b) = b_i$

## Equivalence
- First-price auction is equivalent to the descending price auction.
- Second-price auction is equivalent to the ascending price auction.

## Dominant Strateegy Incentive Compatibility (DSIC)
- A sealed-bid auction $(a, p)$ (allocation rule $a$ and payment rule $p$) is **dominant strategy incentive compatible** (DSIC) if it holds that $$u_i(v_i, \vec b_{-i}) \ge u_i(b_i, \vec b_{-i})$$ for all bidders $i \in [n]$, $v_i \in R_{\ge 0}, b_i \in R{\ge 0}$ and $\vec b_{-i} \in R_{\ge 0}^{n-1}$
- That is, a mechanism is DSIC if bidding/reporting truthfully (i.e. $b_i = v_i$) is a weak dominant strategy equilibrum

### Examples
- First-price auction is _not_ DSIC. In fact, if all bids are different then truthful bidding is _dominated_
- Second-price auction is DSIC
