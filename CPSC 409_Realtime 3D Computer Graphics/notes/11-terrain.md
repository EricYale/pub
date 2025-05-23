# Terrain
- A terrain is made up of a grid of vertices, each with a specified height

## Triangle Strips
- If we rendered the texture using IBOs, each vertex would be referenced many times
- However, since we are using a grid, we can instead make use of **triangle strips**

<img src="./resources/triangle-strip-1.png" alt="Triangle strip" height="100px">
<img src="./resources/triangle-strip-2.png" alt="Triangle strip" height="100px">

## Loading Heights
- Height data can be loaded from a height map (a greyscale image)
<img src="./resources/heightmap.png" alt="Heightmap" height="100px">

## Coloring Terrains
- Textures can be loaded from a color map
- The color map is simply projected onto the terrain

### Multi-Texture Sampling
- You can select from multiple textures based on the height of the vertex
- Or, you can read another map that has different colors to specify which texture to read
