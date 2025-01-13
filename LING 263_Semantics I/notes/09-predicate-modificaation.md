# Predicate Modification
- If we want to say something like "the red ball," we need to express `red(x) ∧ ball(x)`.
- We can introduce a new rule, predicate modification, to our syntax tree interpretation ruleset.

> ### Predicate Modification
> If $\gamma$ has children $\alpha \rightsquigarrow \alpha': \langle e, t \rangle$ and $\beta \rightsquigarrow \beta': \langle e, t \rangle$, then
> - $\gamma \rightsquigarrow \lambda x.\alpha'(x) \land \beta'(x) : \langle e, t \rangle$
> 
> i.e. do predicate conjunction when a binary-branching node dominates two predicates
