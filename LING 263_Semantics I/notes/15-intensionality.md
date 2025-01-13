# Intensionality

## Synonymy
- Two sentences are synonymous if their interpretations are the same for _any_ model.
- This is stronger than saying two sentences have the same truth value in one possible world.

## Intensionality
- **Modals** like `might`, `should`, `can` do not tell us about any possible world; only about _modal circumstances_.
- **Intensional** language talks about not-necessarily-actual possibilities
    - **Attitude verbs**: "thinks", "believes"
    - **Intensional verbs**: "John is looking for a competent plumber"
    - **Conditionals**: "If...then"

## Compositionality
- A problem arises when we try to apply compositionality to intensional language.
- People don't believe _truth values_; for example, `Jennifer believes that it is cold` does not entail `Jennifer believes that 2+2=4` even though both `it is cold` and `2+2=4` are true.

## Intensional Models
- We can make every predicate take an extra parameter, a _possible world_.
    - These possible worlds have type `s`, _state_.

> - `cat(w)`: type `st`
> - `meowed(w, x)`
> - `saw(w, x, y)`

- These are often expressed with subscripts as syntactic sugar

> - cat<sub>w</sub>
> - meowed<sub>w</sub>(x)
> - saw<sub>w</sub>(x, y)

### Intensional Operators
- Modals, attitude verbs, and intensional transitives say things about the existence of possible worlds

> **Some common intensional operators**
> - might: `𝜆p.∃w'.p(w')`: type `<st, t>`
>   - might takes in a predicate (type st), and returns if it is true in some possible world
> - thinks: $\lambda p.\lambda x.\forall w'.dox_w(x, w') \rightarrow p(w')$
>   - `dox` refers to a doxastic state, i.e. $dox_w(x, w')$ means that the world $w'$ is compatible with $x$'s beliefs

