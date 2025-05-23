# State Machines
- State machines can control flow between states of a game or a GameObject

## Design Patterns
- Interface for a state, e.g. `IHeroState`
- States override callbacks that are called when the state is entered/exited, and when a game loop is called
- `IsLegal` function to poll whether it's possible to enter a state from a previous state
