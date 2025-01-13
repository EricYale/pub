# Relative Clauses
- In syntax trees, you can use numbers to represent relative clauses' referents.
- When you reach the relative clause, mark it with a subscript.
- We need a new rule to interpret our syntax trees:

> ### Abstraction
> If $\gamma$ is a tree with children $\alpha$ and $\beta$, and $\alpha$ is the index $i$, and $\beta \rightsquigarrow \beta' : \tau$, then
> - $\gamma \rightsquigarrow \lambda x_i.\beta' : \langle e, \tau \rangle$

- See example below (branch with CP); $x_1$ i treated like an entity, until it meets the number $1$, at which point it is bound to a lambda argument.

![Tree with movement](./resources/movement-tree.png)
