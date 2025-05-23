# SDL

## SDL Features
- `SDL`: basic library
- `SDL_Input`: Handles input, like keypresses, mouse presses, gamepads
- `SDL_Image`: utility for loading .jpg, .png, etc

## Compilation
- SDL library must be linked with your own compiled code

## The SDL API
- `SDL_Init`: initializes SDL
    - Flags for enabling video, audio, etc

## Handling Input
- Events are encoded as an `SDL_Event` object
- Events are stored in a FIFO queue
- `SDL_PollEvent(SDL_Event* event)`: checks for events

### `SDL_Event`
- Every event has a type
- The rest of the event is a **union**: depending on the type, the fields vary
