# OpenGL Basics

## Contexts
- OpenGL is a state machine
- A context stores the state of OpenGL
- You can have multiple contexts, e.g. for multiple games

## Shapes
- **Vertex**: a point in space, defined by X, Y, and Z floating point coordinates
- **Line segment**/**edge**: connects two vertices
= **Triangle**: the basic building block of all models in real-time graphics

## The Pipeline
1. Application stage
    - All geometry and pixel data lives on the CPU
2. Geometry stage
    - Geometry is sent to the GPU
    - Vertices are assembled into primitives (i.e. triangles)
    - Transformations are applied to vertices
3. Rasterization stage
    - Geometry is converted to pixels
4. Display stage
    - Pixels are sent to the display

## Shaders
- Shaders are small programs that run on the GPU
- Each step in the OpenGL pipeline can take a shader that transforms data
