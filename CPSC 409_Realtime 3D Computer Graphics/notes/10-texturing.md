# Texturing
- Triangles can be textured with image files
- GPU VRAM holds texture data, and they can be re-used across multiple triangles

## UV Mapping
- To convert a 2D image file to a texture applied to a 3D mesh, we need to unwrap it using a projection
- Key problems in projections
    - Bijectivity: each point on the surface should map to a point on the texture
    - Size distortion: scale should be constant across surface
    - Shape distortion: a circle should be a circle on the projection
    - Continuity: no visible seams

## Texture Sampling
- Texels (pixels on the GPU) are sampled to determine the color of a pixel on the screen
- The nearest texel may be sampled, which may lead to aliasing
- Other sampling methods like bilinear take an average of nearest pixels

### Mipmapping
- Smaller-sized textures can be used for further objects, so there are less pixels to sample, reducing aliasing

## Texturing in OpenGL
- A Texture Buffer Object (TBO) is used to upload a texture to the GPU
- We need to define a uniform to pass the reference to the texture
- Textures are used by being binded to, and the shader can then access it
    - `texture()` function in GLSL
