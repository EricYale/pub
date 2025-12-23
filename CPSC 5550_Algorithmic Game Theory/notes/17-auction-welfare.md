# Social Welfare in Auctions

## Definition
Given that the bidders make utility $$u_i(\vec b) = a_i(\vec b) \cdot v_i - p_i(\vec b)$$
and the seller collects revenue $$\sum_{i=1}^n p_i(\vec b)$$

> There is no notion of the seller's valuation of the item, since the seller _must_ sell the item; ther is no world in which they keep it.

We can compute the sum of the utilities of all agents involved (seller, all bidders):
$$
sw(a, p, \vec v, \vec b) = \sum_{i=1}^n u_i(\vec b) + \sum_{i=1}^n p_i(\vec b) = \sum_{i=1}^n a_i(\vec b) \cdot v_i
$$

> Note that the summation of the prices cancel out since the auctioneer makes the money, while the bidders pay it.

This is called the **social welfare**.

## Maximizing Social Welfare
To design an auction that maximizes social welfare, we can solve the optimization problem
$$
\max_{a} \sum_{i=1}^n a_i(\vec b) \cdot v_i
$$

> That is, the social welfare is the sum of the private valuations of the bidder(s) who win the auction.

Assuming that values $v_i$ are different, we can see that $a^\star$ has to satisfy
$$
a^\star_i = \mathbb{1}\{ v_i = \max_j v_j \}
$$

> In other words, $a^\star$ should allocate the item to the bidder with the highest valuation.

However, we run into a problem: the valuations $\vec v$ are private information, and are not known to the auctioneer.

Thus, the DSIC property becomes important, since at equilibrium $\vec b = \vec v$, we can solve this optimization problem by subbing in $\vec b$ instead of $\vec v$.

## Second-Price Auction and Social Welfare
The second-price auction is DSIC, and also maximizes social welfare at its truthful equilibrium.

We will prove this using the following lemma.

## Vickey-Clarke-Groves (VCG) Payment Rule

> Each bidder $i$ pays the difference between the optimal welfare of the rest of the bidders if $i$ was not participating and the welfare of the rest of the bidders when $i$ participates.

Mathematically,
$$
p_i(\vec b) = \max_y \sum_{j \neq i} y_jb_i - \sum_{j \neq i} a^\star_j(\vec b) \cdot b_j
$$

> Under second-price auction, the first term reduces to the second-highest bid, and the second term is 0 since no one else gets the item.
>
> Thus, the first bidder has to pay the second highest bid accorrding to this rule. The rest of the bidders will pay $\underset{i}{\max}\ b_i - \underset{i}{\max}\ b_i = 0$.

We proved that the second-price auction comes out as maximizing social welfare from the first principle of VCG payment rule. However, VCG applies to other auctions, including multi-item auctions.

## VCG Auctions: Multiple Items
For multiple items, we can follow the following auction design.

First, allocate items as usual, giving items to the bidders who bid the highest.

Second, for each bidder $i$ who wins an item, charge them the difference between (the total welfare that would have been achieved if $i$ did not participate at all) - (the total welfare of the current (best) allocation, less the welfare of $i$).

> ### Example from [Wikipedia](https://en.wikipedia.org/wiki/Vickrey%E2%80%93Clarke%E2%80%93Groves_auction)
>
> Suppose two apples are being auctioned among three bidders.
> - Bidder A wants one apple and is willing to pay $5 for that apple.
> - Bidder B wants one apple and is willing to pay $2 for it.
> - Bidder C wants two apples and is willing to pay $6 to have both of them but is uninterested in buying only one without the other.
> 
> First, the outcome of the auction is determined by maximizing bids: the apples go to bidder A and bidder B, since their combined bid of $5 + $2 = $7 is greater than the bid for two apples by bidder C who is willing to pay only $6. Thus, after the auction, the value achieved by bidder A is $5, by bidder B is $2, and by bidder C is $0 (since bidder C gets nothing). Note that the determination of winners is essentially a knapsack problem.
> 
> Next, the formula for deciding payments gives:
> 
> - For bidder A: The payment for winning required of A is determined as follows: First, in an auction that excludes bidder A, the social-welfare maximizing outcome would assign both apples to bidder C for a total social value of $6. Next, the total social value of the original auction excluding A's value is computed as $7 − $5 = $2. Finally, subtract the second value from the first value. Thus, the payment required of A is $6 − $2 = $4.
> - For bidder B: Similar to the above, the best outcome for an auction that excludes bidder B assigns both apples to bidder C for $6. The total social value of the original auction minus B's portion is $5. Thus, the payment required of B is $6 − $5 = $1.
> - Finally, the payment for bidder C is (($5 + $2) − ($5 + $2)) = $0.
> 
> After the auction, A is $1 better off than before (paying $4 to gain $5 of utility), B is $1 better off than before (paying $1 to gain $2 of utility), and C is neutral (having not won anything).
