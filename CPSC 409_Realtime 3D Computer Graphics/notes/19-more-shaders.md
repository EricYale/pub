# Other Shaders in the Pipeline

## Tessellation
- A tessellation shader eases the load on the Vertex Puller by reducing the number of vertices to pull from the CPU
- Happens before the vertex shader
- It transforms a lower-poly model into a higher-poly model
- The tessellation shader can be used to render different Levels Of Detail for different distances from the camerea

### Tessellation Control Shader
- Figures out how much tessellation to apply

### Tessellator
- Actually generates the new vertices (can be triangles, quads, or isolines)

### Tessellation Evaluation Shader
- Sets the positions of the new vertices
- You are able to access the positions of all vertices in the patch around the vertex being processed

## Geometry Shader
- A geometry shader adds new geometry (i.e. triangles) from a set of vertices
- Happens after the vertex shader
- Geometry shader can pass data back to the CPU via the Transform Feedback 
- You can choose how many times to invoke the geometry shader!
- Geometry shader can be used to duplicate meshes (like for particle systems)

## GPU Memory
- We can use textures to store data on the GPU
- We can also use another type, Image, which is simpler than a texture (no filtering, etc)
- We can use Shader Storage Buffer Objects (SSBO) to store arbitrary structured data that isn't well suited for an image or texture

## Compute Shader
- The compute shader allows you to do general-purpose computation, separate from the pipeline

## Mesh Shader
- Mesh shader combines vertex, geometry, and tessellation shaders into a single programmable stage
