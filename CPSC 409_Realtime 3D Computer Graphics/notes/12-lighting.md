# Lighting

## Basics of Lighting
- **Local illumination**: lighting based solely on light sources, materials, and positions
- **Indirect illumination**: includes calculations based on bounce lighting
- **Baked lighting**: with static light sources, light info can be pre-calculated and baked into textures

## Representing Light in OpenGL
- Lights can be represented as uniforms, passed to our vertex shaders

## Shading Models
- Lambert shading: only diffuse lighting
- Phong shading: adds a specular component (highlight)

### Lambertian Shading
- The intensity of diffused light is proportional to dot of the light source and the surface normal

### Phong Shading
Three features of the lighting model
- Ambient: the default light applied to a scene
- Diffuse: lambertian shading
- Specular: highlights on a glossy surface surface
    - Proportional to the dot of the reflection vector and the view vector, raised to an exponent
- There are various techniques to calculate the reflection vector
    - The normal vector of each triangle can be used in calculation
    - The normal vector of each vertex can be used
    - Normal vectors can be interpolated between vertices to get smoother lighting (per-pixel)

## Types of Lights
- Ambient: a uniform brightness across the scene
- Directional: like "the sun", assumes all light particles come from the same direction
- Point lights: light emitted from a point; light attenuates over distance
- Spot lights: light eminates from a conec  
= Hemisphere lighting: one color of light comes from above, another color from below
- Image-based lighting: use a texture (captured using a "light probe"—shiny sphere); render the lighting to simulate the real-world texture
