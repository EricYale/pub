# The Game Loop
The game loop handles three main functions:
- Input
- Update (game state)
- Render

## Implementation
- We may want to use function pointers to make our input/update/render functions hot-swappable
- We can store these function pointers in a struct that houses Application state