# Lighting Maps
- We can use various texture maps to make different parts of a texture behave differently with regards to light.

## Specular Maps
- A specular map specifies how shiny a texture will be at a certain point.

## Bump Map
- A map that tells you how much to extrude each pixel on a texture
- Can be used for per-pixel normals, which can be used to calculate lighting at each pixel
    - You can calculate the normals based on the derivative/slope of the bump map

## Normal Map
- An RGB texture that represents the X, Y, and Z of normal vectors
- Often, high-poly models are decimated into low-poly models, and a normal map is generated from the high-poly model
- When we apply transformations to a mesh, we need to also transform the normal vectors
    - This is done by transforming to texture/tangent space
    - We can do this with a TBN matrix

## Displacement Map
- Displacement maps actually generate new geometry
