# OpenGL API

## Types
- `GLContext`: stores the state of OpenGL
- Vertex Buffer Object (VBO): stores large amounts of data to be sent to the GPU
- Vertex Array Object (VAO): a thin wrapper around a vertex buffer that stores additional information, like its format
- Pointers: an "iterator" that lives on the GPU
    - Takes parameters like the length, data type, stride, and offset

## Handles
- OpenGL uses integer "handles" to refer to objects

## Function Calls
- OpenGL uses many "out"-style parameters, where an address is passed in, and the data is changed by the function

## Binding
- To indicate you want to start working with a particular object, you "bind" it
- For example, `glBindVertexArray(vao)`
- To stop working with an object, you "unbind" it: `glBindVertexArray(0)`

## Shaders
- Written in GLSL
- `in` and `out` variables are used to pass data between shaders
- `uniform` variables are constants to GLSL code, but can be changed by the CPU program
    - These stay constant throughout every stage of the shader pipeline
    - Used to pass data to shaders

### Compilation
- Shaders are compiled and sent to the GPU at runtime

### Types of Shaders
- Vertex shader
    - Runs once for every vertex on the GPU
    - Transforms the vertex's position
- Fragment shader
    - Computes the color of each pixel that's drawn
    - Runs once for every fragment on the screen
