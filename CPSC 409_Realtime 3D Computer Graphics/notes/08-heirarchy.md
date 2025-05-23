# Heirarchy
- Having a scene Tree will allow us to progressively apply transformations
- For example, in a humanoid robot, rotating the arm will transform the hand

## Z-Buffer
- To solve the problem of overlapping objects, we can use a Z-buffer
- Just like it stores a color, each pixel stores a Z-depth
- Each time we draw, the Z-buffer does a test to determine which pixel to render
- This can be enabled with `glEnable(GL_DEPTH_TEST)`
