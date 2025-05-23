# Skybox
- A skybox surrounds the world, creating the illusion of a distant background.

## Cubemaps
- Skyboxes are often specified using cubemap texture (6 squares, forming the net of a cube)

## OpenGL
- Use texture type `GP_TEXTURE_CUBE_MAP` when you call `glBindTexture`
- The cubemap skybox is drawn _first_, so it clears the scene, and it is in the background

## Reflection Mapping
- Reflection mapping is a way to "fake" reflective surfaces, without having to compute ray tracing.
- Shiny objects reflect the skybox texture (and ignore scene objects in between); the normal dictates the direction of the reflection

### Dynamic Reflection Mapping
- You can make other scene objects show up in the reflection using dynamic reflection mapping
- You can use an intermediate framebuffer to compute a cubemap that _contains_ the pixels of the scene objects
- Then, the reflection mapping will use the framebuffer cubemap instead of just the skybox
