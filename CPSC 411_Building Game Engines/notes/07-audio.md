# Audio

## SDL Audio System
- `SDL_Init(SDL_AUDIO)`: Initializes the SDL audio system
- `SDL_LoadWAV(file, &wave, &date, &dlen)`: Loads an audio file into memory
- `PlaySound(filename)`: Plays a file in memory
- `SDL_FreeWav(wav_buf)`: Frees an audio file from memory

### `SDL_Mixer`
- `SDL_Mixer` is an extension library that makes sounds easier to work with
- Adds the ability to play to a specific channel

## Sound Manager
- You can have a queue of events (ring buffer) for storing audio calls
- In the update function, the audio manager goes through the queue and plays the sounds

### Priority and Expiry
- Louder sounds can be prioritized, so that softer sounds are not played at the same time
- Sounds can be expired after a certain time
- If two identical sounds are played at the same time, you can cancel duplicated IDs within a certain duration
